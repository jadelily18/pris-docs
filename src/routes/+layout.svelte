<script>
	import '@svelteness/kit-docs/client/polyfills/index.js';
	import '@svelteness/kit-docs/client/styles/normalize.css';
	import '@svelteness/kit-docs/client/styles/fonts.css';
	import '@svelteness/kit-docs/client/styles/theme.css';
	import '@svelteness/kit-docs/client/styles/vars.css';

	import { page } from '$app/stores';
	import PrismarineLogo from '$img/prismarine_100px.png';

	import { Button, KitDocs, KitDocsLayout, createSidebarContext } from '@svelteness/kit-docs';

	/** @type {import('./$types').LayoutData} */
	export let data;

	$: ({ meta, sidebar } = data);

	/** @type {import('@svelteness/kit-docs').NavbarConfig} */
	const navbar = {
		links: [{ title: 'Docs', slug: '/docs', match: /\/docs/ }]
	};

	const { activeCategory } = createSidebarContext(sidebar);

	$: category = $activeCategory ? `${$activeCategory}: ` : '';
	$: title = meta ? `${category}${meta.title} | Prismarine` : null;
	$: description = meta?.description;
</script>

<svelte:head>
	{#key $page.url.pathname}
		{#if title}
			<title>{title}</title>
		{/if}
		{#if description}
			<meta name="description" content={description} />
		{/if}
	{/key}
</svelte:head>

<KitDocs {meta}>
	<KitDocsLayout {navbar} {sidebar}>
		<div class="logo" slot="navbar-left">
			<Button href="/">
				<h1 class="logo-text">Prismarine</h1>
			</Button>
		</div>

		<slot />
	</KitDocsLayout>
</KitDocs>

<style>
	:global(:root) {
		--kd-color-brand: 6, 131, 131;
		--kd-code-copied-bg-color: 72, 179, 179 !important;
	}

	:global(:root.dark) {
		--kd-color-brand: 94, 196, 196;
	}

	:global(:root .text-brand) {
		color: rgb(6, 131, 131);
	}

	:global(:root.dark .text-brand) {
		color: rgb(94, 196, 196);
	}

	:global(.kit-docs .code-fence.lang-bash pre .line:not(:empty)::before) {
		color: rgb(72, 179, 179);
	}

	:global(.code-fence-top-bar button div) {
		background-color: rgb(67, 167, 167) !important;
	}

	.logo :global(a) {
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.logo :global(svg) {
		height: 36px;
		overflow: hidden;
	}

	.logo-text {
		font-weight: 600;
		font-size: large;
		padding-left: 1rem;
	}
</style>
