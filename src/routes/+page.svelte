<script lang="ts">
	import MainHeading from '$/components/main-heading.svelte';
  import Socials from '$/components/socials.svelte';
</script>

<svelte:head>
	<title>maersux' website</title>
  <meta name="description" content="i'm just this random dev guy. currently working on modchecker.com and susgeebot. twitch viewer doing twitch stuff i guess." />

  <meta property="og:title" content="maersux' website">
  <meta property="og:description" content="i'm just this random dev guy. currently working on modchecker.com and susgeebot. twitch viewer doing twitch stuff i guess.">
  <meta property="og:locale" content="en_US">
  <meta property="og:image" content="https://maersux.dev/appa.png">
  <meta property="og:image:height" content="256">
  <meta property="og:image:width" content="256">
  <meta property="og:type" content="website">

  <meta name="twitter:card" content="summary_large_image">
  <meta name="twitter:title" content="maersux' website">
  <meta name="twitter:description" content="i'm just this random dev guy. currently working on modchecker.com and susgeebot. twitch viewer doing twitch stuff i guess.">
  <meta name="twitter:image" content="https://maersux.dev/appa.png">
  <meta name="twitter:image:height" content="256">
  <meta name="twitter:image:width" content="256">
</svelte:head>

<section>
  <MainHeading />
  <Socials />
</section>

<style>
    section {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: var(--space-md);
        padding: var(--space-md)
    }

    @media only screen and (min-width: 768px) {
        section {
            padding: var(--space-lg);
        }
    }
</style>