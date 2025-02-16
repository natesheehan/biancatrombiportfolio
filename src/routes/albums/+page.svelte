<script>
    import Menu from "$lib/components/menu.svelte";
  </script>
  
  <Menu />
  
  <style>
    .container {
      max-width: 1200px;
      margin: 5% auto;
      padding: 1rem;
      color: white;
      font-family: Avenir, sans-serif;
      margin-top: 15%;
    }
  
    /* Grid layout for the iframes */
    .album-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(600px, 1fr));
      gap: 2rem;
      justify-items: center; /* center each item horizontally */
    }
  
    /* Common iframe styling */
    .album-iframe {
      border: 0;
      width: 100%;         /* take full column width */
      max-width: 400px;    /* do not exceed 400px if space is larger */
    }
  
    /* Mobile adjustments */
    @media (max-width: 768px) {
      .container {
        margin-top: 50%;
      }
    }
  </style>
  
  <div class="container">
    <div class="album-grid">
      <!-- Màlikai -->
      <iframe 
        class="album-iframe" 
        style="height: 373px;"
        src="https://bandcamp.com/EmbeddedPlayer/album=750660449/size=large/bgcol=333333/linkcol=0687f5/artwork=small/transparent=true/"
        seamless
      >
        <a href="https://seshtan.bandcamp.com/album/m-likai">Màlikai by Seshtan</a>
      </iframe>
  
      <!-- Heliconia -->
      <iframe 
        class="album-iframe" 
        style="height: 406px;"
        src="https://bandcamp.com/EmbeddedPlayer/album=287790237/size=large/bgcol=333333/linkcol=0687f5/artwork=small/transparent=true/"
        seamless
      >
        <a href="https://seshtan.bandcamp.com/album/heliconia">Heliconia by Seshtan</a>
      </iframe>
  
      <!-- Dancing Waves -->
      <iframe 
        class="album-iframe" 
        style="height: 208px;"
        src="https://bandcamp.com/EmbeddedPlayer/album=4005541801/size=large/bgcol=333333/linkcol=0687f5/artwork=small/transparent=true/"
        seamless
      >
        <a href="https://seshtan.bandcamp.com/album/dancing-waves">Dancing Waves by Seshtan</a>
      </iframe>
  
      <!-- Selvα -->
      <iframe 
        class="album-iframe" 
        style="height: 208px;"
        src="https://bandcamp.com/EmbeddedPlayer/album=2795375922/size=large/bgcol=333333/linkcol=0687f5/artwork=small/transparent=true/"
        seamless
      >
        <a href="https://seshtan.bandcamp.com/album/selv">Selvα ོ by Seshtan &amp; SebastianO</a>
      </iframe>
  
      <!-- Bahian Tapes -->
      <iframe 
        class="album-iframe" 
        style="height: 241px;"
        src="https://bandcamp.com/EmbeddedPlayer/album=152984243/size=large/bgcol=333333/linkcol=0687f5/artwork=small/transparent=true/"
        seamless
      >
        <a href="https://seshtan.bandcamp.com/album/bahian-tapes">Bahian Tapes by Seshtan with Bira Santos</a>
      </iframe>
  
      <!-- Live // uncut -->
      <iframe 
        class="album-iframe" 
        style="height: 307px;"
        src="https://bandcamp.com/EmbeddedPlayer/album=3450866183/size=large/bgcol=333333/linkcol=0687f5/artwork=small/transparent=true/"
        seamless
      >
        <a href="https://seshtan.bandcamp.com/album/live-uncut">Live // uncut by Seshtan</a>
      </iframe>
    </div>
  </div>
  