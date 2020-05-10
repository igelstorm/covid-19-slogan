<script>
	const words = {
		positive: {
			verb: [
				"protect",
				"help"
			],
			object: [
				"the NHS",
				"the public"
			]
		},
		negative: {
			verb: [
				"stop",
				"kill"
			],
			object: [
				"coronavirus",
				"the virus",
				"the disease"
			]
		}
	}

	export const addWord = function(acc, wordType) {
		const possibleWords = words[wordType.phrase][wordType.word].filter(
			function(w) { return !acc.includes(w) }
		)
		const randomIndex = Math.floor(Math.random() * possibleWords.length)
		const word = possibleWords[randomIndex]
		return [...acc, word]
	}

	const randomWords = function() {
		return [
			{phrase: "positive", word: "verb"},
			{phrase: "positive", word: "object"},
			{phrase: "negative", word: "verb"},
			{phrase: "negative", word: "object"}
		].reduce(addWord, [])
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