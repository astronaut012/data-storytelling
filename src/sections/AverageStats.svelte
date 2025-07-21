<script>
  import Scroller from "../lib/Scroller.svelte";
  import { fade, fly } from "svelte/transition";
  import ArticleText from "../lib/ArticleText.svelte";
  import ObservedArticleText from "../lib/ObservedArticleText.svelte";

  import * as Highcharts from "highcharts";
  import "highcharts/modules/exporting";
  import { Chart } from "@highcharts/svelte";

  let fishIsVisible = $state(false);
 // let fish1IsVisible = $state(true);
  const options = {
    threshold: [0.85, 0.95],
  };
  const showfishCallback = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        elem.style.backgroundColor = "#e3ff00";
        fishIsVisible = true;
     //   fish1IsVisible = false;
        setTimeout(expand, 2000);
      } else if (entry.intersectionRatio < 0.9) {
        elem.style.backgroundColor = "#888888";
      }
    });
  };

  const removefishCallback = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        elem.style.backgroundColor = "#e3ff00";
        fishIsVisible = false;
      } else if (entry.intersectionRatio < 0.9) {
        elem.style.backgroundColor = "#888888";
      }
    });
  };

  function expand() {
    document.getElementById("blowfish").style.fontSize = "170px";
  }

  
</script>

<div>
  <Scroller layout="right">
    {#snippet sticky()}
      <div>
        {#if fishIsVisible}
          <p
            in:fly={{ x: 200, duration: 1500 }}
            out:fade
            id="blowfish"
            style="font-size: 90px;"
          >
            &#128033
          </p>
        {/if}
      </div>
      
    {/snippet}

    {#snippet scrolly()}
      <ObservedArticleText callback={removefishCallback} {options}>
        In 2023, an average of <a
          href="https://blackwealthdata.org/explore/education">25%</a
        > of the Black population of each state in the United States had attained
        a bachelor's degree
      </ObservedArticleText>
      <ObservedArticleText callback={showfishCallback} {options}>
        An average of <a href="https://blackwealthdata.org/explore/education"
          >36%</a
        > of the White population of each state in the United States had attained
        a bachelor's degree
      </ObservedArticleText>
    {/snippet}
  </Scroller>
</div>

<style>
</style>
