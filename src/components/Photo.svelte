<script>
  export let src = "";
  export let alt = "";
  export let width = "100%";
  export let height = "auto";

  let loaded = false;

  function handleImageLoad() {
    loaded = true;
    // You can trigger animations or other effects here
  }
</script>

<style>
  .photo-container {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 1em;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    overflow: hidden;
    aspect-ratio: 1;
  }
</style>

<div class="photo-container">
  <img
    {src} {alt}
    class="photo"
    style="width: {width}; height: {height};"
    loading="lazy"
  />
</div>