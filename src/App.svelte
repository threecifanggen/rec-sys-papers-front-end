<script>
	import 'bulma/css/bulma.css';
    import Menu from "./lib/Menu.svelte";
	import { Router, Link, Route } from "svelte-routing";
	
	import CategoryContent from './routes/CategoryContent.svelte';
	import HomePage from './routes/HomePage.svelte';
    import Footer from './lib/Footer.svelte';
    import BreadCrumb from './lib/BreadCrumb.svelte';
</script>


<main>
	<h1>REC-SYS-PAPERS</h1>
	<p style="color:gray">整理「搜广推」领域的相关文献。</p>
	<br>
	<BreadCrumb />
</main>

<Router>
	<Route path="/"><HomePage /></Route>
	<Route path="/category/:cat" let:params>
		<CategoryContent cat="{params.cat}" />
	</Route>
	<Route path="/search/*"></Route>
</Router>
<br><br><br>
<Footer />


<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>