<script>
	import Player from './Player.svelte'
	let redScore = 0;
	let blueScore = 0;
	$: blueWon = redScore <= 0;
	$: redWon = blueScore <= 0;
	$: gameOver = redWon || blueWon;

	function newGame() {
		alert('new game!');
		redScore = 20;
		blueScore = 20;
	}

	// function updateBlueScore(e) {
	// 	const updateScore = e.detail;
	// 	blueScore += updateScore;
	// }

</script>

<main>
	<h1>Magic the Gathering Counter</h1>
	<div id="controls-container">
		<Player
			{gameOver}
			fontColor="red"
			won={redWon}
			winningText="Red wins"
			bind:score={blueScore}
		/>
		<Player 
			{gameOver}
			fontColor="blue" 
			won={blueWon} 
			winningText="Blue wins" 
			bind:score={redScore}
		/>
	</div>
	<button on:click={newGame}>Start Game</button>
</main>

<style>
	main {
		width: 80%;
		padding: 20px;
		border: solid gray 1px;
		margin: 0 auto;
		background-color: wheat;
		margin: 10vh auto;
	}

	#controls-container {
		display: flex;
	}

	button {
		display: block;
		width: 100%;
		margin-top: 20px;
		border: solid salmon 1px;
		background-color: sandybrown;
		color: rgb(61, 56, 56);
		font-size: 20px;
		border-radius: 3px;
	}
</style>