<script>
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
  import ObservedArticleText from "../lib/ObservedArticleText.svelte";

  const options = {
    threshold: [0.85, 0.95],
  };
  const simpleCallback = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        elem.style.opacity="1";

      } else if (entry.intersectionRatio < 0.9) {
        elem.style.opacity="0.5";
      }
    });
  };
</script>

<div>
  <Scroller layout="left">
    {#snippet sticky()}
      <div>
        <p style="font-size: 80px">&#128031</p>
      </div>
    {/snippet}

    {#snippet scrolly()}
      <ObservedArticleText callback={simpleCallback} {options}>Hi!</ObservedArticleText>
      <ObservedArticleText callback={simpleCallback} {options}
        >The other day, I found an interesting story that I thought I'd share.
      </ObservedArticleText>
      <ObservedArticleText callback={simpleCallback} {options}>So wear your diving suits and join in!</ObservedArticleText>
    {/snippet}
  </Scroller>
</div>
