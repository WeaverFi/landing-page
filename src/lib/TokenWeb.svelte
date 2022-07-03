<script type="ts">
  import { browser } from "$app/env";
  import { onDestroy, onMount } from "svelte";
  import WeaverFi from "weaverfi";

  // Variables:
  let wrapper: HTMLElement;
  let canvas: HTMLCanvasElement;
  let destroyed = false; // used to stop the render when the component is destroyed
  let angle = 0;
  let viewOffsetMult = 1;
  let width = 0;
  let height = 0;
  $: minRadius = height * viewOffsetMult;
  $: maxRadius = minRadius + Math.sqrt((width * width / 4) + (height * height));
  $: offsetX = width / 2;
  $: offsetY = height + minRadius;

  // Icon list without duplicates:
  let icons = [...new Set(
    Object.values(WeaverFi.getAllTokens())
    .reduce((a,b) => [...a, ...b])
    .map(tokenData => tokenData.logo)
  )];

  // Randomly placed icons:
  let iconPlacements: { angle: number, amplitude: number, iconIndex: number }[] = [];

  // Draw Web Line Function:
  const drawWebLine = (ctx: CanvasRenderingContext2D, x0: number, y0: number, x1: number, y1: number) => {
    
    // Get web angle
    const xD = x1 - x0;
    const yD = y1 - y0;
    const webAngle = Math.atan2(yD, xD);

    // Draw base line:
    ctx.lineWidth = 1;
    ctx.strokeStyle = "#fff3";
    ctx.beginPath();
    ctx.moveTo(offsetX + x0, offsetY + y0);
    ctx.lineTo(offsetX + x1, offsetY + y1);
    ctx.stroke();

    // Draw the line based on the webAngle:
    const mag = Math.sqrt(xD * xD + yD * yD);
    ctx.lineWidth = 1;
    ctx.strokeStyle = "white";
    ctx.beginPath();
    ctx.moveTo(offsetX + x0 + Math.abs(Math.cos(webAngle * 7 + x0 / 100)) * xD, offsetY + y0 + Math.abs(Math.cos(webAngle * 7 + x0 / 100)) * yD);
    ctx.lineTo(offsetX + x0 + Math.abs(Math.sin(webAngle * 8 + y0 / 100)) * xD, offsetY + y0 + Math.abs(Math.sin(webAngle * 8 + y0 / 100)) * yD);
    ctx.stroke();
    
  };

  // Draw Function:
  let lastFrame = 0;
  const draw = (ctx: CanvasRenderingContext2D) => {

    // Check if destroyed:
    if(destroyed) return;

    // Get frame time:
    const now = performance.now();
    const t = (now - lastFrame) / 1000;
    lastFrame = now;

    // Rotate:
    angle += t * 0.05;
    if(angle >= Math.PI * 2) angle = 0;

    // Draw web:
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    const steps = 32;
    for(let i = 0; i < steps; i++) {
      const currentAngle = angle + (i * Math.PI * 2 / steps);
      const cosCurrent = Math.cos(currentAngle);
      const sinCurrent = Math.sin(currentAngle);
      const nextAngle = angle + ((i + 1) * Math.PI * 2 / steps);
      const cosNext = Math.cos(nextAngle);
      const sinNext = Math.sin(nextAngle);
      drawWebLine(ctx, 0, 0, cosCurrent * maxRadius, sinCurrent * maxRadius);
      for(let r = minRadius; r < maxRadius; r += 32) {
        drawWebLine(ctx, 
          cosCurrent * r,
          sinCurrent * r,
          cosNext * r,
          sinNext * r
        );
      }
    }

    // Request next frame:
    requestAnimationFrame(() => draw(ctx));

  };

  // On Mount:
  onMount(() => {

    // Check if SSR:
    if(!browser) return;

    // Calculate resize:
    onResize();

    // Assign first random tokens:
    iconPlacements = [];
    const numIcons = Math.min(300, icons.length);
    const availableIcons = new Set(icons.map((v,i) => i));
    for(let i = 0; i < numIcons; i++) {
      const index = Math.floor(availableIcons.size * Math.random());
      const iconIndex = [...availableIcons][index];
      availableIcons.delete(iconIndex);
      
      iconPlacements.push({
        angle: 2 * Math.PI * i / numIcons,
        amplitude: ((i % 4) / 4) + 0.25 * Math.random(),
        iconIndex: iconIndex
      });
    }

    // Start Drawing:
    const ctx = canvas.getContext('2d');
    if(!ctx) {
      console.error("Could not get 2d rendering context!");
      return;
    }
    lastFrame = performance.now();
    draw(ctx);

  });

  onDestroy(() => {
    destroyed = true;
  });

  function onResize() {
    const bb = wrapper.getBoundingClientRect();
    width = bb.width;
    height = bb.height;
  }

</script>

<!-- #################################################################################################### -->

<svelte:window on:resize={onResize} />

<div id="wrapper" bind:this={wrapper}>
  <canvas {width} {height} bind:this={canvas} />
  
  <!-- Icons -->
  {#each iconPlacements as icon}
    <img class="icon" src="{icons[icon.iconIndex]}" alt="" style="
      transform: translate({offsetX - 16 + ((minRadius + (maxRadius - minRadius) * icon.amplitude) * Math.cos(icon.angle + angle))}px, {offsetY - 16 + ((minRadius + (maxRadius - minRadius) * icon.amplitude) * Math.sin(icon.angle + angle))}px);
    "/>
  {/each}
</div>

<!-- #################################################################################################### -->

<style>
  #wrapper {
    position: absolute;
    overflow: hidden;
    display: block;
    inset: 0;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  #wrapper::after {
    content: "";
    position: absolute;
    inset: 0;
    box-shadow: inset 0 0 40px var(--accent-color);
    /* background: radial-gradient(closest-side, #fff0 80%, var(--accent-color) 100%); */
  }

  img.icon {
    position: absolute;
    width: min(32px, 5vw);
    height: min(32px, 5vw);
    border-radius: 50%;
    top: 0;
    left: 0;
  }
</style>