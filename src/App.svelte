<script>
  import svelteLogo from './assets/svelte.svg';
  import viteLogo from '/vite.svg';
  import Counter from './lib/Counter.svelte';

  const tailwindcssSrc =
    'https://upload.wikimedia.org/wikipedia/commons/thumb/d/d5/Tailwind_CSS_Logo.svg/512px-Tailwind_CSS_Logo.svg.png?20230715030042';
</script>

<main class="flex flex-col justify-center items-center min-h-screen">
  <div class="flex justify-center items-center gap-5">
    <a href="https://vitejs.dev" target="_blank" rel="noreferrer">
      <img src={viteLogo} class="logo" alt="Vite Logo" />
    </a>
    <a href="https://svelte.dev" target="_blank" rel="noreferrer">
      <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
    </a>
    <a href="https://tailwindcss.com/">
      <img src={tailwindcssSrc} class="logo tailwind" alt="Tailwind CSS Logo" />
    </a>
  </div>
  <h1 class="text-5xl font-bold my-9">Vite + Svelte + TailwindCSS</h1>

  <div class="card p-8">
    <Counter />
  </div>

  <p class="my-4">
    Check out <a
      href="https://github.com/sveltejs/kit#readme"
      target="_blank"
      rel="noreferrer"
      class="font-medium text-[#646cff] hover:text-[#535bf2]">SvelteKit</a
    >, the official Svelte app framework powered by Vite!
  </p>

  <p class="read-the-docs">Click on the Vite and Svelte logos to learn more</p>
</main>

<style>
  .logo {
    height: 10em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .logo.tailwind:hover {
    filter: drop-shadow(0 0 2em #38bdf8aa);
  }
  .read-the-docs {
    color: #888;
  }
</style>
