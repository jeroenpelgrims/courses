<script lang="ts">
	export let title: string;
</script>

<article class="message is-info">
	<div class="message-body">
		{#if title}
			<strong>{title}</strong>
		{/if}
		<p><slot /></p>
	</div>
</article>
