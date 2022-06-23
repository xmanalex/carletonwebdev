<script lang="ts">
   import { onMount } from 'svelte';
   import Supe from "./Supe.svelte"

   let supeinfo = [];

   let search = "Abraxas";

   onMount(async () => {
      const res = await fetch('https://cdn.jsdelivr.net/gh/akabab/superhero-api@0.3.0/api/all.json');
      supeinfo = await res.json();
   });

   $: visibleSupes = search ?
           supeinfo.filter(supe => {
              return supe.name.match(`${search}.*`)
           }) : supeinfo;
</script>

<main>

   <div class="outer_supe_display">
   <div id="cards_display">
      <input type="search" bind:value={search} class="ms-auto w-auto" placeholder="Search" />
   {#each visibleSupes as supe}
      <Supe {supe} />
   {/each}
   </div>
   </div>
</main>

<style>

   #cards_display {
      background: #fff;
      border-radius: 20px;
      text-align: center;
      max-width: 500px;
      margin: 0 auto;
      padding: 1em;
      overflow-y: auto;
      max-height: 900px;
   }
   .outer_supe_display {
      background: #fff;
      text-align: center;
      max-width: 500px;
      margin: 0 auto;
      padding: 1em;
      overflow: hidden;
      max-height: 900px;
      border-radius: 20px;
   }
</style>