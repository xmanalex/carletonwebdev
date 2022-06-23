<script lang="ts">
    export let supe;
</script>

<main>
    <div class="supe_flex_box" >
        <div id="supe_image">
            <img src="{supe.images.sm}" alt="Image of {supe.name}"/>
        </div>
        <div id="supe_general_info" class="supe_card_content">
            <div class="supe_general_info_spacer">
            <h1>{supe.name}</h1>
            <p>Fullname: {supe.biography.fullName}</p>
            <p>Race: {supe.appearance.race}</p>
            <p>Alignment: {supe.biography.alignment}</p>
            <p>Publisher: {supe.biography.publisher}</p>
            </div>
        </div>
        <span>+</span>
    </div>
</main>

<style>
    .supe_flex_box {
        display: flex;
        flex-direction: row;
        /*justify-content: center;*/

    }

    .supe_flex_box > #supe_image {
        text-align: right;
        max-height: 220px;
    }

    .supe_flex_box > #supe_general_info {
        /*width: 100px;*/
        text-align: left;
        /*line-height: 60px;*/
        font-size: 12px;
        width: 300px;
        height: 199px;
        border: 1px solid lightgrey;
        border-left-style: none;
        box-sizing: border-box;
        border-radius: 0px 10px 10px 0px;align-self: flex-start;
    }

    .supe_flex_box > span {
        /*width: 100px;*/
        /*margin: 10px;*/
        text-align: right;
        /*line-height: 60px;*/
        font-size: 12px;
        max-height: 220px;
    }
    .supe_card_content {
        text-align: left;
        border: 1px #666666;
        border-radius: 20px;
    }

    .supe_general_info_spacer {
        margin-left: 10px;
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
