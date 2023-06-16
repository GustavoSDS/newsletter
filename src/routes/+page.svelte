<script>
	import Footer from './Footer.svelte';
	import SignUp from './signup/+page.svelte';
	import Message from './message/+page.svelte';
	import { emailStore, buttonClick } from './store/store';
	let validEmail = false;
	let validButton = false;

	emailStore.subscribe((value) => {
		validEmail = value.length > 0;
	});
	buttonClick.subscribe((value) => {
		validButton = value === true;
	});
</script>

<svelte:head>
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
	<title>Newsletter sign-up form with success message</title>
</svelte:head>

<main class={validButton ? 'message' : 'signup'}>
	{#if validEmail && validButton}
		<Message />
	{:else}
		<div class="hero" />
		<SignUp />
	{/if}
</main>

<Footer />

<style>
	main.signup,
	main.message {
		display: flex;
		flex-direction: column;
		background: var(--white);
	}
	div.hero {
		height: 284px;
		background-image: url('../assets/images/illustration-sign-up-mobile.svg');
		background-size: cover;
		background-repeat: no-repeat;
	}
	@media (min-width: 1000px) {
		main {
			margin: auto;
		}
		main.signup {
			flex-direction: row-reverse;
			width: 928px;
			height: 641px;
			padding: 24px 24px 24px 40px;
			column-gap: 64px;
			border-radius: 34px;
		}
		main.message {
			width: 504px;
			height: 520px;
			border-radius: 32px;
		}
		div.hero {
			width: 50%;
			height: 100%;
			background-position: center;
			border-radius: 14px;
		}
	}
	@media (min-width: 1440px) {
		main.signup {
			margin: 219px auto 0;
		}
		main.message {
			margin: 280px auto 0;
		}
	}
</style>
