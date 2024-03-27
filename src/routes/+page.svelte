<script lang="ts">
  import type { PageData } from "./$types";
  import { generations } from "./generations";

    interface MonsterData {
        id: number;
        name: string;
    }

  interface Monster extends PageData {
    monsters: MonsterData[];
  }

  export let data: Monster; // special syntax for SvelteKit which allows us to pass data from the server to the client
</script>

{#each data.monsters as monster (monster.id)}
  <p>{monster.id}: {monster.name}</p>
{/each}

{#each generations as generation (generation.id)}
  <h1>{generation.name}</h1>
  <p>Games: {generation.games.join(", ")}</p>
  <p>Main region: {generation.main_region}</p>
{/each}

<style>
</style>
