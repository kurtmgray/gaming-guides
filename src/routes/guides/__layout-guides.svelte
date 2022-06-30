<!-- 
    to change the layout for some routes, put routes in a folder together with this file
    named specifically __layout.reset.svelte
    this wraps every other route IN THIS FOLDER

-->

<script>
    import Title from "$lib/title.svelte";
    import "../../styles/global.css"
</script>

<header>
    <nav>

        <Title title="Gaming Guides"/>
        <div class="links">
            <a href="/">Home</a>
            <a href="/about">About</a>
            <a href="/guides">Guides</a>
        </div>
    </nav>
</header>

<main>
    <slot></slot>
    <!-- use slot to render the content of the main page -->
</main>

<footer>
    <p>Copyright 2022 KMG Design</p>
</footer>

<style>
  header {
    text-align: center;
    background: rgba(0,0,0,0.1)
  }
  main {
    max-width: 960px;
    margin: 20px auto;
  }
  footer {
    text-align: center;
  }
  nav {
    display: flex;
    align-items: center;
    max-width: 960px;
    margin: 0 auto;
  }
  .links {
    margin-left: auto;
  }
  a {
    margin-left: 10px;
  }
  </style>