<script>
	import EmailIcon from '$lib/icons/socials/email.svelte';
	import Experience from '$lib/icons/experience.svelte';
	import Button from '$lib/components/atoms/Button.svelte';
	import Sparkles from '../atoms/Sparkles.svelte';
</script>

<section id="hero">
	<h1 class="hello">Sager Alaskar</h1>
	<p class="intro">
		<span class="left">Marine Engineer,</span>
		<span class="right">Who is passionate in DevOps.</span>
	</p>
	<div class="ctas">
		<Sparkles>
			<Button href="mailto:sager@alaskar.dev">
				<EmailIcon slot="icon" />
				Mail me
			</Button>
		</Sparkles>
		<Button color="primary" href="/resume">
			<Experience slot="icon" />
			Resume
		</Button>
	</div>
</section>

<style lang="scss">
	@import '$lib/scss/breakpoints.scss';

	#hero {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 15px;
		position: relative;
		padding: 80px 0;

		@include for-phone-only {
			padding: 40px 0 50px;
		}

		.hello {
			text-align: center;
		}

		.intro {
			font-weight: 500;
			font-size: 1.4rem;
			width: min(100%, 440px);
			display: flex;
			flex-direction: column;

			.left {
				text-align: left;
			}
			.right {
				text-align: right;
			}

			@include for-phone-only {
				display: none;
			}
		}

		.ctas {
			display: flex;
			flex-wrap: wrap;
			align-items: center;
			justify-content: center;
			gap: 10px;
			width: 100%;
		}
	}
</style>
