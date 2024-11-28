<script>
    import { onMount } from 'svelte';
    import { tweened } from 'svelte/motion';
    import { quintOut } from 'svelte/easing';
  
    import { faInstagram } from '@fortawesome/free-brands-svg-icons';
    import { FontAwesomeIcon } from '@fortawesome/svelte-fontawesome';
  
  
    let images = [];
    let currentIndex = 0;
    let currentImage = '';
    const fadeDuration = 400;
    const scaleEffect = tweened(1, {
      duration: fadeDuration,
      easing: quintOut
    });
  
    onMount(() => {
      // Replace this with dynamic loading if necessary
      images = [
        'portfolio/Images Web1.png',
        'portfolio/Images Web2.png',
        'portfolio/Images Web3.png',
        'portfolio/Images Web4.png',
        
        'portfolio/Images Web5.png',
        'portfolio/Images Web6.png',
        'portfolio/Images Web7.png',
        'portfolio/Images Web8.png',
        
        'portfolio/Images Web9.png',
        'portfolio/Images Web10.png',
        'portfolio/Images Web11.png',
        'portfolio/Images Web12.png',
        
        'portfolio/Images Web13.png',
        'portfolio/Images Web14.png',
        'portfolio/Images Web15.png',
        'portfolio/Images Web16.png',
  
      ];
      currentImage = images[currentIndex];
    });
  
    function nextImage() {
      scaleEffect.set(0.9); // Scale down animation
      setTimeout(() => {
        currentIndex = (currentIndex + 1) % images.length;
        currentImage = images[currentIndex];
        scaleEffect.set(1); // Reset scale
      }, fadeDuration / 2);
    }
  
    function prevImage() {
      scaleEffect.set(0.9); // Scale down animation
      setTimeout(() => {
        currentIndex = (currentIndex - 1 + images.length) % images.length;
        currentImage = images[currentIndex];
        scaleEffect.set(1); // Reset scale
      }, fadeDuration / 2);
    }
  </script>
  
  <style>
  
  @font-face {
      font-family: 'big carlson';
      src: url('big-caslon-regular.ttf');
  }
  
  * {
    font-family: 'big carlson';
  }
  
    .gallery {
      display: flex;
      flex-direction: column;
      align-items: center;
      
      cursor: url('https://raw.githubusercontent.com/treyhunner/responsive-css-cursors/main/cursors/banana.cur'), auto;
  
      justify-content: center;
      width: 100%;
      height: 100vh;
      background-color: white;
      overflow: hidden;
    }
  
    .image-container {
      position: relative;
      width: 90%;
      max-width: 60%;
      overflow: hidden;
    }
  
    img {
      width: 100%;
      height: auto;
      object-fit: cover;
      display: block;
    }
  
    .controls {
      display: flex;
      justify-content: space-between;
      width: 100%;
      max-width: 600px;
      margin-top: 20px;
      font-size: 4em;
    }
  
    button {
  
    background-color: transparent;
      border: 1px none transparent;
      /* border-radius: 50%; */
      width: 200px;
      height: 400px;
      font-size: 9rem;
      margin-left: -30%;
      margin-right: -30%;
      margin-top: -75%;
      /* margin: 5%; */
      z-index: 100;
      display: flex
  ;
      align-items: center;
      justify-content: center;
      /* box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); */
      transition: transform 0.2s;
  }
  
  
  
    button:active {
      transform: scale(0.9);
    }
  
    .name{
      position: fixed;top:0;left:50px;font-family:big carlson;font-size:3em;z-index:10; letter-spacing: 2px;
    }
  
    .role{
      position: fixed;top:100px;left:50px;font-family:big carlson;letter-spacing: 2px;
    }
  .instagram-logo {
      position: fixed;
      top: 20px;
      color:black;
      right: 50px;
      height: 440px;
      z-index: 10;
      cursor: pointer;
      transition: transform 0.2s ease-in-out;
    }
  
    
     * {cursor: url('https://raw.githubusercontent.com/treyhunner/responsive-css-cursors/main/cursors/banana.cur'), auto;
  
  }
  @media only screen and (max-width: 600px) {
  
  .image-container{
    
  position: relative;
     
      width: 100%;
      max-width: 100%;
      overflow: hidden;
  
  }
  
  .controls{
    display: flex
  ;
      justify-content: space-between;
      width: 70%;
      max-width: 600px;
      margin-top: 20px;
      font-size: 4em;
  }
  .name{
    position: fixed;
          top: 59px;
          right: 100px;
          font-family: big carlson;
          font-weight: bolder;
          font-size: 4em;
          z-index: 10;
  }
  .role{
    position: fixed;
      letter-spacing: 1px;
      margin-top: 53%;
      top: 100px;
      left: 50px;
      font-family: big carlson;
  }
  button{
    margin-top: -100%;
    font-size: 1em;
  
  }
  }
  </style>
  
  <h1 class="name">Bianca Trombi</h1>
  <p style="position: fixed;top:50px;right:50px;font-family:monospace;letter-spacing:1px;">Get in touch: <b style="letter-spacing:2px;font-family:monospace">bianca.trombi1[at]gmail.com</b></p>
  
  <h3 class="role">Creative Direction & Production</h3> 
  
  <div class="gallery"> 
    <div class="image-container" transition:scale="{scaleEffect}">
      {#if currentImage}
        <img src="/{currentImage}" alt="Portfolio Image" />
      {/if}
    </div>
    <div class="controls">
      <button on:click={prevImage} aria-label="Previous Image">
        <img src="b.png" alt="">
      </button>
      <button on:click={nextImage} aria-label="Next Image">
        <img src="a.png" alt="">
      </button>
    </div>
  </div>
  
  <a href="https://www.instagram.com/seshtan__/" target="_blank" class="instagram-logo">
    <FontAwesomeIcon icon={faInstagram} />
  </a>
  