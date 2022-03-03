

<script>
    export var ball;
    const black = [15,4,2,17,6,13,11,8,10,24,33,20,31,22,29,28,35,26];
    const red   = [32,19,21,25,34,27,36,30,23,5,16,1,14,9,18,7,12,3];
    const green=[0];
    let lenb=black.length;
    let lenr=red.length;
    let tot_len=lenb+lenr
    
    ball=0;
    
    function handleClickr() {
        let random_black=black[Math.floor(Math.random()*lenb)]
        let random_red=red[Math.floor(Math.random()*lenr)]  
        var thetwos=[random_black,random_red]
        ball=thetwos[Math.floor(Math.random()*thetwos.length)]
        for (let i=0;i< lenr;i++) {
     let d = red [i] 
    if (ball == d){console.log ('red')
    return true;}
}
console.log(ball)
    }
   
    function handleClickb() {
        let random_black=black[Math.floor(Math.random()*lenb)]
        let random_red=red[Math.floor(Math.random()*lenr)]  
        var thetwos=[random_black,random_red]
        ball=thetwos[Math.floor(Math.random()*thetwos.length)]
        for (let i=0;i< lenr;i++) {
     let d = red [i] 
    if (ball == d){console.log ('black')
    return true;}
}
console.log(ball)

    }




    export let grid = [4, 4];
	
	$: col = `repeat(${grid[1]}, 1fr)`;
	$: row = `repeat(${grid[0]}, 1fr)`;
	$: is_active = Array(grid[0]).fill(0).map(_ => Array(grid[1]).fill(false));
	
	let start = [];
	let end = [];
	let hover_end = []
	let clicked = false;
	
	function select(i, j) {
		if (clicked) {
			end = [i, j];
		} else { 
			start = [i, j];
		}
		
		clicked = !clicked;
		check_active([i, j]);
	}
	
	function hover(i, j) {
		if (!clicked) return;
		hover_end = [i, j];
		check_active(hover_end);
	}
	
	function is_in_range([i, j], [i2, j2]) {
		return ((i - start[0]) * (i - i2) <= 0) && 
			((j - start[1]) * (j - j2)<= 0)
	}
	
	function check_active (end) {
		is_active = is_active.map(
			(a, i) => a.map((_, j) => is_in_range([i, j], end)));
	}
	


    

    
    </script>
   <h2>The ball n is {ball} </h2>

   <div class="container" style="grid-template-rows: {row}; grid-template-columns: {col};">

	{#each {length: grid[0]} as _, i (i)}
	  {#each {length: grid[1]} as _, j (j)}
			<div class:active={is_active[i][j]}
					 on:click={() => select(i, j)}
					 on:mouseover={() => hover(i, j)}
				></div>
		{/each}
	{/each}

</div>
<strong>Current: </strong>{hover_end}<br>
<strong>Coords:</strong> {start} {end[0] ? '-' : ''} {end}
<style>
	.container {
		display: grid;
		border: 1px solid #999;
		border-radius: 2px;
		width: 200px;
		height: 200px;
		grid-gap: 1px;
		background: #999;
	} 
	
	.container div {
		background: #fff;
	}	
	
	div.active {
		background: orange;
	}
</style>


   <button type="button" class="btn btn-outline-warning" on:click={handleClickr}>RED</button>
   
   <button type="button" class="btn btn-outline-warning" on:click={handleClickb}>BLACK</button>