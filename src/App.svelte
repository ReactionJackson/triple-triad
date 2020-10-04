<script>
	import { PLAYERS } from './constants'
	import { rand } from './utils/rand'
	import Board from './components/Board.svelte'
	import PlayerBoard from './components/PlayerBoard.svelte'

	let decks = [[], []]

	const getDecks = (async () => {
		const response = await fetch('https://triad.raelys.com/api/decks')
		const { results } = await response.json()
		decks = [
			results[rand(1, results.length)].cards,
			results[rand(1, results.length)].cards,
		]
	})()

</script>

<main>
	<PlayerBoard
		username="Quills"
		player={ PLAYERS.P1 }
		deck={ decks[PLAYERS.P1] }
	/>
	<Board decks={ decks } />
	<PlayerBoard
		username="Joe"
		player={ PLAYERS.P2 }
		deck={ decks[PLAYERS.P2] }
	/>
</main>

<style>
	main {
		display: flex;
		justify-content: center;
		transform: scale(0.75);
	}
</style>
