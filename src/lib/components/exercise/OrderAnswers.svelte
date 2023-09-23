<script lang="ts">
	export let correctOrder: string[];
	let userOrder = correctOrder
		.map((item) => [item, Math.random()] as const)
		.sort((a, b) => a[1] - b[1])
		.map(([item]) => item);

	function move(from: number, to: number) {
		const item = userOrder.splice(from, 1);
		const a = userOrder.slice(0, to);
		const b = userOrder.slice(to, userOrder.length);
		userOrder = [...a, ...item, ...b];
	}
</script>

<p>
	<strong> Zet de opties hieronder in de juiste volgorde. </strong><br />
	Je kan de pijltjes achteraan elke optie gebruiken, of je kan de opties verslepen.
</p>

<ol>
	{#each userOrder as item, i}
		<li>
			<div class="counter">{i + 1}</div>
			{item}
			<div class="buttons">
				<button class="button is-light is-small" on:click={() => move(i, Math.max(i - 1, 0))}>
					<span class="icon is-small">
						<i class="fas fa-chevron-up" />
					</span>
				</button>
				<button
					class="button is-light is-small"
					on:click={() => move(i, Math.min(i + 1, correctOrder.length - 1))}
				>
					<span class="icon">
						<i class="fas fa-chevron-down" />
					</span>
				</button>
			</div>
		</li>
	{/each}
</ol>

<button class="button is-primary">Controleer volgorde</button>

<style lang="scss">
	ol {
		margin-left: 0;
	}

	li {
		list-style-position: inside;
		background-color: #eee;
		padding: 0rem 0.3rem 0rem 0;
		display: grid;
		grid-template-columns: min-content 1fr min-content;
		align-items: center;
		gap: 0.5rem;

		.counter {
			background-color: #f9f9f9;
			width: 2rem;
			height: 100%;
			display: flex;
			align-items: center;
			justify-content: center;
		}

		.buttons {
			display: grid;
			grid-template-columns: 1fr 1fr;
			margin: 0.3rem 0;

			button {
				margin: 0;
			}
		}
	}
</style>
