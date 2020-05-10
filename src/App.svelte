<script>
	const words = {
		positive: {
			verb: [
				"protect",
				"save",
				"help"
			],
			object: [
				"the NHS",
				"lives",
				"the public"
			]
		},
		negative: {
			verb: [
				"stop",
				"kill",
				"control"
			],
			object: [
				"coronavirus",
				"the virus",
				"the disease"
			]
		},
		intransitive: {
			verb: [
				"stay",
				"be",
				"remain"
			],
			object: [
				"at home",
				"alert",
				"with us"
			]
		}
	}

	const sampleFrom = function(arr) {
		return arr[Math.floor(Math.random() * arr.length)]
	}

	const addWord = function(acc, wordType) {
		const possibleWords = words[wordType.phrase][wordType.word].filter(
			function(w) { return !acc.includes(w) }
		)
		const word = sampleFrom(possibleWords)
		return [...acc, word]
	}

	const randomPhraseType = function() {
		return sampleFrom(["positive", "negative", "intransitive"])
	}

	const randomWords = function() {
		const phraseTypes = [
			randomPhraseType(),
			randomPhraseType(),
			randomPhraseType()
		]
		return [
			{phrase: phraseTypes[0], word: "verb"},
			{phrase: phraseTypes[0], word: "object"},
			{phrase: phraseTypes[1], word: "verb"},
			{phrase: phraseTypes[1], word: "object"},
			{phrase: phraseTypes[2], word: "verb"},
			{phrase: phraseTypes[2], word: "object"}
		].reduce(addWord, [])
	}

	export const slogan = function() {
		const phrase = randomWords()
		return `${phrase[0]} ${phrase[1]}. ${phrase[2]} ${phrase[3]}. ${phrase[4]} ${phrase[5]}.`
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