<script lang="ts">
	export let previousLink: string | undefined = undefined;
	export let nextLink: string | undefined = undefined;
</script>

{#if previousLink || nextLink}
	<div class="footer has-text-centered">
		{#if previousLink}
			<a href={previousLink} class="button is-medium">
				<span class="icon is-small">
					<i class="fas fa-arrow-left" />
				</span>
				<span>Ga terug</span>
			</a>
		{/if}
		{#if nextLink}
			<a href={nextLink} class="button is-medium">
				<span>Ga verder</span>
				<span class="icon is-small">
					<i class="fas fa-arrow-right" />
				</span>
			</a>
		{/if}
	</div>
{/if}
