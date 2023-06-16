<script>
	import { emailStore, buttonClick } from './../store/store.js';

	let isValidEmail = true;
	let email;
	let error;
	const emailRegex = /\b[\w\.-]+@[\w\.-]+\.\w{2,4}\b/;

	function validateEmail() {
		console.log(email);
		isValidEmail = emailRegex.test(email);
		if (isValidEmail) {
			emailStore.set(email);
			error = '';
		} else {
			error = 'error';
		}
	}
	function handleSubmit(e) {
		if (isValidEmail && emailRegex.test(email)) {
			buttonClick.set(isValidEmail);
			console.log('Form submitted successfully');
		} else {
			e.preventDefault();
			error = 'error';
			isValidEmail = false;
		}
	}
</script>

<form>
	<label for="email"
		>Email address
		{#if !isValidEmail}
			<span>Valid email required</span>
		{/if}
	</label>

	<input
		bind:value={email}
		on:input={validateEmail}
		type="email"
		id="email"
		placeholder="email@company.com"
		class={error}
		required
	/>

	<a type="submit" on:click={handleSubmit} href="/"> Subscribe to monthly newsletter </a>
</form>

<style>
	form {
		width: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
	}
	label {
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	label {
		margin: 30px 0 0;
		color: var(--dark-Slate-Grey);
		font-weight: 700;
	}
	label span {
		font-weight: 700;
		color: var(--tomato);
	}

	input {
		height: 56px;
		margin: 10px 0 24px;
		padding-left: 20px;
		color: var(--grey);
		border: 1px solid var(--grey);
		border-radius: 8px;
	}
	input:hover {
		cursor: pointer;
		border: 1px solid var(--dark-Slate-Grey);
	}
	.error {
		color: var(--tomato);
		border: 1px solid red;
		background-color: var(--tomato-opacity);
	}
	.error::placeholder {
		color: var(--tomato);
	}

	a {
		color: var(--white);
		height: 56px;
		border: none;
		border-radius: 8px;
		font-weight: 700;
		background: var(--dark-Slate-Grey);
		text-decoration: none;
		display: grid;
		place-content: center;
	}
	a:hover {
		cursor: pointer;
		box-shadow: 0px 6px 40px -5px var(--tomato);
		background: linear-gradient(to left, var(--orange) 0%, var(--pink) 100%);
	}
</style>
