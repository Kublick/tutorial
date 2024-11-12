<script lang="ts">
	import Header from './Header.svelte';
	// let name = $state('Max');

	// let status: 'OPEN' | 'CLOSED' = $state('OPEN');

	// let full_name = $derived(name + '' + ' Lopez');

	// function onclick() {
	// 	status = status === 'OPEN' ? 'CLOSED' : 'OPEN';
	// }
	//
	let formstate = $state({
		name: '',
		birthday: '',
		step: 0,
		error: ''
	});
</script>

<!-- <Header {name} /> -->
<!-- <h2>The full name is {full_name}</h2>

<input type="text" bind:value={name} />

<p>the store is now: {status}</p>

<button {onclick}>Toggle</button> -->

<main>
	<p>Step: {formstate.step + 1}</p>
	{#if formstate.step === 0}
		<p class="error">{formstate.error}</p>
	{/if}
	{#if formstate.step === 0}
		<div>
			<label for="name">Name</label>
			<input type="text" id="name" bind:value={formstate.name} />
		</div>
		<button
			onclick={() => {
				if (formstate.name !== '') {
					formstate.step += 1;
					formstate.error = '';
				} else {
					formstate.error = 'Name is empty';
				}
			}}
		>
			Next
		</button>
	{:else if formstate.step === 1}
		<div>
			<label for="bday">Birthday</label>
			<input type="date" id="bday" bind:value={formstate.birthday} />
		</div>
		<button
			onclick={() => {
				if (formstate.birthday !== '') {
					formstate.step += 1;
					formstate.error = '';
				} else {
					formstate.error = 'birthday is empty';
				}
			}}
		>
			Next
		</button>
	{/if}
</main>

<style>
	.error {
		color: red;
	}
</style>
