<script>
	const words = {
		positive: {
			verb: [
				"Defend",
				"Guard",
				"Help",
				"Preserve",
				"Protect",
				"Save",
			],
			object: [
				"Britain",
				"businesses",
				"key workers",
				"lives",
				"productivity",
				"the GDP",
				"the NHS",
				"the people",
				"the public",
			]
		},
		negative: {
			verb: [
				"Avoid",
				"Control",
				"Crush",
				"Eliminate",
				"Fight",
				"Kill",
				"Prevent",
				"Put an end to",
				"Quash",
				"Quell",
				"Stop",
			],
			object: [
				"coronavirus",
				"disease",
				"the affliction",
				"the blight",
				"the epidemic",
				"the pandemic",
				"the plague",
				"the scourge",
				"the virus",
				"transmission",
			]
		},
		intransitive: {
			verb: [
				"Always be",
				"Keep on being",
				"Remain",
				"Stay",
			],
			object: [
				"alert",
				"at home",
				"careful",
				"cautious",
				"conscientious",
				"mindful",
				"obedient",
				"on your guard",
				"prudent",
				"safe",
				"vigilant",
				"wary",
				"watchful",
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

	export const slogan = randomWords()
</script>

<main>
	<p>The latest advice from the UK Government:</p>
	<p class="slogan">{slogan[0]} {slogan[1]}.<br>{slogan[2]} {slogan[3]}.<br>{slogan[4]} {slogan[5]}.</p>
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
			max-width: 1200px;
		}

		.slogan {
			font-size: 3rem;
		}
	}
</style>
