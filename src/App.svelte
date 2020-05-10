<script>
	const words = {
		noun: [
			"coronavirus",
			"the NHS"
		],
		verb: [
			"stop",
			"protect"
		]
	}

	export const word = function(type) {
		const randomIndex = Math.floor(Math.random() * words[type].length)
		return words[type][randomIndex]
	};

	const randomWords = function() {
		return [
			"verb",
			"noun",
			"verb",
			"noun"
		].map(word)
	}

	export const slogan = function() {
		const phrase = randomWords()
		return `${phrase[0]} ${phrase[1]}. ${phrase[2]} ${phrase[3]}.`
	}
</script>

<main>
	<h1>{slogan()}</h1>
</main>

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