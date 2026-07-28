<script>
  let lang = "EN";

  const toggleLanguage = () => {
    lang = lang === "EN" ? "DE" : "EN";
  };
</script>

<button
  type="button"
  class="w-10 h-10 border-2 bg-primary border-primary text-secondary text-lg font-anton transition"
  on:click={toggleLanguage}
>
  {lang}
</button>

<style>
  .bg-primary:hover {
    color: var(--primary);
    background-color: var(--neutral-light);
  }
</style>
