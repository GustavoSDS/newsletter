<script>
	import { buttonClick, emailStore } from './../store/store.js';
	import success from '../../assets/images/icon-success.svg';
	let valueEmail;
	let validEmail = false;
	let validButton = false;

	emailStore.subscribe((value) => {
		valueEmail = value;
		validEmail = value.length > 0;
	});
	buttonClick.subscribe((value) => {
		validButton = value === true;
	});

	function handleClick() {
		buttonClick.set(false);
	}
	console.log(validButton);
	console.log(validEmail);
</script>

<section>
	{#if validButton && validEmail}
		<!-- Success message start -->
		<div>
			<img src={success} alt="icon success" />
			<h1>Thanks for subscribing!</h1>
			<p>
				A confirmation email has been sent to <strong>{valueEmail}</strong>. Please open it and
				click the button inside to confirm your subscription.
			</p>
		</div>

		<!-- Success message end -->
		<a href="/" on:click={handleClick}> Dismiss message </a>
	{:else}
		<p>You are not subscribed, please subscribe on the home page to receive news</p>
	{/if}
</section>

<style>
	section {
		padding: 0 24px;
		display: flex;
		flex-direction: column;
		justify-content: center;
	}

	img {
		margin-top: 35%;
	}

	h1 {
		margin: 24px 0;
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
		margin: 40% 0 40%;
	}
	a:hover {
		cursor: pointer;
		background: linear-gradient(to left, var(--orange) 0%, var(--pink) 100%);
	}
	@media (min-width: 1000px) {
		section {
			height: 100%;
			padding: 64px;
			justify-content: space-between;
		}
		img,
		a {
			margin: 0;
		}
		h1 {
			margin: 14px 0;
		}
	}
</style>
