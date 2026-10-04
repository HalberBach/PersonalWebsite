<script>
  import { onMount } from "svelte";

  let scrollY = 0;
  let maxScroll = 500;

  onMount(() => {
    const handleScroll = () => {
      scrollY = window.scrollY;
    };
    window.addEventListener("scroll", handleScroll, { passive: true });
    return () => window.removeEventListener("scroll", handleScroll);
  });

  $: progress = Math.min(scrollY / maxScroll, 1);
  $: offset = progress * 150; // amount of horizontal movement in pixels
  $: opacity = 1 - progress;
</script>

<div
  class="hero-text-wrapper uppercase font-bebas mx-auto max-w-5xl mb-20 mt-6 sm:mb-0 text-[4rem] sm:text-[10rem] 
  md:text-[16rem] leading-[0.73] md:tracking-[-0.02em] transform scale-y-[1.7] overflow-hidden md:overflow-visible"
>
  <p
    class="hero-line m-0 mt-3 text-left uppercase"
    style="transform: translateX(-{offset}px); opacity: {opacity};"
  >
    software
  </p>
  <p
    class="hero-line m-0 text-right uppercase"
    style="transform: translateX({offset}px); opacity: {opacity};"
  >
    developer
  </p>
</div>

<style>
  .hero-text-wrapper {
    display: flex;
    flex-direction: column;
    width: 100%;
  }

  .hero-line {
    width: 100%;
    will-change: transform, opacity;
    text-overflow: clip;
    white-space: nowrap;
  }
</style>
