<script lang="ts">
	export let code: string;
</script>

<iframe
	src={`https://www.youtube.com/embed/${code}`}
	title="YouTube video player"
	frameborder="0"
	allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
	allowfullscreen
/>

<style>
	iframe {
		width: 100%;
		aspect-ratio: 16/9;
	}
</style>
