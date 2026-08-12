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

	let isHidden = $state(true);

	function OnClick()
	{
		isHidden = !isHidden
	}

	const maxWidthQuery = window.matchMedia("(max-width: 915px)");

	let iconColor = getComputedStyle(document.documentElement).getPropertyValue("--icon-color");
	let lightMode = window.matchMedia("(prefers-color-scheme: light)").matches;
	let linkIconSize = $state(maxWidthQuery.matches ? 24 : 32);

	maxWidthQuery.addEventListener('change', () => linkIconSize = maxWidthQuery.matches ? 24 : 32);
</script>

<div class="footer">
	<button onclick={OnClick}>
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
				<Column padding="20px" gap="15px">
					<div class="lucide">
						<img style="height: 100%; margin: 0;" src={lightMode ? LucideLogoLight : LucideLogoDark} alt="Logotipo de Lucide">
						<p>Lucide</p>
					</div>
					<a href="https://lucide.dev/license" target="_blank" rel="noopener noreferrer">
						Ver licencia
						<Link size={linkIconSize}/>
					</a>
				</Column>
			</Card>
			<Card>
				<Column padding="20px" gap="15px">
					<div class="svelte-logo">
						<SvelteLogo/>
					</div>
					<a href="https://github.com/sveltejs/svelte/blob/main/LICENSE.md" target="_blank" rel="noopener noreferrer">
						Ver licencia
						<Link size={linkIconSize}/>
					</a>
				</Column>
			</Card>
			<Card>
				<Column padding="20px" gap="15px">
					<div class="simple-icons">
						<SimpleIconsLogo/>
						<p>Simple Icons</p>
					</div>
					<a href="https://github.com/simple-icons/simple-icons/blob/develop/LICENSE.md" target="_blank" rel="noopener noreferrer">
						Ver licencia
						<Link size={linkIconSize}/>
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
		padding: clamp(16px, 3vw, 24px);
		color: var(--text-color);
		background:
			linear-gradient(90deg, transparent, rgb(122 163 41 / 0.12), transparent),
			var(--surface);
		border: none;
		border-top: 1px solid var(--card-border);
		border-bottom: 1px solid var(--card-border);
		box-shadow: var(--soft-shadow);
		transition:
			background-color 160ms ease,
			color 160ms ease;
	}

	button h1
	{
		font-size: clamp(1.8rem, 3vw, 3rem);
	}

	button:hover
	{
		cursor: grab;
		color: var(--accent-cyan);
		background-color: var(--card-color-end);
	}

	button:active
	{
		cursor: grabbing;
	}

	button:focus-visible,
	a:focus-visible
	{
		outline: 3px solid var(--accent-cyan);
		outline-offset: 4px;
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
		height: 4.5rem;
		width: 100%;
		color: var(--icon-color);
		font-size: clamp(1.7rem, 3vw, 2.35rem);
		font-weight: 600;
	}

	.lucide p,
	.simple-icons p
	{
		margin: 0;
	}

	.lucide p
	{
		color: var(--text-color);
		font-family: "Inter", ui-sans-serif, system-ui, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
	}

	.simple-icons p
	{
		color: var(--text-color);
		font-family: Roboto Mono,DejaVu Sans Mono,Consolas,monospace,ui-monospace,SFMono-Regular,Menlo,Monaco,Liberation Mono,Courier New !important;
	}

	:global(.simple-icons svg)
	{
		color: var(--accent-violet);
		fill: currentColor;
		height: 100%;
	}

	.svelte-logo
	{
		display: flex;
		width: 100%;
		justify-content: center;
		align-items: center;
		color: var(--muted-text);
	}

	:global(.svelte-logo svg)
	{
		width: min(280px, 100%);
		height: auto;
	}

	a
	{
		display: flex;
		gap: 16px;
		align-items: center;
		justify-content: center;
		text-align: center;
		padding: 6px 8px;
		border: 1px solid var(--card-border);
		border-radius: 10px;
		color: var(--link-color);
		background-color: var(--surface);
		box-shadow: var(--soft-shadow);
		font-size: clamp(1rem, 2vw, 1.45rem);
		font-weight: 700;
		text-decoration: none;
		transition:
			border-color 160ms ease,
			color 160ms ease,
			transform 160ms ease;
	}

	a:hover
	{
		border-color: var(--accent-pink);
		color: var(--link-hover-color);
		transform: translateY(-1px);
	}

	@media (max-width: 915px) 
	{
		a
		{
			gap: 10px;
			padding: 10px 12px;
		}

		.lucide,
		.simple-icons
		{
			font-size: 1.75em;
			height: 3rem;
		}

		:global(.svelte-logo svg)
		{
			width: 220px;
		}
	}
</style>
