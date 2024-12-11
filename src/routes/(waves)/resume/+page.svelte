<meta name="robots" content="noindex" />
<div class="min-h-screen">
	<div class="container">
		<iframe src="CV.pdf" title="Resume PDF" />
	</div>
</div>

<style>
	.min-h-screen {
		min-height: 100vh;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		z-index: 10; /* Ensure it's above the animation */
		position: relative; /* Make z-index take effect */
	}

	.container {
		width: 100%;
		max-width: 1024px;
		height: 100vh;
		background-color: #333;
		border-radius: 8px;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
		overflow: hidden;
	}

	iframe {
		width: 100%;
		height: 100%;
		border: none;
	}
</style>
