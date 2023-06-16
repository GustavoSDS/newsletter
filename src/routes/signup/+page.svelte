<script>
	import Form from './Form.svelte';
</script>

<!-- Sign-up form start -->

<section>
	<h1>Stay updated!</h1>
	<p>Join 60,000+ product managers receiving monthly updates on:</p>
	<ul>
		<li>Product discovery and building what matters</li>
		<li>Measuring to ensure updates are a success</li>
		<li>And much more!</li>
	</ul>

	<Form />
</section>

<!-- Sign-up form end -->

<style>
	section {
		height: 558px;
		display: flex;
		flex-direction: column;
		padding: 40px 24px;
	}

	ul {
		margin-top: 10px;
		padding-left: 24px;
		list-style: url('../../assets/images/icon-list.svg') outside;
	}
	ul li {
		margin-top: 8px;
	}

	/* Media quieries for desktop */
	@media (min-width: 1000px) {
		section {
			justify-content: space-around;
		}
	}
</style>
