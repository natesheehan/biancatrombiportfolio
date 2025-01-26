<script>

    import { faInstagram } from '@fortawesome/free-brands-svg-icons';
    import { FontAwesomeIcon } from '@fortawesome/svelte-fontawesome';
  
  </script>
  
  <style>
  
  @font-face {
      font-family: 'big carlson';
      src: url('big-caslon-regular.ttf');
  }
  
  * {
    font-family: 'big carlson';
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
  
  <h1 class="name">SESHTAN</h1>
  
  
  <a href="https://www.instagram.com/seshtan__/" target="_blank" class="instagram-logo">
    <FontAwesomeIcon icon={faInstagram} />
  </a>
  