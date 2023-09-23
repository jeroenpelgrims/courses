<script lang="ts">
	export let doelen: string[];
</script>

<article class="message is-primary">
	<div class="message-body">
		<strong>Wat moet je kennen en kunnen na dit deel?</strong>
		<ul>
			{#each doelen as doel}
				<li>{doel}</li>
			{/each}
		</ul>
	</div>
</article>

<style lang="scss">
</style>
