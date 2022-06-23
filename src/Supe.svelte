<script lang="ts">
</script>

<main>
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
</main>

<style>
</style>