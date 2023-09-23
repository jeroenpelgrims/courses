<svelte:head>
	<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma@0.9.4/css/bulma.min.css" />
	<script src=" https://cdn.jsdelivr.net/npm/@mdi/js@7.2.96/commonjs/mdi.min.js "></script>
	<script defer src="https://use.fontawesome.com/releases/v5.3.1/js/all.js"></script>
</svelte:head>

<main class="container is-max-desktop">
	<slot />
</main>

<style>
	:global(html) {
		font-size: 14px;
	}
</style>
