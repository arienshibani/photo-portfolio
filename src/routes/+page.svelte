<script>
  import { writable } from 'svelte/store';

  let photos = [
    { src: 'https://ik.imagekit.io/ari/2022ischia001.JPG?updatedAt=1719499287997.jpg', alt: 'Photo 1' },
    { src: 'https://ik.imagekit.io/ari/2022ischia02?updatedAt=1719498858408.jpg', alt: 'Photo 2' },
    { src: 'https://ik.imagekit.io/ari/2022ischia03?updatedAt=1719498886685.jpg', alt: 'Photo 3' },
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
  }

</script>

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
    max-width: 100%;
    max-height: 80vh; /* Ensure the image does not exceed 80% of the viewport height */
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
    margin-top: 1em;
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
</style>

<main>

  <!-- Main image container -->
  <div class="main-image-container">
    <p>Arien Shibani</p>
    {#if $currentPhoto}
      <img src={$currentPhoto.src} alt={$currentPhoto.alt} class="main-image" />
    {/if}
  </div>

  <!-- Thumbnail strip -->
  <div class="thumbnail-strip">
    {#each photos as photo}
      <button type="button"  on:click={() => updateMainPhoto(photo)}>
        <img class="thumbnail" src={photo.src} alt={photo.alt} />
      </button>
    {/each}
  </div>
</main>
