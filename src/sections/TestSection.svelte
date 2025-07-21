<script>
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
</script>

<div>
  <Scroller layout="left">
    {#snippet sticky()}
      <div>
        <p style="font-size: 80px">&#128031</p>
      </div>
    {/snippet}

    {#snippet scrolly()}
      <ArticleText>Hi!</ArticleText>
      <ArticleText
        >The other day, I found an interesting story that I thought I'd share.
      </ArticleText>
      <ArticleText>So wear your diving suits and join in!</ArticleText>
    {/snippet}
  </Scroller>
</div>
