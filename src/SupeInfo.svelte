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
      <img src="{supe.images.sm}"/>
      <h1>{supe.name}</h1>
      <p>Fullname: {supe.biography.fullname}</p>
      <p>Race: {supe.appearance.race}</p>
      <p>Alignment: {supe.biography.alignment}</p>
      <p>Publisher: {supe.biography.publisher}</p>
   {/each}
   </div>
</main>

<style>
   #cards_display {
      background: #fff;
      border-radius: 20px;
      border:1px solid black;
      text-align: center;
      padding: 1em;
      max-width: 400px;
      margin: 0 auto;
   }
   img {
      border-radius: 5px 5px  5px 5px;
   }
</style>