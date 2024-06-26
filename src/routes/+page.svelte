<script>
import Button from "../components/Button.svelte";
import Photo from "../components/Photo.svelte";
</script>

<main>
    <div class="mainPhoto">
        <Photo src="//live.staticflickr.com/2854/13245068254_6dd578c586_b.jpg"/>
    </div>
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding-top: 20px;
    }

    .mainPhoto {
        display: flex;
        justify-content: center;
        @media (orientation: portrait) {
            height: 50vh;
        }
    }
</style>
