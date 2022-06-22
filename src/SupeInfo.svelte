<script lang="ts">
   import { onMount } from 'svelte';

   let supeinfo = [];

   onMount(async () => {
      const res = await fetch('https://cdn.jsdelivr.net/gh/akabab/superhero-api@0.3.0/api/all.json');
      supeinfo = await res.json();
   });
</script>

<main>
   {#each supeinfo as supe}
      <img src="{supe.images.sm}"/>
      <h1>{supe.name}</h1>
      <p>Fullname: {supe.biography.fullname}</p>
      <p>Race: {supe.appearance.race}</p>
      <p>Alignment: {supe.biography.alignment}</p>
      <p>Publisher: {supe.biography.publisher}</p>
   {/each}
</main>

<style>

</style>