<script>
    let { children } = $props();
</script>

<div class="article-text">
    <p>
        {@render children()}
    </p>
</div>

<style>
    .article-text {
        margin: 50vh auto;
        width: 50%;
        background-color: #ff99fc;
        color: #004d39;
        border: solid #9c3fe3 3px;
        border-radius: 20px;
        padding: 20px;
        box-shadow: 8px 8px #8aa6df;
    }
</style>
