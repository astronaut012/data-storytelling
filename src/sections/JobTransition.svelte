<script>
  let show = $state(false);
  function displayMessage() {
    document.getElementById("shark").style.animation = "null";
    show = true;
  }
</script>

<button id="shark" onclick={displayMessage}>&#129416</button>
{#if show}
  <p>Beware! There may be a shark lurking around with secret information</p>
{/if}

<style>
  button {
    /* background-color: rgba(255, 255, 255, 0.717); */
    background-color: rgba(255, 255, 255, 0);
    border: none;
    box-shadow: none;
    margin: 30px auto;
    font-size: 70px;
    text-align: center;
    animation: shake 0.5s;

    /* When the animation is finished, start again */
    animation-iteration-count: infinite;
  }
  p {
    background-color: rgba(255, 255, 255, 0.543);
    border: none;
    box-shadow: none;
    /* color: #007052; */
    margin: 20px auto;
    font-size: 30px;
    text-align: center;
  }

  @keyframes shake {
    0% {
      transform: translate(1px, 1px) rotate(0deg);
    }
    10% {
      transform: translate(-1px, -2px) rotate(-1deg);
    }
    20% {
      transform: translate(-3px, 0px) rotate(1deg);
    }
    30% {
      transform: translate(3px, 2px) rotate(0deg);
    }
    40% {
      transform: translate(1px, -1px) rotate(1deg);
    }
    50% {
      transform: translate(-1px, 2px) rotate(-1deg);
    }
    60% {
      transform: translate(-3px, 1px) rotate(0deg);
    }
    70% {
      transform: translate(3px, 1px) rotate(-1deg);
    }
    80% {
      transform: translate(-1px, -1px) rotate(1deg);
    }
    90% {
      transform: translate(1px, 2px) rotate(0deg);
    }
    100% {
      transform: translate(1px, -2px) rotate(-1deg);
    }
  }
</style>
