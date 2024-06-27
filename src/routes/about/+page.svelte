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

    p{
        font-weight: normal;
    }

    h1{
        font-weight: bold;
        margin-top: 5em;
    }

    a{
        color: white;
    }

  </style>

  <main>

    <!-- Main image container -->
    <div class="main-image-container">
        <h1>Who's Arien Shibani</h1>
        <p>He takes pictures with his fancy camera.</p>

        <h1>Can i buy his work?</h1>
        <p>Not everything is for sale. </p>

        <h1>Can I use his work for something?</h1>
        <p>Probably. Send me a <a href="mailto:aaari94@gmail.com">mail</a></p>

    </div>


  </main>