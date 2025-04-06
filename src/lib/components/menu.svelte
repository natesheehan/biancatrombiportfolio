<script>
    // Icons
    import { faInstagram } from '@fortawesome/free-brands-svg-icons';
    import { FontAwesomeIcon } from '@fortawesome/svelte-fontawesome';

    // Mobile menu toggle state
    let menuOpen = false;

    // Toggle & close menu
    function toggleMenu() {
        menuOpen = !menuOpen;
    }

    function closeMenu() {
        menuOpen = false;
    }
</script>

<style>
    @font-face {
        font-family: 'big carlson';
        src: url('big-caslon-regular.ttf');
    }

    @font-face {
        font-family: 'snake';
        src: url('Snake Mix.ttf');
    }

    html, body {
        background-color: black;
        margin: 0;
        padding: 0;
    }

    /* HEADER STYLES */
    .header-container {
        position: fixed;
        top: 10px;
        left: 20px;
        z-index: 100;
        display: flex;
        align-items: center;
        gap: 20px;
    }

    .logo-letter {
        font-family: 'snake';
        color: white;
        font-size: 6em;
        margin: 0;
    }

    .site-name {
        font-family: 'big carlson';
        color: white;
        font-size: 5em;
        margin: 0;
    }

    .instagram-logo {
        position: fixed;
        top: 20px;
        right: 50px;
        color: white;
        z-index: 100;
        cursor: pointer;
        font-size: 2rem;
        transition: transform 0.2s ease-in-out;
    }

    .instagram-logo:hover {
        transform: scale(1.1);
    }

    /* MENU STYLES */
    .menu {
        position: fixed;
        left: 20px;
        top: 25%;
        letter-spacing: 3px;
        z-index: 100;
    }

    .menu ul {
        list-style-type: none;
        padding: 0;
    }

    .menu li {
        margin: 20px 0;
    }

    .menu a {
        color: #8072ff;
        text-decoration: none;
        font-size: 1.2rem;
        transition: color 0.2s ease-in-out;
        cursor: pointer;
    }

    .menu a:hover {
        color: #fff;
    }

    /* MOBILE MENU TOGGLE */
    .menu-toggle {
        display: none;
        position: fixed;
        top: 15px;
        left: 15px;
        background: transparent;
        color: white;
        border: none;
        font-size: 2rem;
        cursor: pointer;
        z-index: 101;
    }

    .menu-toggle:focus {
        outline: none;
    }

    /* Slide-in mobile menu */
    .mobile-menu {
        position: fixed;
        top: 0;
        left: 0;
        width: 70%;
        height: 100%;
        background: rgba(0, 0, 0, 0.9);
        color: white;
        transform: translateX(-100%);
        transition: transform 0.3s ease-in-out;
        padding: 20px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        box-shadow: 4px 0 10px rgba(0, 0, 0, 0.3);

        /* Ensure mobile menu is above overlay */
        z-index: 1001;
    }

    .mobile-menu.open {
        transform: translateX(0);
    }

    .mobile-menu ul {
        list-style-type: none;
        padding: 0;
        text-align: center;
    }

    .mobile-menu li {
        padding: 15px 0;
    }

    .mobile-menu a {
        color: #8072ff;
        text-decoration: none;
        font-size: 1.4rem;
        transition: color 0.2s ease-in-out;
    }

    .mobile-menu a:hover {
        color: white;
    }

    /* Close button */
    .close-menu {
        position: absolute;
        top: 15px;
        right: 20px;
        font-size: 2rem;
        cursor: pointer;
        color: #8072ff;
        transition: color 0.2s ease-in-out;
    }

    .close-menu:hover {
        color: white;
    }

    /* Overlay */
    .overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5);
        z-index: 100; /* below the mobile-menu */
        display: none;
    }

    .overlay.show {
        display: block;
    }

    @media (max-width: 768px) {
        /* Centered header on mobile */
        .header-container {
            left: 50%;
            transform: translateX(-50%);
            text-align: center;
            flex-direction: column;
            position: absolute;
            top: 0;
        }

        .logo-letter, .site-name {
            font-size: 3em;
        }

        .instagram-logo {
            position: relative;
            top: 0;
            right: 0;
            text-align: center;
            margin-top: 10px;
        }

        /* Hide desktop menu */
        .menu {
            display: none;
        }

        /* Show mobile menu button */
        .menu-toggle {
            display: block;
        }
    }
    
</style>

<!-- HEADER -->
<div class="header-container">
    <p class="logo-letter">e</p>
    <!-- Normal link back to home -->
    <a href="/" style="text-decoration: none;">
        <h1 class="site-name">Seshtan</h1>
    </a>
    <!-- Instagram link -->
    <a
      href="https://www.instagram.com/seshtan__/"
      target="_blank"
      class="instagram-logo"
    >
        <FontAwesomeIcon icon={faInstagram} />
    </a>
</div>

<!-- MOBILE MENU TOGGLE -->
<button class="menu-toggle" on:click={toggleMenu}>
    ☰
</button>

<!-- MOBILE MENU OVERLAY -->
{#if menuOpen}
    <div class="overlay show" on:click={closeMenu}></div>
{/if}

<!-- MOBILE MENU -->
<div class="mobile-menu {menuOpen ? 'open' : ''}">
    <!-- Close icon -->
    <span class="close-menu" on:click={closeMenu}>&times;</span>
    <ul>
        <!-- Normal anchor + closeMenu on click -->
        <li>
          <a href="/about" on:click={closeMenu}>About</a>
        </li>
        <li>
          <a href="/albums" on:click={closeMenu}>Music</a>
        </li>
        <li>
          <a href="/radio" on:click={closeMenu}>Radio Shows</a>
        </li>
        <li>
            <a href="/contact" on:click={closeMenu}>Contact</a>
          </li>
    </ul>
</div>

<!-- DESKTOP MENU (hidden on mobile) -->
<div class="menu">
    <ul>
        <li><a href="/about">About</a></li>
        <li><a href="/albums">Music</a></li>
        <li><a href="/radio">Radio Shows</a></li>
        <li><a href="/contact">Contact</a></li>
    </ul>
</div>
