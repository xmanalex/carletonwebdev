<script lang="ts">
    export let supe;
    import {show_power_stats, social_tags, supe_tags} from "./stores.js"
    $: console.log($supe_tags)

    const show_powerstats = (id) => {
        for( var i = 0; i <  $show_power_stats.length; i++) {

            if ($show_power_stats[i] === id) {
                $show_power_stats.splice(i, 1);
            }
        }
        $show_power_stats =  $show_power_stats;
    }

    const add_supe_tag = () => {
        let a_tag_value:string = document.getElementById("add_tag_element").value;
        $social_tags = [...$social_tags, a_tag_value];
        //clear value from tag input
        document.getElementById("add_tag_element").value = ""
    }

    const tag_supe_hero = (tag,id) => {
        $supe_tags = [  ...$supe_tags,
            {id: id,
            tag: tag,}
        ]
        // $supe_tags.push({ id: id, tag: tag,})
        // $supe_tags = $supe_tags;
        console.log(tag,id)
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
            <div class="supe_general_info_spacer">
                <h2>Tags:</h2>
                <input type="search"  id="add_tag_element" placeholder="Add tag" /><button on:click={() => add_supe_tag()}>Add Tag</button>
            </div>
            <div class="supe_general_info_spacer">
                {#each $social_tags as tag }
                    <button on:click={tag_supe_hero(tag,supe.id)}>{tag}</button>
                {/each}
            </div>
        </div>
        <div id="supe_stats_button" on:click={() => show_powerstats(supe.id)} class="btn">+</div>
    </div>
</main>

<style>
    .supe_flex_box {
        display: flex;
        flex-direction: row;
        max-width: 600px;
        width:700px;
        height: 420px;
    }

    .supe_flex_box > #supe_image {
        max-height: 700px;
        max-width: 200px;
    }

    .supe_flex_box > #supe_general_info {
        /*width: 100px;*/
        text-align: left;
        /*line-height: 60px;*/
        font-size: 12px;
        width: 300px;
        max-width: 300px;
        height: 378px;
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
