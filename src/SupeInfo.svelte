<script lang="ts">
   import { onMount } from 'svelte';

   let supeinfo = [];

   onMount(async () => {
      const res = await fetch('https://cdn.jsdelivr.net/gh/akabab/superhero-api@0.3.0/api/all.json');
      supeinfo = await res.json();
   });
</script>

<main>
   <div id="cards_display">
   {#each supeinfo as supe}
      <div class="supe_card_container">
         <div class="card_row">
            <div class="card_column">
               <img src="{supe.images.sm}" alt="Image of {supe.name}"/></div>
            <div class="card_column">
               <div class="supe_card_content">
               <h1>{supe.name}</h1>
               <p>Fullname: {supe.biography.fullname}</p>
               <p>Race: {supe.appearance.race}</p>
               <p>Alignment: {supe.biography.alignment}</p>
               <p>Publisher: {supe.biography.publisher}</p>
            </div></div>
         </div>

         <div class="supe_card_media">
            <img src="{supe.images.sm}"/>
         </div>

      </div>
   {/each}
   </div>
</main>

<style>
   #cards_display {
      background: #fff;
      border-radius: 20px;
      text-align: center;
      padding: 1em;
      max-width: 400px;
      margin: 0 auto;
   }

   .supe_card_container {
      width: 900px;
      margin-left: auto;
      margin-right: auto;
   }

   .supe_card_media {
      max-width: 50%;
      position: relative;
   }

   .supe_card_content {

   }

   .card_row {
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
      width: 100%;
   }

   .card_column {
      display: flex;
      flex-direction: column;
      flex-basis: 100%;
      flex: 1;
   }

   img {
      border-radius: 5px 5px  5px 5px;
      width: 100px;
   }
</style>