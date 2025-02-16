<script>
    import Menu from "$lib/components/menu.svelte";
  </script>
  
  <style>
    /* Main layout container */
    .container {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;
      color: white;
      margin: 5% auto;
      width: 60%;
      max-width: 1200px;
      gap: 2rem;
    }
  

    /* Text content */
    .text-content {
      flex: 1;
      font-size: x-small;
      text-align: justify;
      letter-spacing: 2px;
      font-family: 'avenir';
    }
  
    /* Image container */
    .image-container {
      flex: 1;
      display: flex;
      justify-content: center;
    }
  
    .image-container img {
      max-width: 80%;
      height: auto;
    }
  
    @media (max-width: 768px) {
      .container {
        flex-direction: column-reverse;
        text-align: center;
        margin-top: 60%;
      }
  
      .text-content {
        width: 100%;
      }
  
      .image-container {
        width: 100%;
      }
    }
  </style>
  

  <Menu />
  
  <div class="container">
    <!-- Text Content -->
    <div class="text-content" style="font-family:avenir;margin-top:5%">
      <p>
        Seshtan is an electro-acoustic experimental music project created in 2020 by
        self-taught harpist Bianca Trombi. The project reimagines the classical harp by
        blending its traditional sounds with unconventional techniques and effects. Her
        work focuses on the exploration of the ecology of sounds that a harp can produce,
        delving into free improvisation and extended techniques to create a wide range
        of textures, rhythms, and effects beyond its traditional role—from whistle-like
        tones and gong-like effects to xylophonic and percussive rhythms. These sounds
        are used to shape new auditory narratives, soundscapes, and non-idiomatic
        compositions, where the harp is the main character and primary source of sound,
        moving away from the conventions typically associated with the instrument.
      </p>
  
      <p>
        The project also incorporates various other instruments, including drums,
        percussions, and flutes, often accompanied by field recordings that evoke the
        more-than-human world.
      </p>
  
      <p>
        Over the past few years, Seshtan has performed at various events and venues
        across London, both solo and in collaboration with other musicians. She has
        produced two albums and hosted several radio shows on Threads Radio and
        Loose Lips. A particular highlight was a live, recorded performance at Niche
        Lnd with violinist Sebastiano Roberto, where they explored immersive, intimate
        soundscapes through free improvisation.
      </p>
  
      <p>
        Seshtan is ultimately a testament to my love for the harp as an instrument for
        music and healing.
      </p>
    </div>
  
    <!-- Image -->
    <div class="image-container">
      <img src="/about/_DSF2400.jpg" alt="Seshtan Music Project">
    </div>
  </div>
  