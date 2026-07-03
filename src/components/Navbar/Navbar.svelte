<script>
  export let currentPath = '/'; 

  let scrollY = 0;
  $: isScrolled = scrollY > 80;

  const links = [
    { label: 'About', href: '/#about' },
    { label: 'Work', href: '/#work' },
    { label: 'Contact', href: '/#contact' },
  ];
</script>

<svelte:window bind:scrollY />

<header
  class="fixed top-0 left-0 right-0 z-50 transition-all duration-300 ease-out
    {isScrolled ? 'bg-neutral-900/95 backdrop-blur py-2' : 'bg-black py-6'}"
>
<div class="relative flex items-center justify-center px-6 md:px-10">
  <a href="/" class="absolute left-6 font-display transition-all duration-300
    {isScrolled ? 'text-lg' : 'text-3xl md:text-4xl'}">
    NILS HALBACH
  </a>

  <nav class="hidden md:flex gap-8">
      {#each links as link}
        <a
          href={link.href}
          class="relative text-white/80 hover:text-white transition-colors
            {isScrolled ? 'text-sm' : 'text-base'}"
        >
          {link.label}
          {#if currentPath === link.href}
            <span class="absolute -bottom-1 left-0 right-0 h-[2px] bg-white"></span>
          {/if}
        </a>
      {/each}
  </nav>

  <span class="absolute right-6 border border-white/30 text-white text-xs px-2 py-1">
    EN
  </span>
</div>
</header>