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
      <div class="supe_flex_box" >
         <div>
            <img src="{supe.images.sm}" alt="Image of {supe.name}"/>
         </div>
         <div class="supe_card_content">
            <h1>{supe.name}</h1>
            <p>Fullname: {supe.biography.fullName}</p>
            <p>Race: {supe.appearance.race}</p>
            <p>Alignment: {supe.biography.alignment}</p>
            <p>Publisher: {supe.biography.publisher}</p>
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
      max-width: 500px;
      margin: 0 auto;
      padding: 1em;
   }

   .supe_card_container {
      max-height: 180px;
      width: 500px;
      border-radius: 10px;
      text-align: left;
      /*margin-bottom: 1em;*/
      /*padding: 5px 5px 5px 0px;*/
   }
   .supe_card_content {
      /*margin-left: 10px;*/
      max-height: 100px;
      text-align: left;
      border: 1px #666666;
      border-radius: 20px;
   }

   img {
      height: 90%;
      border-radius: 10px 0px 0px 10px;
      /*max-width: 50%;*/
      /*max-height: 70%;*/
   }
   .supe_flex_box {
      display: flex;
      flex-direction: row;
      height: 250px;
   }
</style>