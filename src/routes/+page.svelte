<script lang="ts">
  import { invoke } from "@tauri-apps/api/tauri";

  let name = $state("");
  let greetMsg = $state("");

  async function greet(event: Event) {
    event.preventDefault();
    greetMsg = await invoke("greet", { name });
  }
</script>

<main class="mx-0 pt-[10vh] flex flex-col justify-center text-center">
  <h1 class="text-center">Welcome to Tauri + Svelte</h1>

  <div class="flex justify-center">
    <a href="https://vite.dev" target="_blank">
      <img src="/vite.svg" class="logo vite h-24 p-6 transition duration-750 hover:drop-shadow-[0_0_2em_#747bff]" alt="Vite Logo" />
    </a>
    <a href="https://tauri.app" target="_blank">
      <img src="/tauri.svg" class="logo tauri h-24 p-6 transition duration-750 hover:drop-shadow-[0_0_2em_#24c8db]" alt="Tauri Logo" />
    </a>
    <a href="https://svelte.dev" target="_blank">
      <img src="/svelte.svg" class="logo svelte-kit h-24 p-6 transition duration-750 hover:drop-shadow-[0_0_2em_#ff3e00]" alt="SvelteKit Logo" />
    </a>
  </div>
  <p class="mt-2">Click on the Tauri, Vite, and SvelteKit logos to learn more.</p>

  <form class="flex justify-center mt-4" onsubmit={greet}>
    <input id="greet-input" placeholder="Enter a name..." bind:value={name} class="rounded-lg border border-transparent px-4 py-2 text-base font-medium text-gray-900 bg-white shadow-md transition duration-200 focus:outline-none mr-2 dark:text-white dark:bg-gray-900/60" />
    <button type="submit" class="rounded-lg border border-transparent px-4 py-2 text-base font-medium text-gray-900 bg-white shadow-md transition duration-200 cursor-pointer hover:border-blue-600 active:bg-gray-100 focus:outline-none dark:text-white dark:bg-gray-900/60 dark:active:bg-gray-800/40">Greet</button>
  </form>
  <p class="mt-4">{greetMsg}</p>
</main>
