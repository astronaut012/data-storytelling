<script>
  import Scroller from "../lib/Scroller.svelte";
  import { fade, fly } from "svelte/transition";
  import ArticleText from "../lib/ArticleText.svelte";
  import ObservedArticleText from "../lib/ObservedArticleText.svelte";
  import ToTop from "../lib/toTop.svelte";
  import App from "../App.svelte";


  function displayBonus() {
    document.getElementById("bonus").style.visibility="visible";
  }
  </script>

  <div>
    <p class="article-text">You made it to the end of the adventure</p>
    <ToTop />
    <ArticleText>OR..</ArticleText>
    <button onclick={displayBonus}>Click for a bonus section!</button>
    <div id="bonus">
        <ArticleText>This is the bonus!!</ArticleText>
    </div>
  </div>

  <style>
    #bonus {
        visibility: hidden;
    }

        .article-text {
        margin:auto;
        width: 50%;
        background-color: #ff99fc;
        color: #004d39;
        border: solid #9c3fe3 3px;
        border-radius: 20px;
        padding: 30px;
        box-shadow: 8px 8px #8aa6df;
    }
    </style>