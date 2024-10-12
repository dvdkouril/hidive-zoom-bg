<script lang="ts">
	import qr from "$lib/qr-invite.png";
	import { onMount } from "svelte";
	import { slide } from "svelte/transition";
	// import { hidiveLogo } from "$lib/logos";

	const hidiveLogo = `
  <defs>
    <style>
      .cls-1 {
        fill: #4f5a63;
      }
    </style>
  </defs>
  <!-- Generator: Adobe Illustrator 28.7.1, SVG Export Plug-In . SVG Version: 1.2.0 Build 142)  -->
  <g>
    <g id="Layer_1">
      <g>
        <path d="M141.4,61.5h10.7v13.8h23.5v-13.8h10.7v36.6h-10.7v-14.9h-23.5v14.9h-10.7v-36.6Z"/>
        <path d="M192.9,61.5h10.7v36.6h-10.7v-36.6Z"/>
        <path d="M210.2,61.5h18.6c17.2,0,23,8,23,18.3s-5.9,18.3-21.4,18.3h-20.3v-36.6h0ZM230.1,90.2c7.9,0,11-3.7,11-10.4s-3.1-10.4-11.8-10.4h-8.5v20.8h9.2Z"/>
        <path d="M257.2,61.5h10.7v36.6h-10.7v-36.6Z"/>
        <path d="M272.5,61.5h12.2l14.5,28.1h0l14.3-28.1h10.9l-19.6,36.6h-12.8l-19.6-36.6h0Z"/>
        <path d="M328.8,61.5h34.6v7.9h-23.9v7.2h18.4v6.2h-18.4v7.4h24.5v7.9h-35.2v-36.6h0Z"/>
      </g>
      <g>
        <path class="cls-1" d="M378,61.4h4.7v32.4h19.3v4.2h-23.9v-36.6h0Z"/>
        <path class="cls-1" d="M432.3,89.2h-19l-3.6,8.9h-4.9l15.5-36.6h5.6l15.5,36.6h-5.5l-3.6-8.9h0ZM430.9,85.7l-8-20h-.1l-8.1,20h16.2,0Z"/>
        <path class="cls-1" d="M447.2,61.4h14.9c8.5,0,12.5,3.7,12.5,9.6s-2.1,7.3-6.5,7.8h0c5.1.5,7.9,3.8,7.9,8.6s-3.6,10.6-12.5,10.6h-16.3v-36.6h0ZM462.7,77.5c5.2,0,7.5-2.3,7.5-5.9s-2.4-6.1-8.2-6.1h-10.2v12h10.9,0ZM463.3,93.9c6.3,0,8.1-2.7,8.1-6.9s-3-6.1-8.4-6.1h-11.2v13h11.4Z"/>
      </g>
      <g>
        <path class="cls-1" d="M83.9,60.4c-10.3,0-18.8,8.4-18.8,18.8s8.4,18.8,18.8,18.8,18.8-8.4,18.8-18.8-8.4-18.8-18.8-18.8ZM87.2,80.8l5.9,6-2,2-5.8-5.9v9.7h-2.8v-9.7l-8.4,8.7-2.1-2,8.5-8.8h-10.3v-2.8h10.3l-4.4-4.5,2-2,4.3,4.4v-12.1h2.8v12.1l6.3-6.5,2.1,2-6.4,6.6h11.6v2.8h-11.6Z"/>
        <path d="M78.4,79.4c0-3,2.4-5.4,5.4-5.4s5.4,2.4,5.4,5.4-2.4,5.4-5.4,5.4-5.4-2.4-5.4-5.4"/>
        <path d="M83.8,105.3c-9.6,0-19.9-4.3-29.6-12.4-7.3-6-11.8-12-11.9-12.3l-1.1-1.5,1.1-1.5c.2-.2,4.7-6.2,12-12.3,9.8-8.1,20.1-12.4,29.8-12.4h0c9.6,0,19.9,4.3,29.6,12.4,7.3,6,11.8,12,11.9,12.3l1.1,1.5-1.1,1.5c-.2.2-4.7,6.2-12,12.3-9.8,8.1-20.1,12.4-29.8,12.4h0ZM47.4,79.2c4.2,5,19,21.2,36.4,21.2h0c17.6,0,32.4-16.1,36.6-21.2-4.2-5-19-21.2-36.4-21.2h0c-17.6,0-32.4,16.1-36.6,21.2Z"/>
      </g>
    </g>
  </g>
	`;

	const hidiveLogoWhite = `
  <defs>
    <style>
      .cls-1 {
        fill: #fff;
      }
    </style>
  </defs>
  <g>
    <g>
      <path class="cls-1" d="M140.56,61.29h10.69v13.81h23.5v-13.81h10.69v36.64h-10.69v-14.92h-23.5v14.92h-10.69v-36.64Z"/>
      <path class="cls-1" d="M192.06,61.29h10.69v36.64h-10.69v-36.64Z"/>
      <path class="cls-1" d="M209.37,61.29h18.65c17.21,0,23,7.96,23,18.32,0,11.75-5.9,18.32-21.38,18.32h-20.27v-36.64ZM229.31,90.02c7.91,0,11.02-3.68,11.02-10.41,0-5.79-3.12-10.41-11.75-10.41h-8.52v20.82h9.24Z"/>
      <path class="cls-1" d="M256.42,61.29h10.69v36.64h-10.69v-36.64Z"/>
      <path class="cls-1" d="M271.68,61.29h12.19l14.53,28.06h.06l14.31-28.06h10.91l-19.6,36.64h-12.81l-19.6-36.64Z"/>
      <path class="cls-1" d="M327.97,61.29h34.63v7.91h-23.94v7.18h18.37v6.24h-18.37v7.41h24.5v7.91h-35.19v-36.64Z"/>
    </g>
    <g>
      <path class="cls-1" d="M377.24,61.21h4.68v32.41h19.27v4.23h-23.94v-36.64Z"/>
      <path class="cls-1" d="M431.53,88.93h-18.99l-3.62,8.91h-4.9l15.48-36.64h5.57l15.48,36.64h-5.46l-3.56-8.91ZM430.14,85.48l-7.96-19.99h-.11l-8.13,19.99h16.2Z"/>
      <path class="cls-1" d="M446.4,61.21h14.92c8.52,0,12.47,3.73,12.47,9.58,0,4.23-2.12,7.29-6.46,7.85v.06c5.07.45,7.85,3.79,7.85,8.57,0,6.46-3.56,10.58-12.53,10.58h-16.26v-36.64ZM461.93,77.3c5.18,0,7.52-2.28,7.52-5.9s-2.39-6.07-8.18-6.07h-10.19v11.97h10.86ZM462.49,93.72c6.29,0,8.13-2.67,8.13-6.9,0-3.67-3.01-6.07-8.35-6.07h-11.19v12.97h11.41Z"/>
    </g>
  </g>
  <g>
    <g>
      <path class="cls-1" d="M83.04,85.37v8.72h3.12v-8.73c-.5.14-1.02.22-1.57.22s-1.06-.08-1.56-.21Z"/>
      <path class="cls-1" d="M79.49,82.65l-7.94,8.18,2.24,2.17,7.93-8.17c-.93-.51-1.7-1.27-2.23-2.18Z"/>
      <path class="cls-1" d="M89.68,76.63l5.63-5.81-2.24-2.17-5.63,5.81c.93.51,1.7,1.26,2.24,2.17Z"/>
      <path class="cls-1" d="M90.31,81.21h10.7v-3.12h-10.7c.14.5.22,1.03.22,1.57s-.08,1.06-.21,1.55Z"/>
      <path class="cls-1" d="M78.89,78.08h-9.25v3.12h9.25c-.13-.5-.21-1.01-.21-1.55s.08-1.07.22-1.57Z"/>
      <path class="cls-1" d="M81.72,74.47l-3.41-3.47-2.23,2.19,3.4,3.47c.54-.91,1.31-1.67,2.23-2.19Z"/>
      <path class="cls-1" d="M87.49,84.82l5.05,5.15,2.23-2.19-5.06-5.16c-.53.91-1.3,1.67-2.22,2.19Z"/>
      <path class="cls-1" d="M86.16,73.94v-11.4h-3.12v11.39c.5-.13,1.02-.21,1.56-.21s1.07.08,1.57.22Z"/>
    </g>
    <path class="cls-1" d="M126.43,77.7c-.19-.25-4.65-6.24-11.94-12.28-9.78-8.1-20.03-12.38-29.64-12.38h-.07c-9.68,0-19.99,4.29-29.82,12.4-7.32,6.04-11.79,12.01-11.97,12.26l-1.1,1.48,1.1,1.49c.19.25,4.65,6.24,11.94,12.28,9.78,8.1,20.03,12.38,29.64,12.38h.07c9.67,0,19.99-4.29,29.82-12.4,7.32-6.04,11.79-12.01,11.97-12.26l1.1-1.48-1.1-1.49ZM84.71,99.69c-11.33,0-20.51-9.18-20.51-20.51s9.18-20.51,20.51-20.51,20.51,9.18,20.51,20.51-9.18,20.51-20.51,20.51Z"/>
  </g>`;

	onMount(() => {
		// console.log("logo:");
		// console.log(logo);
	});

	let useOtherLogo: boolean;
	$: console.log(`useOtherLogo: ${useOtherLogo}`);

	const logoDefaultWidth = 517;
	const logoDefaultHeight = 158;

	let bgColor: string = "#ffffff";
	let logoSize: number = 1.0;

	type Transform = {
		x: number;
		y: number;
		s: number;
	};

	$: transforms = generateTransforms(50, logoSize);

	function generateTransforms(N: number, scaling: number): Transform[] {
		let transforms: Transform[] = [];
		const arrX = Array.from({ length: N }, (_, i) => i);
		for (const x of arrX) {
			const arrY = Array.from({ length: N }, (_, i) => i);
			const scale = Array.from({ length: N }, (_, i) =>
				Math.random(),
			);

			const sineWave = (
				amplitude: number,
				frequency: number,
				length: number,
			) =>
				Array.from(
					{ length },
					(_, i) =>
						amplitude *
						Math.sin(frequency * i),
				);
			const sineValues = sineWave(2, 1, N * N);
			const scaleOffset = 3;
			const spX = logoDefaultWidth;
			const spY = logoDefaultHeight;
			for (const [y, i] of arrY.entries()) {
				// transforms.push({ x: x, y: y, s: scale[i] });
				// transforms.push({ x: x, y: y, s: sineValues[i] + scaleOffset });
				transforms.push({
					x: x * spX * scaling,
					y: y * spY * scaling,
					s: 1 * scaling,
				});
			}
		}
		return transforms;
	}

	let svgCanvas: SVGSVGElement;

	function saveToPNG() {
		//~ thanks chatgpt
		console.log("saving...");
		console.log(svgCanvas);

		const svgData = new XMLSerializer().serializeToString(
			svgCanvas,
		);
		console.log(svgData);
		const svgBlob = new Blob([svgData], {
			type: "image/svg+xml;charset=utf-8",
		});
		const url = URL.createObjectURL(svgBlob);
		console.log(url);
		const img = new Image();
		img.onload = function () {
			// Step 4: Create a Canvas and draw the image
			const canvas = document.createElement("canvas");
			canvas.width = svgCanvas.width.baseVal.value;
			canvas.height = svgCanvas.height.baseVal.value;
			const ctx = canvas.getContext("2d");
			if (!ctx) {
				console.log("failed at getting context");
				return;
			}
			ctx.drawImage(img, 0, 0);

			// Step 5: Convert the canvas to PNG and trigger a download
			const pngData = canvas.toDataURL("image/png");
			const link = document.createElement("a");
			link.href = pngData;
			link.download = "svg_image.png";
			link.click();

			// Clean up
			URL.revokeObjectURL(url);
		};
		img.src = url;
	}

	// const spX = 240;
	// const spY = 50;
</script>

<div id="controls">
	hey.
	<button on:click={() => saveToPNG()}>save</button>
	<input type="checkbox" id="darkOrLight" bind:checked={useOtherLogo} />
	<label>the other logo</label>
	<input type="color" bind:value={bgColor} />
	<label>bg</label>
	<input
		type="range"
		min="0.1"
		max="2"
		step="0.01"
		bind:value={logoSize}
	/>
	<label>size</label>
</div>
<div id="c">
	<svg
		bind:this={svgCanvas}
		viewBox="0 0 1920 1080"
		width="1920"
		height="1080"
		style="background-color: {bgColor || '#e5e5e5'};"
	>
		{#each transforms as t}
			<g
				transform="translate({t.x}, {t.y}) scale({t.s}, {t.s})"
			>
				{#if useOtherLogo}
					{@html hidiveLogoWhite}
				{:else}
					{@html hidiveLogo}
				{/if}
			</g>
		{/each}

		<!-- <rect -->
		<!-- 	width={logoDefaultWidth} -->
		<!-- 	height={logoDefaultHeight} -->
		<!-- 	fill-opacity="0.5" -->
		<!-- /> -->
		<!---->
		<!-- <rect -->
		<!-- 	x={logoDefaultWidth} -->
		<!-- 	y={logoDefaultHeight} -->
		<!-- 	width={logoDefaultWidth} -->
		<!-- 	height={logoDefaultHeight} -->
		<!-- 	fill-opacity="0.5" -->
		<!-- /> -->
		<!---->
		<!-- {@html hidiveLogo} -->
		<!-- <image -->
		<!-- 	id="qr" -->
		<!-- 	transform="translate(10, 10) rotate(-20, 150, 150)" -->
		<!-- 	href={qr} -->
		<!-- 	width="300" -->
		<!-- /> -->
		<!-- <text x="80" y="380" class="invite-text" -->
		<!-- 	>Join for a coffee break!</text -->
		<!-- > -->
	</svg>

	<!-- <img id="qr" src={qr} width="300" /> -->
</div>

<style>
	#c {
		position: relative;
		/* background-color: red; */
		width: 1920px;
		height: 1080px;
	}
	#controls {
		height: 30px;
		background-color: lightgreen;
	}
	#qr {
		border: 10px dashed black;
		position: absolute;
		z-index: 2;
	}
	.invite-text {
		font: bold 30px sans-serif;
		background-color: white;
	}
</style>
