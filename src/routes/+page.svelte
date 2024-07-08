<script>
  import { goto } from '$app/navigation';

  let name = "";

  function greet() {
    goto('/greeting?name=' + encodeURIComponent(name));
  }
</script>

<div class="background">
  <div class="container">
  <h1>Welcome to Svelte!</h1>

  <p>Enter a name and click "Greet" to go to the greeting page.</p>

  <form class="row" on:submit|preventDefault={greet}>
    <input id="greet-input" placeholder="Enter a name..." bind:value={name} />
    <button type="submit">Greet</button>
  </form>
  </div>
</div>

<style>
    .background {
    height: 100%;
    width: 100%;
    background: url("../../assets/background/mainmenu.png");
  }
  .container {
    margin: 0;
    padding-top: 10vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
  }
  .row {
    display: flex;
    justify-content: center;
  }

  input,
  button {
    border-radius: 8px;
    border: 1px solid transparent;
    padding: 0.6em 1.2em;
    font-size: 1em;
    font-weight: 500;
    font-family: inherit;
    color: #0f0f0f;
    background-color: #ffffff;
    transition: border-color 0.25s;
    box-shadow: 0 2px 2px rgba(0, 0, 0, 0.2);
  }

  button {
    cursor: pointer;
  }

  button:hover {
    border-color: #396cd8;
  }
  button:active {
    border-color: #396cd8;
    background-color: #e8e8e8;
  }

  input,
  button {
    outline: none;
  }

  #greet-input {
    margin-right: 5px;
  }
</style>