<script>
	import Card from "./lib/Card.svelte";
    import Column from "./layouts/Column.svelte";

	import Fold from "lucide-svelte/icons/fold-vertical";
	import Unfold from "lucide-svelte/icons/unfold-vertical";
	import Link from "lucide-svelte/icons/square-arrow-out-up-right";
	import LucideLogoLight from "/credits/lucide-logo-light.svg";
	import LucideLogoDark from "/credits/lucide-logo-dark.svg";
	import SvelteLogo from "./lib/svelte-horizontal.svelte";
	import SimpleIconsLogo from "./lib/simpleicons.svelte";

	let isHidden = true

	function OnClick()
	{
		isHidden = !isHidden
	}

	let iconColor = getComputedStyle(document.documentElement).getPropertyValue("--icon-color");
	let lightMode = window.matchMedia("(prefers-color-scheme: light)").matches;
</script>

<div class="footer">
	<button on:click={OnClick}>
		<h1>Créditos</h1>
		{#if isHidden}
			<Unfold color={iconColor}/>
		{:else}
			<Fold color={iconColor}/>
		{/if}
	</button>
	<div class="credits" class:hidden={isHidden}>
		<div class="content">
			<Card>
				<Column padding="20px">
					<div class="lucide">
						<img style="height: 100%; margin: 0;" src={lightMode ? LucideLogoLight : LucideLogoDark} alt="Logotipo de Lucide">
						<p>Lucide</p>
					</div>
					<a href="https://lucide.dev/license" target="_blank" rel="noopener noreferrer">
						Ver licencia
						<Link size={50}/>
					</a>
				</Column>
			</Card>
			<Card>
				<Column padding="20px">
					<div class="svelte-logo">
						<SvelteLogo/>
					</div>
					<a href="https://github.com/sveltejs/svelte/blob/main/LICENSE.md" target="_blank" rel="noopener noreferrer">
						Ver licencia
						<Link size={50}/>
					</a>
				</Column>
			</Card>
			<Card>
				<Column padding="20px">
					<div class="simple-icons">
						<SimpleIconsLogo/>
						<p>Simple Icons</p>
					</div>
					<a href="https://github.com/simple-icons/simple-icons/blob/develop/LICENSE.md" target="_blank" rel="noopener noreferrer">
						Ver licencia
						<Link size={50}/>
					</a>
				</Column>
			</Card>
		</div>
	</div>
</div>

<style>
	button
	{
		display: flex;
		width: 100%;
		align-items: center;
		justify-content: center;
		gap: 20px;
		background-color: transparent;
		border: none;
		border-top: 2px solid var(--border-color);
		border-bottom: 2px solid var(--border-color);
	}

	button:hover
	{
		cursor: grab;
	}

	button:active
	{
		cursor: grabbing;
	}

	.hidden
	{
		display: none;
		visibility: hidden;
	}

	.lucide,
	.simple-icons
	{
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 1.25rem;
		height: 6rem;
		width: 100%;
		font-size: 3.5rem;
		font-weight: 600;
	}

	.lucide p,
	.simple-icons p
	{
		margin: 0;
	}

	.lucide p
	{
		color: #3c3c43;
		font-family: "Inter", ui-sans-serif, system-ui, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
	}

	.simple-icons p
	{
		color: var(--icon-color);
		font-family: Roboto Mono,DejaVu Sans Mono,Consolas,monospace,ui-monospace,SFMono-Regular,Menlo,Monaco,Liberation Mono,Courier New !important;
	}

	:global(.simple-icons svg)
	{
		fill: var(--icon-color);
		height: 100%;
	}

	.svelte-logo
	{
		fill: #4a4a55;
	}

	:global(.svelte-logo svg)
	{
		width: 350px;
		height: auto;
	}

	a
	{
		display: flex;
		gap: 16px;
		align-items: center;
		justify-content: center;
		text-align: center;
		font-size: 42px;
		color: blue;
	}

	a:hover
	{
		color: darkblue;
	}

	@media (prefers-color-scheme: dark)
	{
		.lucide p
		{
			color: #dfdfd6;
		}

		.svelte-logo
		{
			color: #b5b5aa;
		}

		a
		{
			color: #00ff00;
		}

		a:hover
		{
			color: #00c900;
		}
	}
</style>