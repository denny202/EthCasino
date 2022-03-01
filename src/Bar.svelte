

<script>
    export var ball;
    const black = [15,4,2,17,6,13,11,8,10,24,33,20,31,22,29,28,35,26];
    const red   = [32,19,21,25,34,27,36,30,23,5,16,1,14,9,18,7,12,3];
    const green=[0];
    let lenb=black.length;
    let lenr=red.length;
    let tot_len=lenb+lenr
    
    ball=0;
    
    function handleClick() {
        let random_black=black[Math.floor(Math.random()*lenb)]
        let random_red=red[Math.floor(Math.random()*lenr)]  
        var thetwos=[random_black,random_red]
        ball=thetwos[Math.floor(Math.random()*thetwos.length)]

    }
    
    var color="red";
    black.forEach(function(item, array) {
       if (item===ball){
           color="black"
       }
})
    console.log(ball)

    
    </script>
   <h2>The ball n is {ball}{color}</h2>



   <button type="button" class="btn btn-outline-warning" on:click={handleClick}>RED</button>
   <button type="button" class="btn btn-outline-danger">Danger</button>