<script lang="ts">
	export let filename: string;
	export let lang: string;
	export let fullBleed: boolean | undefined = undefined;

	let codeContent: HTMLElement;
	let isCopied = false;

	// Copy the code inside the slot
	async function copyCode() {
		if (codeContent) {
			const codeText = codeContent.textContent?.trim() || '';
			try {
				await navigator.clipboard.writeText(codeText);
				isCopied = true;

				// Reset copy state after 2 seconds
				setTimeout(() => (isCopied = false), 2000);
			} catch (error) {
				alert('Failed to copy code.');
			}
		}
	}
</script>

<div class="code-block" class:full-bleed={fullBleed}>
	{#if filename}
		<div class="filename">{filename}</div>
	{/if}
	{#if lang}
		<div class="lang">{lang}</div>
	{/if}
	<!-- Copy button -->
	<button class="copy-button" on:click={copyCode}>
		{#if isCopied}
			Copied!
		{:else}
			📋
		{/if}
	</button>

	<!-- Slot containing the code -->
	<div bind:this={codeContent} class="code-container">
		<slot />
	</div>
</div>

<style lang="scss">
	.code-block {
		display: block;
		position: relative;
		background-color: var(--color--code-background);
		color: var(--color--code-text);
		font-family: var(--font--mono);
		font-size: 1rem;
		line-height: 1.33em;
		border-radius: 8px;
		box-shadow: var(--card-shadow);

		padding: 30px 15px;
		margin: 30px 0;

		:global(pre) {
			overflow-x: auto;
			scrollbar-color: var(--color--primary) var(--color--primary-tint);
			scrollbar-width: thin;
			padding-bottom: 5px;

			&::-webkit-scrollbar {
				height: 8px;
			}
			&::-webkit-scrollbar-thumb {
				background: var(--color--primary);
				&:hover {
					background: var(--color--primary-shade);
				}
			}
		}

		.lang {
			position: absolute;
			right: 0;
			top: -15px;
			background: inherit;
			border-radius: 8px;
			padding: 5px 10px;
			z-index: 2;
			font-size: 0.85em;
		}

		.filename {
			background: inherit;
			border-top-left-radius: 8px;
			border-top-right-radius: 8px;
			margin-bottom: -2px;
			padding: 5px 10px;
			position: absolute;
			left: 0px;
			top: -15px;
			z-index: 1;
		}
		.copy-button {
			position: absolute;
			right: 40px;
			top: -15px;
			background: var(--color--code-background);
			color: white;
			border: none;
			border-radius: 10px;
			padding: 5px 8px;
			font-size: 0.8rem;
			cursor: pointer;
			transition: background 0.2s ease;

			&:hover {
				background: var(--color--primary-shade);
			}
		}
	}
</style>
