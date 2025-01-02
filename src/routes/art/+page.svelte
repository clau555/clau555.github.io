<script lang="ts">
    const images: string[] = [
        "dragounet_march.jpg",
        "emerald_tyran.jpg",
        "lagiacrus.jpg",
        "afghan_girl.jpg",
        "ariane5.jpg",
        "leprunenec.jpg",
        "cool_guy.jpg",
        "raven.jpg",
        "raya_&_beep.jpg"
    ];
</script>

<div class="gallery">
    {#each images as image}
        <img src="/art/{image}" alt="artwork" />
    {/each}
</div>

<style>
    .gallery {
        display: flex;
        flex-wrap: wrap;
        column-gap: 16px;
        row-gap: 64px;
        flex-direction: row;
        justify-content: space-evenly;
    }

    img {
        width: auto;
        height: 400px;
        border-radius: 3px;
    }

    @media (max-width: 800px) {
        .gallery {
            row-gap: 16px;
        }

        img {
            width: 100%;
            height: auto;
        }
    }
</style>
