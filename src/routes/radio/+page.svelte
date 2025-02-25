<script>
    import Menu from "$lib/components/menu.svelte";
    // Image Gallery Data
    let images = [
      { src: "/radio/1 Threads radio.jpg", link: "https://soundcloud.com/threadsradio/seshtan-hackney-wick-22-jan-24?in=seshtan/sets/threads-radio" },
      { src: "/radio/2 Loose Lips.JPG", link: "https://soundcloud.com/loose-lips123/loose-lips-mix-series-434-seshtan?in=seshtan/sets/radio-shows" },
      { src: "/radio/3 Threads.png", link: "https://soundcloud.com/seshtan/threads-radio-gate-w-seshtan-21-feb-23?in=seshtan/sets/threads-radio" },
      { src: "/radio/4 (square).jpg", link: "https://soundcloud.com/seshtan/playground-jam-baths-house-london" },
      { src: "/radio/5 Threads.png", link: "https://soundcloud.com/threadsradio/gate-w-bart-seshtan-and-craft-ebbing-hackney-wick-09-jul-24" }
    ];
  
    let currentIndex = 0;
  
    function prevImage() {
      currentIndex = (currentIndex - 1 + images.length) % images.length;
    }
  
    function nextImage() {
      currentIndex = (currentIndex + 1) % images.length;
    }
  
    function setImage(index) {
      currentIndex = index;
    }
  </script>
  
  <style>
    /* Center the gallery */
    .gallery-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      width: 90%;
      max-width: 600px;
      margin: auto;
      color: white;
      text-align: center;
    }
  
    /* Main Image Styling */
    .main-image-container {
      position: relative;
      width: 100%;
      max-width: 400px;
      aspect-ratio: 1 / 1; /* Ensures a square shape */
      overflow: hidden;
      border-radius: 10px;
      margin-top: 10%;
    }
  
    .main-image {
      width: 100%;
      height: 100%;
      object-fit: cover; /* Ensures images fit without stretching */
      border-radius: 10px;
      cursor: pointer;
      transition: opacity 0.3s ease-in-out;
    }
  
    /* Navigation Buttons */
    .nav-button {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      background: rgba(0, 0, 0, 0.6);
      border: none;
      color: white;
      font-size: 1.5rem;
      cursor: pointer;
      padding: 10px;
      z-index: 10;
      transition: background 0.3s ease-in-out;
    }
  
    .nav-button:hover {
      background: rgba(0, 0, 0, 0.8);
    }
  
    .left {
      left: 10px;
    }
  
    .right {
      right: 10px;
    }
  
    /* Thumbnails */
    .thumbnails {
      display: flex;
      justify-content: center;
      margin-top: 15px;
      gap: 10px;
      flex-wrap: wrap;
    }
  
    .thumbnail {
      width: 60px;
      height: 60px;
      object-fit: cover;
      border-radius: 5px;
      cursor: pointer;
      transition: opacity 0.3s;
      border: 2px solid transparent;
    }
  
    .thumbnail:hover {
      opacity: 0.7;
    }
  
    .thumbnail.active {
      border: 2px solid #8072ff;
    }
  
    @media (max-width: 768px) {
      .gallery-container {
        width: 100%;
        margin-top: 50%;
      }
  
      .main-image-container {
        max-width: 90%;
        aspect-ratio: 1 / 1;
      }
  
      .thumbnail {
        width: 50px;
        height: 50px;
      }
    }
  </style>
  
  <Menu/>
  
  <div class="gallery-container">
    <!-- Main Image -->
    <div class="main-image-container">
      <button class="nav-button left" on:click={prevImage}>
        ~
      </button>
  
      <a href={images[currentIndex].link} target="_blank">
        <img class="main-image" src={images[currentIndex].src} alt="Gallery Image">
      </a>
  
      <button class="nav-button right" on:click={nextImage}>
       ~
      </button>
    </div>
  
    <!-- Thumbnails -->
    <div class="thumbnails">
      {#each images as image, index}
        <img
          src={image.src}
          class="thumbnail {index === currentIndex ? 'active' : ''}"
          alt="Thumbnail"
          on:click={() => setImage(index)}
        />
      {/each}
    </div>
  </div>
  