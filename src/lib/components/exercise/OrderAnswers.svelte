<script lang="ts">
	export let correctOrder: string[];

	let userOrder = correctOrder
		.map((item) => [item, Math.random()] as const)
		.sort((a, b) => a[1] - b[1])
		.map(([item]) => item);
	let showValidation = false;
	let showSolution = false;
	let dragFromIndex: number | undefined = undefined;

	function move(from: number, to: number) {
		const item = userOrder.splice(from, 1);
		const a = userOrder.slice(0, to);
		const b = userOrder.slice(to, userOrder.length);
		userOrder = [...a, ...item, ...b];
	}

	function onDrag(e: DragEvent, fromIndex: number) {
		e.preventDefault();
		dragFromIndex = fromIndex;
	}

	function onDrop(e: DragEvent, toIndex: number) {
		e.preventDefault();

		console.log(dragFromIndex, toIndex);

		if (dragFromIndex) {
			move(dragFromIndex, toIndex);
		}
	}
</script>

<p>
	<strong> Zet de opties hieronder in de juiste volgorde. </strong><br />
	Je kan de pijltjes achteraan elke optie gebruiken, of je kan de opties verslepen.
</p>

<ol id="items">
	{#each showSolution ? correctOrder : userOrder as item, i}
		<li
			class="message"
			class:is-success={showValidation && item === correctOrder[i]}
			class:is-danger={showValidation && item !== correctOrder[i]}
			data-index={i}
			draggable="true"
			on:dragover={(e) => e.preventDefault()}
			on:drag={(e) => onDrag(e, i)}
			on:drop={(e) => onDrop(e, i)}
		>
			<div class="index">{i + 1}</div>
			<div class="message-body">{item}</div>

			{#if !showValidation}
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
			{/if}
		</li>
	{/each}
</ol>

{#if !showValidation}
	<button
		class="button is-primary"
		on:click={() => {
			showValidation = !showValidation;
			showSolution = false;
		}}
	>
		Controleer volgorde
	</button>
{/if}

{#if showValidation}
	<button class="button is-secondary" on:click={() => (showSolution = !showSolution)}>
		{#if showSolution}
			Verberg juiste volgorde
		{:else}
			Toon juiste volgorde
		{/if}
	</button>
{/if}

<style lang="scss">
	ol {
		list-style: none;
		display: grid;
		gap: 0.2rem;
		margin-left: 0;

		li {
			display: grid;
			grid-template-columns: min-content 1fr min-content;
			margin-bottom: 0;
			cursor: pointer;

			.index {
				width: 2rem;
				height: 100%;
				display: flex;
				align-items: center;
				justify-content: center;
				background-color: #fff;
				font-size: 1.25rem;
			}

			.message-body {
				padding-top: 0.75rem;
				padding-bottom: 0.75rem;
				padding-left: 1rem;
			}

			.buttons {
				display: grid;
				grid-template-columns: 1fr 1fr;
				margin-right: 0.5rem;
			}
		}
	}
</style>
