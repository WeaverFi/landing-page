<script type="ts">

  // Imports:
  import { browser } from "$app/environment";
  import { onDestroy, onMount } from "svelte";
  import weaver from "weaverfi";

  // Type Imports:
  import type { URL } from 'weaverfi';

  // Initializations:
  let wrapper: HTMLElement;
  let canvas: HTMLCanvasElement;
  let destroyed = false;
  let lastFrame = 0;
  let icons: URL[] = [];
  let iconPlacements: { angle: number, amplitude: number, iconIndex: number }[] = [];

  // Dimensions:
  let angle = 0;
  let viewOffsetMult = 1;
  let width = 0;
  let height = 0;

  // Reactive Dimensions:
  $: minRadius = height * viewOffsetMult;
  $: maxRadius = minRadius + Math.sqrt((width * width / 4) + (height * height));
  $: offsetX = width / 2;
  $: offsetY = height + minRadius;

  // Function to draw web lines:
  const drawWebLine = (ctx: CanvasRenderingContext2D, x0: number, y0: number, x1: number, y1: number) => {
    
    // Getting Web Angle:
    const xD = x1 - x0;
    const yD = y1 - y0;
    const webAngle = Math.atan2(yD, xD);

    // Drawing Base Line:
    ctx.lineWidth = 1;
    ctx.strokeStyle = "#fff3";
    ctx.beginPath();
    ctx.moveTo(offsetX + x0, offsetY + y0);
    ctx.lineTo(offsetX + x1, offsetY + y1);
    ctx.stroke();

    // Drawing Line:
    ctx.lineWidth = 1;
    ctx.strokeStyle = "white";
    ctx.beginPath();
    ctx.moveTo(offsetX + x0 + Math.abs(Math.cos(webAngle * 7 + x0 / 100)) * xD, offsetY + y0 + Math.abs(Math.cos(webAngle * 7 + x0 / 100)) * yD);
    ctx.lineTo(offsetX + x0 + Math.abs(Math.sin(webAngle * 8 + y0 / 100)) * xD, offsetY + y0 + Math.abs(Math.sin(webAngle * 8 + y0 / 100)) * yD);
    ctx.stroke();
  };

  // Function to draw web:
  const draw = (ctx: CanvasRenderingContext2D) => {
    if(!destroyed) {

      // Initializations:
      const now = performance.now();
      const steps = 32;

      // Getting Frames:
      const t = (now - lastFrame) / 1000;
      lastFrame = now;

      // Setting Rotation:
      angle += t * 0.05;
      if(angle >= Math.PI * 2) {
        angle = 0;
      }

      // Drawing Web:
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      for(let i = 0; i < steps; i++) {
        const currentAngle = angle + (i * Math.PI * 2 / steps);
        const cosCurrent = Math.cos(currentAngle);
        const sinCurrent = Math.sin(currentAngle);
        const nextAngle = angle + ((i + 1) * Math.PI * 2 / steps);
        const cosNext = Math.cos(nextAngle);
        const sinNext = Math.sin(nextAngle);
        drawWebLine(ctx, 0, 0, cosCurrent * maxRadius, sinCurrent * maxRadius);
        for(let r = minRadius; r < maxRadius; r += 32) {
          drawWebLine(ctx, cosCurrent * r, sinCurrent * r, cosNext * r, sinNext * r);
        }
      }

      // Requesting Next Frame:
      requestAnimationFrame(() => draw(ctx));
    }
  };

  // Function to assign random tokens to web:
  const assignRandomTokens = () => {

    // Initializations:
    const numIcons = Math.min(300, icons.length);
    const availableIcons = new Set(icons.map((v,i) => i));

    // Resetting Placements:
    iconPlacements = [];

    // Placing Tokens:
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
  }

  // Function to resize web canvas:
  const onResize = () => {
    const bb = wrapper.getBoundingClientRect();
    width = bb.width;
    height = bb.height;
  }

  onMount(() => {
    if(browser) {
      icons = [...new Set(Object.values(weaver.getAllTokens()).reduce((a,b) => [...a, ...b]).map(tokenData => tokenData.logo))];
      onResize();
      assignRandomTokens();
  
      // Start Drawing:
      const ctx = canvas.getContext('2d');
      if(ctx) {
        lastFrame = performance.now();
        draw(ctx);
      } else {
        console.error("Could not get 2d rendering context!");
      }
    }
  });

  onDestroy(() => {
    destroyed = true;
  });

</script>

<!-- #################################################################################################### -->

<!-- Window Bindings -->
<svelte:window on:resize={onResize} />

<!-- Token Web Canvas Wrapper -->
<div id="wrapper" bind:this={wrapper}>

  <!-- Canvas -->
  <canvas {width} {height} bind:this={canvas} />
  
  <!-- Icons -->
  {#each iconPlacements as icon}
    <img class="icon" src="{icons[icon.iconIndex]}" alt="" style="transform: translate({offsetX - 16 + ((minRadius + (maxRadius - minRadius) * icon.amplitude) * Math.cos(icon.angle + angle))}px, {offsetY - 16 + ((minRadius + (maxRadius - minRadius) * icon.amplitude) * Math.sin(icon.angle + angle))}px);" />
  {/each}
</div>

<!-- #################################################################################################### -->

<style>

  #wrapper {
    position: absolute;
    inset: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
  }

  #wrapper::after {
    content: '';
    position: absolute;
    inset: 0;
    box-shadow: inset 0 0 40px var(--accentColor);
  }

  img.icon {
    position: absolute;
    top: 0;
    left: 0;
    width: min(32px, 5vw);
    height: min(32px, 5vw);
    border-radius: 50%;
  }

</style>