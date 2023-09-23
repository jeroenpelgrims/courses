<script lang="ts">
	export let answer: string;
	let reveal = false;
</script>

<form on:submit|preventDefault={() => (reveal = true)}>
	<div class="field has-addons">
		<p class="control">
			<input class="input" type="text" placeholder="Vul je antwoord in" required />
		</p>
		<p class="control">
			<button class="button is-primary">Controleer antwoord</button>
		</p>
	</div>
</form>

{#if reveal}
	<article class="message">
		<div class="message-body">
			<slot />
		</div>
	</article>
{/if}
