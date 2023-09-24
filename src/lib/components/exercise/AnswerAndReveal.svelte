<script lang="ts">
	export let multiline: boolean = false;
	let reveal = false;
</script>

<form on:submit|preventDefault={() => (reveal = true)} class:multiline>
	{#if multiline}
		<p class="control">
			<textarea class="textarea" placeholder="Vul je antwoord in" required disabled={reveal} />
		</p>
		<p class="control">
			<button class="button is-primary">Controleer antwoord</button>
		</p>
	{:else}
		<div class="field has-addons">
			<p class="control">
				<input
					class="input"
					type="text"
					placeholder="Vul je antwoord in"
					required
					disabled={reveal}
				/>
			</p>
			<p class="control">
				<button class="button is-primary">Controleer antwoord</button>
			</p>
		</div>
	{/if}
</form>

{#if reveal}
	<article class="message">
		<div class="message-body">
			<slot />
		</div>
	</article>
{/if}

<style lang="scss">
	form.multiline .field {
		display: grid;
	}
</style>
