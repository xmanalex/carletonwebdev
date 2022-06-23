<script lang="ts">
   import { onMount } from 'svelte';
   import Supe from "./Supe.svelte"
   import SupeStats from "./SupeStats.svelte"
   import {show_power_stats, social_tags,supe_tags} from "./stores.js"

   let supeinfo = [];
   let search = "";

   //get remote data
   onMount(async () => {
      const res = await fetch('https://cdn.jsdelivr.net/gh/akabab/superhero-api@0.3.0/api/all.json');
      supeinfo = await res.json();
   });

   //search with filter for Supe names
   $: visibleSupes = search ?
           supeinfo.filter(supe => {
              return supe.name.match(`${search}.*`)
           }) : supeinfo;

   //filter supes by tag
   const filterHero = (filter) => {
      //find all supe names that have the tag filter request

      let test = $supe_tags.filter(supe => {
         return supe.tag.match("love")
      })
      console.log(test);

      // let mysmartvariable = supeinfo.filter(supe => {
      //    return supe.name.match(`${search}.*`)
      // })
      // console.log(mysmartvariable);
   }

</script>

<main>
   <div class="outer_supe_display">
   <div class="inner_supe_cards_display">
      <input type="search" bind:value={search} id="search_element" placeholder="Search" />
      <div class="supe_tag">
         {#each $social_tags as tag }
            <button on:click={filterHero(tag)}>{tag}</button>
         {/each}
      </div>
      {#each visibleSupes as supe}
         {#if $show_power_stats.includes(supe.id)}
         <SupeStats {supe} />
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
   .supe_tag {
      text-align: left;
   }
</style>
