<script>
	let { art } = $props();
</script>

<h1>
	Article number {art}
</h1>

<img src="https://picsum.photos/id/{23 + art}/300/200" alt="picsum" />
<p>
	Lorem ipsum dolor sit, amet consectetur adipisicing elit. Hic, atque quia
	nostrum voluptates placeat alias expedita voluptatibus, ipsa in, odit
	explicabo dolorem rerum debitis culpa repellendus nihil quaerat cumque iste.
</p>

<style>
	img {
		float: left;
		padding-right: 1rem;
	}
	p {
		max-width: 43rem;
	}
</style>
