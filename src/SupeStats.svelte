<script lang="ts">
    export let supe;
    import {show_power_stats} from "./stores.js"
    $: console.log($show_power_stats)
    const show_powerstats = (id) => {
        for( var i = 0; i <  $show_power_stats.length; i++) {

            if ($show_power_stats[i] === id) {
                $show_power_stats.splice(i, 1);
            }
        }
        $show_power_stats =  $show_power_stats;
    }
</script>

<main>
    <div class="supe_flex_box" >
        <div id="supe_image">
            <img src="{supe.images.sm}" alt="Image of {supe.name}" width="150"/>
        </div>
        <div id="supe_general_info" class="supe_card_content_{supe.biography.alignment}">
            <div class="supe_general_info_spacer">
            <h1>{supe.name}</h1>
            <p>Fullname: {supe.biography.fullName}</p>
            <p>Race: {supe.appearance.race}</p>
            <p>Alignment: {supe.biography.alignment}</p>
            <p>Publisher: {supe.biography.publisher}</p>
            </div>
            <div class="supe_general_info_spacer">
            <h2>Powers:</h2>
            <p>Intelligence: {supe.powerstats.intelligence}%</p>
            <p>Strength: {supe.powerstats.strength}%</p>
            <p>Speed: {supe.powerstats.speed}%</p>
            <p>Durability: {supe.powerstats.durability}%</p>
            <p>Power: {supe.powerstats.durability}%</p>
            <p>Combat: {supe.powerstats.combat}%</p>
            </div>
        </div>
        <div id="supe_stats_button" on:click={() => show_powerstats(supe.id)} class="btn">+</div>
    </div>
</main>

<style>
    .supe_flex_box {
        display: flex;
        flex-direction: row;
        /*justify-content: center;*/
        max-width: 600px;
        width:600px;
        height: 300px;
    }

    .supe_flex_box > #supe_image {
        max-height: 500px;
        max-width: 200px;
    }

    .supe_flex_box > #supe_general_info {
        /*width: 100px;*/
        text-align: left;
        /*line-height: 60px;*/
        font-size: 12px;
        width: 300px;
        max-width: 300px;
        height: 270px;
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
    .supe_card_content_good {
        text-align: left;
        border: 1px #666666;
        border-radius: 20px;
        color: blue;
    }
    .supe_card_content_bad {
        text-align: left;
        border: 1px #666666;
        border-radius: 20px;
        color: crimson;
    }

    .supe_general_info_spacer {
        margin-left: 10px;
        line-height: 10px;
        font-size: 10px;
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

    #supe_stats_button {
        position: relative;
        right:30px;

    }
    .btn {
        height: 30px;
        line-height: 30px;
        width: 30px;
        font-size: 1.5em;
        border-radius: 50%;
        text-align: center;
        cursor: pointer;
    }
</style>
