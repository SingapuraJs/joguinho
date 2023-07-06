<script>
	let linha = false;
	let coluna = false;
	// let peca = ["../src/static/row-1-column-1.jpg"]
	function selecionarPeca(pc, i, j) {
		console.log (i, j) 
		if (primeiro === false) {
		primeiro = pc;
		linha = i;
		coluna = j;
	  } else {
		  segundo = pc;
		// console.log("peça 1:", primeiro);
		// console.log("peça 2:", segundo);
		trocarPosicao(primeiro, segundo,i,j);
		  primeiro = false;
		  segundo = false;
	}
}
  
	function trocarPosicao(p1, p2, i, j) {
		let temporal = p1;
		pecas[linha][coluna] = p2
		pecas[i][j] = temporal 
		linha = false;
		coluna = false;
		testarArray();
		console.log (pecas)
	  }
	  
	let primeiro = false;
	let segundo = false;

	
	let pecas = [
		
	  [{image: "/src/lib/images/row-1-column-1.jpg", value: 1},{image: "/src/lib/images/row-1-column-2.jpg", value: 2},{image: "/src/lib/images/row-1-column-3.jpg", value: 3}],
	  [{image: "/src/lib/images/row-2-column-1.jpg", value: 4},{image: "/src/lib/images/row-2-column-2.jpg", value: 5},{image: "/src/lib/images/row-2-column-3.jpg", value: 6}],
	  [{image: "/src/lib/images/row-2-column-4.jpg", value: 7},{image:"/src/lib/images/row-2-column-5.jpg", value: 9},{image: "/src/lib/images/row-1-column-1.jpg", value: 8}]
	];

	console.log(pecas[0])
	// let pecas = [
		
	// 	[{image: "", value: 5},{image: "", value: 2},{image: "", value: 7}],
	// 	[{image: "", value: 4},{image: "", value: 1},{image: "", value: 9}],
	// 	[{image: "", value: 8},{image: "", value: 3},{image: "", value: 6}],
	// 	[{image: "", value: 10},{image: "", value: 12},{image: "", value: 11}],
	// 	[{image: "", value: 13},{image: "", value: 14},{image: "", value: 15}],
	// 	[{image: "", value: 18},{image:"", value: 17},{image: "", value: 16}]
	//   ];
  
	let arrayCorreto = [
	  [{image: "", value: 1},{image: "", value: 2},{image: "", value: 3}],
	  [{image: "", value: 4},{image: "", value: 5},{image: "", value: 6}],
	  [{image: "", value: 7},{image:"", value: 8},{image: "", value: 9}]
	];

	// let arrayCorreto = [
	//   [{image: "", value: 1},{image: "", value: 2},{image: "", value: 3}],
	//   [{image: "", value: 4},{image: "", value: 5},{image: "", value: 6}],
	//   [{image: "", value: 7},{image: "", value: 8},{image: "", value: 9}],
	//   [{image: "", value: 10},{image:"", value:11},{image:"", value: 12}],
	//   [{image: "", value: 13},{image:"", value: 14},{image:"", value: 15}],
	//   [{image: "", value: 16},{image:"", value: 17},{image: "", value: 18}]
	// ];

	function testarArray (){
		for(let i = 0; i < pecas.length; i++){
			for(let j = 0; j < pecas[i].length; j++){
				if (pecas[i][j].value != arrayCorreto[i][j].value){
					console.log ("Não cabo !!")
					return 
				}
			}
		}
		console.log ("Cabo")
	} 
	
	
  </script>
  
  <table class="jogo">
	{#each pecas as row, i}
	{#each row as peca, j }
	

	<div class="table">
		
		<!-- svelte-ignore a11y-click-events-have-key-events -->
		<!-- svelte-ignore a11y-no-static-element-interactions -->
		<img class="peca" src="{peca.image}" on:click={() => {selecionarPeca(peca, i,j);}} alt="">
	</div>
	
	{/each}
 {/each}
</table>
  
  <style>
	table.jogo {
	  background: white;
	  grid-template-columns: repeat(3,auto);
	  display: grid;
	  justify-content: center;
	  align-items: center;

	}
		.peca{
			display: flex;
			grid-template-columns: repeat(3,auto);
			width: 150px;
			height: 165px;
			position: center;
			background: rgb(255, 255, 255);
    		padding: 0px;
			margin-top: 0%;
   	 		margin: auto;
    		box-shadow: 0px 0px  5px black;
			
		}


  </style>