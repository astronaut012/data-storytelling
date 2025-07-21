<script>
  import FadeBottom from "./FadeBottom.svelte";
  import FadeTop from "./FadeTop.svelte";

  let { title } = $props();
</script>

<FadeTop/>
<div class="title-card">
  <h1>{title}</h1>
</div>
<FadeBottom />

<style>
  .title-card {
    background-color: #007052;
    height: 150%;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 2rem;
    box-sizing: border-box;
    font-family: "Inter", sans-serif;
  }

  h1 {
    font-size: 2.2rem;
    margin: 0;
    color: #e3ff00;
    text-shadow: 1px 1px 0 #007052;
  }

  @media (max-width: 600px) {
    h1 {
      font-size: 2rem;
    }
  }
</style>
