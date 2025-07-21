<script>
  import Scroller from "../lib/Scroller.svelte";
  import { fade, fly } from "svelte/transition";
  import ArticleText from "../lib/ArticleText.svelte";
  import ObservedArticleText from "../lib/ObservedArticleText.svelte";
  let src1 = "popMap.png";
  let src2 = "texasClicked.png";
  let selected = $state(false);
  let texas = $state(false);
  let chartTitle = $state("Percentage of Black population in each state");

  const options = {
    threshold: [0.85, 0.95],
  };

  const displayTexas = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        elem.style.backgroundColor = "#e3ff00";
        selected = true;
        texas = false;
        chartTitle = "Percentage of Black population in each state";
      } else if (entry.intersectionRatio < 0.9) {
        elem.style.backgroundColor = "#888888";
      }
    });
  };

  const removeTexas = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        elem.style.backgroundColor = "#e3ff00";
        selected = false;
      } else if (entry.intersectionRatio < 0.9) {
        elem.style.backgroundColor = "#888888";
      }
    });
  };

  const zoomTexas = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        elem.style.backgroundColor = "#e3ff00";
        texas = true;
        chartTitle = "Texas";
      } else if (entry.intersectionRatio < 0.9) {
        elem.style.backgroundColor = "#888888";
      }
    });
  };
</script>

<div>
  <Scroller layout="left">
    {#snippet sticky()}
      <div>
        <p style="font-size: 30px" class="whiteBg">{chartTitle}</p>
        <div class="map">
          {#if !selected && !texas}
            <img src={src1} alt="map" style="width: 800px; height:350px;" />
          {/if}
          {#if selected && !texas}
            <img src={src2} alt="map" style="width: 800px; height:350px;" />
          {/if}
          {#if texas}
            <img
              src="texasResized.png"
              alt="map"
              style="width: 800px; height:350px;"
              in:fade
            />
          {/if}
        </div>
        <p class="whiteBg">
          Source: <a href="https://blackwealthdata.org/explore/population"
            >Black Wealth Data Center</a
          >
        </p>
      </div>
    {/snippet}

    {#snippet scrolly()}
      <ArticleText>
        The Black population forms <a
          href="https://blackwealthdata.org/explore/education">12%</a
        > of the total population of the United States
      </ArticleText>
      <ObservedArticleText callback={removeTexas} {options}>
        ..which drops to <a href="https://blackwealthdata.org/explore/education"
          >7%</a
        > of Active MD residents
      </ObservedArticleText>
      <ObservedArticleText callback={displayTexas} {options}
        >Let's zoom into the state with the highest Black population</ObservedArticleText
      >
      <div class="stick">
        <ObservedArticleText callback={zoomTexas} {options}
          >Texas - The Black population here has a median total household debt
          of $55,500
        </ObservedArticleText>
      </div>
      <ArticleText>And a median annual income of $57,539</ArticleText>
    {/snippet}
  </Scroller>
</div>

<style>
  .stick {
    position: sticky;
    top: -40%;
  }
</style>
