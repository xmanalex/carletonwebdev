<script lang="ts">
    export let supe;
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
    .supe_flex_box {
        display: flex;
        flex-direction: row;
        justify-content: space-evenly;
    }
    .supe_card_content {
        text-align: left;
        border: 1px #666666;
        border-radius: 20px;
    }
    .power_stats_flex_box {
        display: flex;
        flex-direction: column;
    }
    img {
        height: 90%;
        border-radius: 10px 0px 0px 10px;
        /*max-width: 50%;*/
        /*max-height: 70%;*/
    }
</style>
