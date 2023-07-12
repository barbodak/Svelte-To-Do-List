<script lang='ts'>
	let name = 'barbod';
	let cnt = 0;
	function incrementCnt():void{
		cnt++;
	}
</script>

<h1>{name.toUpperCase()}</h1>
<br>
<p>{cnt}</p>
<button on:click={incrementCnt}>
	click to make bigger number
</button>


<style>
	h1 {
		color: rgb(79, 102, 55);
		font-family: 'Courier New', Courier, monospace;
		font-size: 2em;
	}
</style>