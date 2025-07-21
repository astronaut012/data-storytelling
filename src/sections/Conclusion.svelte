<script>
  import Scroller from "../lib/Scroller.svelte";
  import { fade, fly } from "svelte/transition";
  import ArticleText from "../lib/ArticleText.svelte";
  import ObservedArticleText from "../lib/ObservedArticleText.svelte";
  import ToTop from "../lib/toTop.svelte";
  import App from "../App.svelte";

  function displayBonus() {
    document.getElementById("bonus").style.display = "block";
    document.getElementById("bonusBtn").style.visibility = "hidden";
    //  ToTop.style.visibility="hidden";
    //document.getElementById('removable').style.visibility="hidden";
    document.getElementById("removable").remove();
    document.getElementById("removable2").remove();
    document.getElementById("addable").style.display = "block";
  }
</script>

<div class="middle">
  <p class="article-text">You made it to the bottom of the sea!</p>
  <div id="removable"><ToTop /></div>
  <p
    class="article-text"
    id="removable2"
    style="text-align: center; margin-top:100px"
  >
    ..or
  </p>
  <p class="shark">&#129416</p>
  <button id="bonusBtn" onclick={displayBonus}>Click for a bonus section</button
  >
  <div id="bonus">
    <p class="article-text">
      The <a href="https://blackwealthdata.org/explore/assets">median assets</a>
      for the Black population in 2022 was 32% of the median assets overall
    </p>
    <p class="article-text">
      The median <a href="https://blackwealthdata.org/explore/assets"
        >education loans</a
      > taken per Black household was $26,000 - higher than the median for most other
      races
    </p>
    <p class="article-text">
      The percentage of the Black population that was <a
        href="https://blackwealthdata.org/explore/assets">unbanked</a
      > in 2023 was over twice that of overall, with over 25% of unbanked people
      saying they did not have enough money to meet the minimum balance requirements.
    </p>
  </div>
  <div id="addable"><ToTop /></div>
</div>

<style>
  .shark {
    background-color: rgba(255, 255, 255, 0);
    border: none;
    box-shadow: none;
    margin: 30px auto;
    font-size: 70px;
    text-align: center;
  }
  #addable {
    display: none;
  }
  #bonus {
    display: none;
    background-color: #004d39;
    border: solid #8aa6df 3px;
    width: 50vh auto;
    padding: 5%;
    margin-right: 15%;
    margin-left: 15%;
    border-radius: 20px;
  }

  .article-text {
    margin: 20px auto;
    width: 30%;
    background-color: #ff99fc;
    color: #004d39;
    border: solid #9c3fe3 3px;
    border-radius: 20px;
    padding: 30px;
    box-shadow: 8px 8px #8aa6df;
  }
  #bonusBtn {
    margin-bottom: 40px;
  }
</style>
