<script>
import { writable } from "svelte/store";

let photos = [
	{ src: "https://ik.imagekit.io/ari/2022ischia001", alt: "Ischia 01" },
	{ src: "https://ik.imagekit.io/ari/2022ischia02", alt: "Ischia 02" },
	{ src: "https://ik.imagekit.io/ari/2022ischia03", alt: "Ischia 03" },
	{ src: "https://ik.imagekit.io/ari/2014bergen03", alt: "Bergen 03" },
	{ src: "https://ik.imagekit.io/ari/2014bergen02", alt: "Bergen 02" },
	{ src: "https://ik.imagekit.io/ari/2014berlin01", alt: "Berlin 01" },
	{ src: "https://ik.imagekit.io/ari/2014bergen01", alt: "Bergen 04" },
	{ src: "https://ik.imagekit.io/ari/2014dublin02", alt: "Dublin 02" },
];

// Shuffle array
photos.sort(() => Math.random() - 0.5);

// Reactive variable for the current main image
let currentPhoto = writable(photos[0]);

/**
 * @param {{ src: string; alt: string; }} photo
 */
const updateMainPhoto = (photo) => {
	currentPhoto.set(photo);
};



</script>


<main>
  <div class="main-image-container">
    <a href="/about">
      <p>Arien Shibani</p>
    </a>
    {#if $currentPhoto}
      <img
        class="main-image"
        src={$currentPhoto.src + "?tr=h-1032,w-1032"}
        alt={$currentPhoto.alt}
        fetchpriority="high"
        loading="eager"
      />
    {/if}
  </div>

  <div class="thumbnail-strip" >
    {#each photos as photo}
      <button type="button" on:click={() => updateMainPhoto(photo)}>
        <img
          class="thumbnail"
          src={photo.src + "?tr=h-100,w-100"}
          alt={photo.alt}
          />
      </button>
    {/each}
  </div>
</main>

<style>
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    padding: 1em;
    box-sizing: border-box;
  }

  .main-image-container {
    flex: 1;
    justify-content: center;
    align-items: center;
    max-width: 1062px;
    max-height: 1062px; /* Ensure the image does not exceed 80% of the viewport height */
    overflow: hidden;
  }

  .main-image {
    max-width: 100%;
    max-height: 100%;
    object-fit: contain; /* Ensure the image scales correctly */
  }

  .thumbnail-strip {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 20px;
    overflow-x: auto; /* Allow horizontal scrolling on small screens */
    white-space: nowrap; /* Prevent line break and keep thumbnails in a row */
    width: 80vw;
    /* Black scrollbar  */
    scrollbar-color: #ffffff rgb(0, 0, 0);
    scrollbar-width: thin;
  }

  .thumbnail {
    margin: 0 0.5em;
    cursor: pointer;
    transition: transform 0.3s ease;
    width: 100px; /* Adjust thumbnail size as needed */
    height: 100px; /* Adjust thumbnail size as needed */
    flex: 0 0 auto; /* Prevent flex items from shrinking */
    filter: invert(1); /* Negative effect */
    opacity: 50%;
  }

  .thumbnail:hover,
  .thumbnail:active {
    opacity: 100%;
  }

  @media (max-width: 600px) {
    .thumbnail {
      width: 80px; /* Adjust thumbnail size for mobile */
      height: 80px; /* Adjust thumbnail size for mobile */
    }

    .main-image-container {
      max-height: 50vh; /* Adjust main image height for mobile */
    }
  }

  button{
    background-color: transparent;
    border: none;
  }

  p{
    font-size: 1em;
    width: 10px;
    font-family: 'Arial', sans-serif;
    font-weight: bold;
}

a{
  text-decoration: none;
  color: white;
}
</style>
