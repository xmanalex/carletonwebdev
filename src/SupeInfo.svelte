<script lang="ts">
   import { onMount } from 'svelte';
   import Supe from "./Supe.svelte"
   import {show_power_stats} from "./stores.js"

   let supeinfo = [];

   let search = "";

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
   <div class="inner_supe_cards_display">
      <input type="search" bind:value={search} id="search_element" class="ms-auto w-auto" placeholder="Search" />
      {#each visibleSupes as supe}
         {#if $show_power_stats.includes(supe.id)}
         <Supe {supe} />
            {:else }
         <Supe {supe} />
         {/if}
      {/each}
   </div>
   </div>
</main>

<style>

   .inner_supe_cards_display {
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
   #search_element {
      width: 100%;
   }
</style>
