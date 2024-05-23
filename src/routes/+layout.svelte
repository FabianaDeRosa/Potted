<script>
  import "../app.scss";
  import Header from "./Header.svelte";
  import Footer from "./Footer.svelte";
</script>



<div id="wrapper">

  <Header />

  <main>

    <slot />

  </main>

  <Footer />

</div>



<style lang="scss">

  #wrapper {
    grid-template-rows: auto 1fr auto;
    height: 100vh;
    display: grid;
  }
</style>