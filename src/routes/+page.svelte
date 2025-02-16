<script>

  import Menu from "$lib/components/menu.svelte";

</script>

<style>




  .container {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    color: white;
    margin: 5% auto;
    margin-right: 5%;
    width: 60%;
    max-width: 1200px;
    gap: 2rem;
  }

  .text-content {
    flex: 1;
    font-size: small;
  }

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
        margin-top: 55% !important;
        margin-left: 0%;
        display: flex;
        margin: auto;
    }

    .text-content {
      width: 80%;
      text-align: justify;
      margin-top: 60%;
    }

    .image-container {
      width: 100%;
    }
  }
</style>


<Menu />

<div class="container" >
  <div class="text-content" style="font-family:avenir;font-size:x-small;margin-top:7%">
    <h2>2024</h2>
    <p>November 05 | Erthe Runway Show’24, Plantroom, London</p>
    <p>April 20 | Niche Lnd, The Baths House, London</p>
    <p>March 07 | The Sound Of The Divine Feminine, Diwine Grapes, London</p>
    <p>February 08 | Ferm Of The Wick, London</p>

    <h2>2023</h2>
    <p>December 14 | The Marquis Of Conrwallis, London</p>
    <p>December 03 | Playground Jam, The Baths House, London</p>
    <p>November 24 | Opening Rituals, London</p>
    <p>August 5 | GATE Festival’23, Guilford</p>
    <p>January 28 | Internal Objects Presents, Unit D4, London</p>

    <h2>2022</h2>
    <p>December 06 | Creatures, London</p>
    <p>November 26 | Internal Objects Presents, Unit D4, London</p>
    <p>August 3 | GATE Festival’24, Guilford</p>
    <p>March 18 | Gather All The Electronics, Algha Works, London</p>
  </div>

  <div class="image-container">
    <img src="/Home page .jpg" alt="Event Image">
  </div>
</div>
