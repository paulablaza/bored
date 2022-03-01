<script>
  import "bulma";
  import "animate.css";

  let activity = "Click the button!";

  let button;
  let buttonText = 'Do Something!'

  

  const generateActivity = async () => {
    button.disabled = true
    buttonText = 'Loading'

    const data = await fetch("https://www.boredapi.com/api/activity/");
    const result = await data.json();
    activity = result.activity;

    button.disabled = false
    buttonText = 'Do Something!'
  };
</script>

<div class="container">
  <h1 class="title m-1 has-text-centered animate__animated animate__fadeInDown">
    I am bored
  </h1>
  <h2
    class="is-bold is-size-4 mt-1 mb-6 has-text-centered animate__animated animate__fadeInUp animate__delay-1s"
  >
    what should i do?
  </h2>

  <div class="generator">
    <h3
      class="mx-2 is-size-4 isbold has-text-centered animate__animated animate__fadeIn animate__zoomIn animate__delay-2s"
    >
      {activity}
    </h3>

    <button
      on:click={generateActivity}
      class="button is-black mt-4 animate__animated animate__fadeInUp animate__delay-2s"
      bind:this={button}
    >
      {buttonText}
    </button>
  </div>
</div>


<style lang="css">
  :global(body) {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .container {
    display: flex;
    flex-direction: column;
  }

  .generator {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>
