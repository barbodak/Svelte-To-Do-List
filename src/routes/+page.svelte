<script lang='ts'>
	let name = 'Graphic Disign Is My passion';
	let r = 0;
	let g = 0;
	let b = 0;
	let cnt = 0;
	let clicked = false;
	let rootElement:any;
	$: rootElement && rootElement.style.setProperty('--color', `rgb(${r}, ${g}, ${b})`);
	function f(a: number):string {
		a = Math.floor(a);
		return (a < 10? a.toString() : a === 10? 'A': a === 11? 'B': a === 12? 'C': a === 13? 'D': a === 14? 'E': 'F');
	}
	function rgbToHex(r: number, g: number, b: number): any {
		let res = "#";
		res += f(r/16) + f(r%16) + f(g/16) + f(g%16) + f(b/16) + f(b%16);
		return res;
	}
	function sleep(ms:any) {
    return new Promise((resolve) => setTimeout(resolve, ms ?? 200));
  }
  async function transitionTo(tr:number, tg: number, tb: number):Promise <void> {
	let mx = 50;
	let jr = (tr - r) / mx;
	let jg = (tg - g) / mx;
	let jb = (tb - b) / mx;
	while (mx + 2 > 0) {
		r += jr;
		b += jb;
		g += jg;
		mx--;
		await sleep(1);
	}
	await sleep(25);
	r = tr, g = tg, b = tb;
}
	async function rainbow(n:number):Promise<void>{
		clicked = true;
		console.log(n);
		await transitionTo(148, 1, 211);
		await transitionTo(75, 0, 130);
		await transitionTo(0, 1, 255);
		await transitionTo(2, 50, 254);
		await transitionTo(1, 255, 0);
		await transitionTo(50, 253, 0);
		await transitionTo(255, 254, 0);
		await transitionTo(255, 127, 1);
		await transitionTo(254, 0, 0);
		// await transitionTo(148, 1, 211);
		rainbow(n);
	}
	async function hand():Promise<void> {
		cnt++;
		rainbow(cnt);	
	}
</script>
<body>
<h1 style="color: {rgbToHex(r, g, b)};">{name}</h1>
<br>
<p>r : {r} | g : {g} | b : {b} | chicked : {clicked}</p>
<button on:click={hand}>
	click to make bigger number
</button>
<p>{rgbToHex(r, g, b)}</p>
</body>2



<style>
	body {
		/* background-color: #000000; */
		align-items: center;
		}
	h1 {
		font-family: -apple-system, BlinkMacSystemFont, sans-serif;
		font-size: 8em;
	}
</style>