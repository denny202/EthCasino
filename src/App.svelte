<script>
	import Bar from "./Bar.svelte"
	import Butt from "./Button.svelte"
	import T from "./Home.svelte"

	
	let grid = [7, 9];

</script>


<style>
	div {
		display: flex;
		width: 100px;
		justify-content: space-between;
	}
	
	div span:first-child {
		margin-right: 20px;
	}
	
	input {
		width: 100%
	}
</style>


<Bar {grid}/>
<Butt/>
<T/>
<main>
	<h2>hey</h2>
	
</main>
