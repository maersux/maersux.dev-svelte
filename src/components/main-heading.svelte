<script lang="ts">
  import { onMount } from 'svelte';

  interface Timing {
    readonly pause: number;
    readonly delete: number;
    readonly write: number;
  }

  const timing: Timing = {
    pause: 2000,
    delete: 75,
    write: 100
  };

  const steps: string[] = ['maersux', 'marcel'];

  let currentStep: number = 0;
  let displayText: string = '';

  const getCommonPrefix = (a: string, b: string): string => {
    let i = 0;
    while (i < a.length && i < b.length && a[i] === b[i]) {
      i++;
    }
    return a.slice(0, i);
  };

  onMount(() => {
    const typeAnimation = (): void => {
      const currentText: string = steps[currentStep];
      const nextText: string = steps[(currentStep + 1) % steps.length];
      const commonPrefix: string = getCommonPrefix(currentText, nextText);

      let index: number = displayText.length;

      const typingInterval = setInterval(() => {
        if (index < nextText.length) {
          displayText = nextText.slice(0, index + 1);
          index++;
        } else {
          clearInterval(typingInterval);

          setTimeout(() => {
            eraseAnimation(commonPrefix);
          }, timing.pause);
        }
      }, timing.write);
    };

    const eraseAnimation = (commonPrefix: string): void => {
      const currentText: string = steps[currentStep];

      let index: number = currentText.length;

      const erasingInterval = setInterval(() => {
        if (index > commonPrefix.length) {
          displayText = displayText.slice(0, index - 1);
          index--;
        } else {
          clearInterval(erasingInterval);

          currentStep = (currentStep + 1) % steps.length;
          typeAnimation();
        }
      }, timing.delete);
    };

    typeAnimation();
  });
</script>

<h1>
  <span class="text-gradient">Hi, I am</span>
  <span class="typewriter">{displayText}</span>
</h1>

<style>
    h1 {
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
        font-size: 2.25rem;
        font-weight: var(--font-weight-black);
    }

    @media only screen and (min-width: 768px) {
        h1 {
            font-size: 3.75rem;
        }
    }

    .typewriter {
        position: relative;
    }

    .typewriter::after {
        content: '|';
        margin-left: 0.2rem;
        animation: blink 0.7s steps(2, start) infinite;
        color: var(--text-color);
    }

    @keyframes blink {
        to {
            visibility: hidden;
        }
    }
</style>