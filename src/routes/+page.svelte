<script lang="ts">
  import type { PageData } from "./$types";
  import { generations } from "./generations";

  interface MonsterData {
    id: number;
    name: string;
    image: string;
  }

  interface Monster extends PageData {
    monsters: MonsterData[];
  }

  export let data: Monster; // special syntax for SvelteKit which allows us to pass data from the server to the client
</script>

<div class="generations">
  {#each generations as generation (generation.id)}
    <div class="generation">{generation.main_region}</div>
  {/each}
</div>

<div class="monsters">
  {#each data.monsters as monster (monster.id)}
    <div class="monster">
      <div class="monster-content">
        <img src={monster.image} alt={monster.name} />
        {monster.name}
      </div>
      <div class="monster-id">
        {monster.id}
      </div>
    </div>
  {/each}
</div>

<style>
  .generations {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
  }
  .generation {
    margin: 5px;
    padding: 5px 10px;
    border: 1px solid black;
    background-color: #ff0000;
    color: #ffffff;
  }
  .generation:hover {
    background-color: #00027c;
  }
  .monsters {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
  }
  .monster-id {
    position: absolute;
    top: 8px;
    left: 8px;
    font-size: 0.8em;
    color: #aaa;
  }
.monster {
    width: 100px;
    margin: 10px;
    padding: 10px;
    position: relative;
    background-color: #22ff00;
    transition: background-color 0.5s ease;
}

.monster:hover {
    background-color: #00ff95;
}
  .monster-content {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>
