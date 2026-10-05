<script>
  import LanguageButton from "../Utilities/LanguageButton.svelte";
  import CVDownloadButton from "../Utilities/CVDownloadButton.svelte";

  export let currentPath = "/";

  let scrollY = 0;
  $: isScrolled = scrollY > 80;

  let showMobileMenu = false;
  const toggleMobileMenu = () => {
    showMobileMenu = !showMobileMenu;
  };

  const links = [
    { label: "Work", href: "/#work" },
    { label: "Projects", href: "/#projects" },
    { label: "About", href: "/#about" },
  ];
</script>

<svelte:window bind:scrollY />

<header
  class={`fixed top-0 left-0 right-0 z-50 transition-all duration-300 ease-out py-10 bg-main-light`}
>
  <div class="relative flex items-center justify-center px-6 md:px-10">
    <a
      href="/"
      class="absolute left-10 font-anton transition-all duration-300 text-5xl"
    >
      NILS HALBACH
    </a>

    <nav
      class={`hidden md:flex gap-8 absolute top-1/2 -translate-y-1/2 transition-all 
      ${isScrolled ? "right-50" : "left-1/2 -translate-x-1/2"}`}
    >
      {#each links as link}
        <a
          href={link.href}
          class="relative transition-all duration-200 text-base hover:text-white hover:scale-125"
        >
          {link.label}
          {#if currentPath === link.href}
            <span class="absolute -bottom-1 left-0 right-0 h-0.5 bg-white"
            ></span>
          {/if}
        </a>
      {/each}
    </nav>

    <div class="absolute right-6">
      <!-- Mobile -->
      <button
        class="md:hidden flex flex-col justify-center items-center w-8 h-8"
        on:click={toggleMobileMenu}
        aria-label="Menu"
      >
        <span class="block w-6 h-0.5 bg-primary mb-1"></span>
        <span class="block w-6 h-0.5 bg-primary mb-1"></span>
        <span class="block w-6 h-0.5 bg-primary"></span>
      </button>

      <!-- Desktop -->
      <div class="hidden md:flex items-center gap-4">
        <CVDownloadButton />
        <!-- <LanguageButton /> -->
      </div>

      <!-- Mobile Dropdown -->
      {#if showMobileMenu}
        <div class="md:hidden absolute right-0 top-full mt-2 bg-main-light p-4 rounded shadow-lg z-50 min-w-40 flex flex-col gap-2">
          <CVDownloadButton />
          <!-- <LanguageButton /> -->
        </div>
      {/if}
    </div>
  </div>
</header>
