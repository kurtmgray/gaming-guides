<!-- 
    __ before the component name tells sveltekit its a layout component 
    this wraps every other route 

-->

<script>
    import Title from "../lib/title.svelte";
    import "../styles/global.css"
</script>

<header>
    <Title title="Gaming Guides"/>

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
      display: flex;
      justify-content: center;
    }
    main {
      max-width: 960px;
      margin: 20px auto;
    }
    footer {
      text-align: center;
    }
  </style>