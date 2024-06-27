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


  </style>

  <main>

    <!-- Main image container -->
    <div class="main-image-container">
      <p>About</p>

    </div>


  </main>