<script>
	import './styles.css';
</script>

<div class="app">
	<slot />
</div>

<style>
	.app {
		position: relative;
		display: flex;
		flex-direction: column;
		min-height: 100vh;
		width: 100%;
	}
</style>

