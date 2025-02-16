<script>
  import { onMount, onDestroy } from 'svelte';
  import Menu from '$lib/components/menu.svelte';
  
  let heroIntersecting = true;
  let previousScroll = 0;
  let observer;       // store to destroy if needed
  let handleScroll;   // store so we can remove it

  onMount(() => {
    // -- IntersectionObserver only in browser --
    const heroSection = document?.getElementById('heroSection');
    if (heroSection && typeof IntersectionObserver !== 'undefined') {
      observer = new IntersectionObserver(([entry]) => {
        heroIntersecting = entry.isIntersecting;
      }, { threshold: 0.1 });
      observer.observe(heroSection);
    }

    // -- Define scroll handler + add it in onMount --
    handleScroll = () => {
      const scrollY = window.pageYOffset || document.documentElement.scrollTop;

      // Hero parallax
      const heroImage = document?.querySelector('.hero-image[data-parallax="true"]');
      if (heroImage) {
        const offset = scrollY * 0.2;
        heroImage.style.setProperty('--parallax-offset', `-${offset}px`);
      }

      // Transition section parallax
      const parallaxBg = document?.getElementById('parallaxBg');
      if (parallaxBg) {
        const rect = parallaxBg.getBoundingClientRect();
        if (rect.top < window.innerHeight && rect.bottom > 0) {
          const offset = scrollY * 0.15;
          parallaxBg.style.transform = `translateY(${-10 - offset}px)`;
          parallaxBg.style.opacity = `${1 - offset * 0.0005}`;
        }
      }

      previousScroll = scrollY;
    };
    window.addEventListener('scroll', handleScroll);
  });

  onDestroy(() => {
    if (observer) observer.disconnect();
    if (handleScroll) window.removeEventListener('scroll', handleScroll);
  });

  function scrollTo(sectionId) {
    // only call in browser
    if (typeof document !== 'undefined') {
      const el = document.getElementById(sectionId);
      if (el) el.scrollIntoView({ behavior: 'smooth' });
    }
  }
</script>


<style>
  :global(body) {
    margin: 0;
    padding: 0;
    background: #000;
    color: #fff;
    font-family: 'Avenir', sans-serif;
    overflow-x: hidden;
  }

  /* -----------------------------
     STICKY TOP NAV (MENU)
  ----------------------------- */
  .header {
    position: fixed;
    top: 0;
    width: 100%;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 1rem;
    z-index: 999;
    background: rgba(0,0,0,0.7);
    backdrop-filter: blur(5px);
    transition: background-color 0.3s, box-shadow 0.3s;
  }

  .header.scrolled {
    background: rgba(0,0,0,0.9);
    box-shadow: 0 2px 5px rgba(0,0,0,0.5);
  }

  .site-title {
    font-size: 1.2rem;
    font-weight: 600;
  }

  /* -----------------------------
     HERO SECTION
  ----------------------------- */
  .hero {
    position: relative;
    width: 100%;
    height: 100vh; 
    overflow: hidden;
  }

  .hero-image-wrapper {
    position: absolute;
    top: 0; 
    left: 0;
    width: 100%;
    height: 226vh;


    overflow: hidden;
    z-index: 1;
  }
  
  .hero-image {
    width: 100%;
    height: 100%;
    object-fit: cover; /* Make the hero image more pronounced */
    object-position: center;
    display: block;

    /* Fade-in animation */
    opacity: 0;
    animation: fadeInHero 1.5s ease forwards;
  }

  .hero-image[data-parallax="true"] {
    transform: translateY(var(--parallax-offset, 0));
    transition: transform 0.1s linear;
  }

  /* Fade in the hero image */
  @keyframes fadeInHero {
    to {
      opacity: 1;
    }
  }

  .hero-overlay {
    position: absolute;
    top: 0; left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(to bottom, rgba(0,0,0,0.4), rgba(0,0,0,0.8));
    z-index: 2;
  }

  .hero-content {
    position: relative;
    z-index: 3;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100%;
    text-align: center;
    padding: 1rem;
    animation: fadeInUp 1s ease forwards;
    opacity: 0;
    transform: translateY(20px);
  }

  .hero-content h1 {
    font-size: 3rem;
    margin-bottom: 1.5rem;
    letter-spacing: 1px;
  }

  .hero-content p {
    font-size: 1.1rem;
    margin-bottom: 2rem;
    max-width: 700px;
    line-height: 1.6;
    opacity: 0.95;
  }

  .scroll-down-arrow {
    display: inline-block;
    cursor: pointer;
    font-size: 2rem;
    margin-top: 1rem;
    color: #fff;
    transition: transform 0.3s ease;
  }
  .scroll-down-arrow:hover {
    transform: translateY(5px);
  }

  @keyframes fadeInUp {
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  /* -----------------------------
     EVENTS SECTION
  ----------------------------- */
  .events-section {
    position: relative;
    padding: 6rem 1rem 4rem;
    background: #000;
  }

  .events-title {
    text-align: center;
    font-size: 2rem;
    margin-bottom: 1.5rem;
    letter-spacing: 1px;
  }

  .events-grid {
    max-width: 800px;
    margin: 0 auto;
  }

  .year-title {
    margin: 2rem 0 1rem;
    font-size: 1.2rem;
    text-transform: uppercase;
    letter-spacing: 1px;
  }

  .event-date {
    margin: 0.4rem 0;
    font-size: 0.95rem;
    color: #ddd;
  }

  /* -----------------------------
     PARALLAX TRANSITION SECTION
  ----------------------------- */
  .parallax-section {
    position: relative;
    width: 100%;
    min-height: 50vh;
    overflow: hidden;
    background: #000;
  }

  .parallax-bg {
    position: absolute;
    top: 0; 
    left: 0;
    width: 100%;
    height: 120%;
    background: url('/Home page .jpg') center center / cover no-repeat;
    transform: translateY(-10%);
    transition: transform 0.2s linear, opacity 0.4s ease;
    z-index: 1;
  }

  .parallax-overlay {
    position: absolute;
    top: 0; left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.4);
    z-index: 2;
  }

  .parallax-content {
    position: relative;
    z-index: 3;
    text-align: center;
    padding: 3rem 1rem;
    min-height: 50vh;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }

  .parallax-content h2 {
    font-size: 2.5rem;
    margin-bottom: 1rem;
  }

  .parallax-content p {
    max-width: 600px;
    margin-bottom: 2rem;
  }

  /* -----------------------------
     ALBUMS SECTION (Scroll-Snap Parallax)
  ----------------------------- */
  .albums-section {
    position: relative;
    width: 50%;
    float:right;
    background: #111;
  }

  /* The wrapper that does vertical scrolling + snap */
  .albums-wrapper {
    position: relative;
    height: 100vh;                /* Full viewport height for snapping */
    overflow-y: scroll;           /* Scrolling within this container */
    scroll-snap-type: y mandatory;
    scroll-behavior: smooth;
    
    /* Hide scrollbars for WebKit-based browsers */
    -webkit-overflow-scrolling: touch;
  }

  /* Hide the scrollbar for Chrome, Safari and Opera */
  .albums-wrapper::-webkit-scrollbar {
    width: 0;
    background: transparent; /* optional: just in case */
  }

  /* Hide scrollbar in Firefox */
  .albums-wrapper {
    scrollbar-width: none;  /* Firefox */
    -ms-overflow-style: none; /* IE/Edge */
  }

  /* Each "slide" (album) is 1 full screen in height */
  .album {
    position: relative;
    width: 100%;
    height: 100%;
    scroll-snap-align: start;
    background-attachment: scroll;
    background-size: contain;
    background-position: unset;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  /* A dark overlay for better text contrast */
  .album-overlay {
    position: absolute;
    top: 0; 
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    z-index: 1;
  }

  .album-content {
    position: relative;
    z-index: 2;
    max-width: 600px;
    text-align: center;
    padding: 1rem;
  }

  .album-content h3 {
    font-size: 2rem;
    margin-bottom: 1rem;
    letter-spacing: 0.5px;
  }

  .album-content p {
    font-size: 1.1rem;
    margin-bottom: 1.5rem;
    line-height: 1.6;
  }

  .stream-button {
    display: inline-block;
    margin-top: 1rem;
    background-color: #fff;
    color: #000;
    padding: 0.75rem 1.25rem;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    font-size: 1rem;
    transition: background-color 0.3s, box-shadow 0.3s;
  }
  .stream-button:hover {
    background-color: #66bb6a;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  }

  /* -----------------------------
     MEDIA QUERIES
  ----------------------------- */
  @media (max-width: 768px) {
    .header {
      height: 50px;
    }
    .site-title {
      font-size: 1rem;
    }
    .hero-content h1 {
      font-size: 2rem;
    }
    .hero-content p {
      font-size: 1rem;
    }

    .album-content h3 {
      font-size: 1.4rem;
    }

    .hero{
      height:85vh;
    }

    .hero-image-wrapper{
      height:100vh;
    }
    .albums-section {

    width: 100%;
  }

  .album {
    background-size: cover;
  }
  }
</style>

<!-- HEADER / MENU -->
<Menu />

<!-- HERO (Shows entire image) -->
<section class="hero" id="heroSection">
  <div class="hero-image-wrapper">
    <img
      src="/Home page .jpg"
      alt="Hero Image"
      class="hero-image"
      data-parallax="true"
    />
  </div>
  <div class="hero-overlay"></div>
  <div class="hero-content">
    <!-- Optional headline or call-to-action -->

  </div>
</section>

<!-- EVENTS SECTION -->
<section class="events-section" id="eventsSection">
  <h2 class="events-title">Performances</h2>
  <div class="events-grid">
    <div class="year-title">2024</div>
    <div class="event-date">November 05 | Erthe Runway Show’24, Plantroom, London</div>
    <div class="event-date">April 20 | Niche Lnd, The Baths House, London</div>
    <div class="event-date">March 07 | The Sound Of The Divine Feminine, Diwine Grapes, London</div>
    <div class="event-date">February 08 | Ferm Of The Wick, London</div>

    <div class="year-title">2023</div>
    <div class="event-date">December 14 | The Marquis Of Cornwallis, London</div>
    <div class="event-date">December 03 | Playground Jam, The Baths House, London</div>
    <div class="event-date">November 24 | Opening Rituals, London</div>
    <div class="event-date">August 05 | GATE Festival’23, Guilford</div>
    <div class="event-date">January 28 | Internal Objects Presents, Unit D4, London</div>

    <div class="year-title">2022</div>
    <div class="event-date">December 06 | Creatures, London</div>
    <div class="event-date">November 26 | Internal Objects Presents, Unit D4, London</div>
    <div class="event-date">August 03 | GATE Festival’24, Guilford</div>
    <div class="event-date">March 18 | Gather All The Electronics, Algha Works, London</div>
  </div>
</section>

<h2 class="events-title">Albums</h2>
<!-- ALBUMS SECTION with Scroll Snap Parallax -->
<section class="albums-section" id="albumsSection">

  <div class="albums-wrapper">
    <!-- ALBUM 1 -->
    <div 
      class="album" 
      style="background-image: url('albums/malikai.jpeg');"
    >
      <div class="album-overlay"></div>
      <div class="album-content">
        <h3>MÁLIKAI</h3>
        <p>The album explores the subtle and intricate qualities of the colours produced through the harp and the transformative nature of its tones through
          extended techniques. Inspired by Málikai, ceremonial songs performed during rites of passage in Wakuénai cosmologies, the album creates
          mystical soundscapes that transcend conventional instrumental approaches by exploring diverse physical methods of sound synthesis. </p>
        <button class="stream-button">Stream</button>
      </div>
    </div>

    <!-- ALBUM 2 -->
    <div 
      class="album" 
      style="background-image: url('albums/heliconia.jpeg');"
    >
      <div class="album-overlay"></div>
      <div class="album-content">
        <h3>HELICONIA</h3>
        <p>Recorded in between England and Brazil, the album is an intimate journey through ambient soundscapes with ethereal textures,
          meditative melodies, and rhythmic patterns. Constructed from unwritten improvisations, strings intertwine with field recordings from
          tropical islands, flutes, shakers, and local drums gathered throughout my travels. </p>
        <button class="stream-button">Stream</button>
      </div>
    </div>

    <!-- ALBUM 3 -->
    <div 
      class="album" 
      style="background-image: url('albums/live.jpeg');"
    >
      <div class="album-overlay"></div>
      <div class="album-content">
        <h3>LIVE//uncut</h3>
        <p>Unedited and uncut, this album consists of long, pure, uninterrupted takes that explore free improvisation as a tool for storytelling.</p>
           
        <button class="stream-button">Stream</button>
      </div>
    </div>

  </div>
</section>
