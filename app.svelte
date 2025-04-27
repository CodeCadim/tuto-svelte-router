<script>
	// Get the pages components
	import Blog from "./pages/blog.svelte";
	import Home from "./pages/home.svelte";
	import About from "./pages/about.svelte";

	// Page is the dynamic component to display
	// See in the html part below : <Page {...params} />
	// Home is set as default page
	let Page = $state(Home);

	// params are dynamic props to pass to the component
	let params = $state();

	// routes defines the route as #tag => component
	const routes = {
		home: Home,
		blog: Blog,
		about: About,
	};

	// router reads the hash part of the URL, constructs the props and defines
	// the component to display
	const router = () => {
		// Get the hash part of the URL and transform it into a search query
		// params after removing the hash character '#'
		const q = new URLSearchParams(window.location.hash.substring(1));

		// Convert the search query into an object
		params = Object.fromEntries(q.entries());

		if (params.page) {
			// Route page to appropriate component using the property 'page'
			Page = routes[params.page];

			// Remove the property 'page' so we get only the parameters
			delete params.page;
		}
	};
	// Route each time the URL change
	window.addEventListener("hashchange", router);

	// initial call
	router();
</script>

<main>
	<nav>
		<a href="#page=home">Home</a>
		<a href="#page=about">About</a>
		<a href="#page=blog&art=1">Art. 1</a>
		<a href="#page=blog&art=2">Art. 2</a>
		<a href="#page=blog&art=3">Art. 3</a>
	</nav>

	<Page {...params} />
</main>

<style>
	main {
		height: 100vh;
		font-family: sans-serif;
		background-color: #fbfbee;
		max-width: 43rem;
		padding: 1rem;
		margin: 0 auto;
	}
	nav {
		display: flex;
		gap: 1rem;
	}
	nav a {
		color: #000;
		text-decoration: none;
		font-weight: bolder;
		padding: 0.25rem 1rem;
		box-shadow: 1px 1px 4px 0px;
	}
	nav a:hover {
		box-shadow: 0px 0px 1px;
	}
</style>
