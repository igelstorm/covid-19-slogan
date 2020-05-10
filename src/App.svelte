<script>
	const words = {
		positive: {
			verb: [
				"Protect",
				"Save",
				"Help",
				"Preserve",
				"Guard",
				"Defend",
			],
			object: [
				"the NHS",
				"lives",
				"Britain",
				"the public",
				"the people",
				"key workers",
				"productivity",
				"businesses",
				"the GDP",
			]
		},
		negative: {
			verb: [
				"Stop",
				"Kill",
				"Control",
				"Avoid",
				"Fight",
				"Prevent",
				"Quash",
				"Quell",
				"Put an end to",
				"Crush",
				"Eliminate",
			],
			object: [
				"coronavirus",
				"the virus",
				"disease",
				"transmission",
				"the pandemic",
				"the epidemic",
				"the plague",
				"the scourge",
				"the affliction",
				"the blight",
			]
		},
		intransitive: {
			verb: [
				"Stay",
				"Always be",
				"Remain",
				"Keep on being",
			],
			object: [
				"at home",
				"alert",
				"safe",
				"with us",
				"vigilant",
				"watchful",
				"on your guard",
				"wary",
				"careful",
				"cautious",
				"prudent",
				"conscientious",
				"mindful",
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
	<p>The latest advice from the UK Government:</p>
	<p class="slogan">{slogan()}</p>
	<p>Refresh the page for more.</p>
	<p><small>
		This is satire. For official advice and guidance from the UK Government, see: <a href="https://www.gov.uk/coronavirus">https://www.gov.uk/coronavirus</a>
	</small></p>
</main>

<style>
	main {
		text-align: center;
		padding: 5rem 1rem;
		margin: 0 auto;
	}

	p {
		font-family: 'Open Sans', sans-serif;
		font-weight: 400;
		font-size: 1rem;
		margin: 1.2em 0;
	}

	.slogan {
		font-family: 'Open Sans', sans-serif;
		font-weight: 800;
		font-size: 2rem;
	}

	@media (min-width: 640px) {
		main {
			max-width: 800px;
		}

		.slogan {
			font-size: 3rem;
		}
	}
</style>
