<script>
  import { goto } from '$app/navigation';
  import { fade } from 'svelte/transition';
  import { window as tauriWindow } from "@tauri-apps/api";

  let isTransitioning = false;

  async function toGame() {
    isTransitioning = true;
    await new Promise(resolve => setTimeout(resolve, 300)); 
    goto('/game');
  }

  async function toFate() {
    isTransitioning = true;
    await new Promise(resolve => setTimeout(resolve, 300))
    goto('/fate_game')
  }

  const closeWin = async () => {
  const appWindow = tauriWindow.getCurrent();
  await appWindow.close();
}
</script>

{#if !isTransitioning}
  <div class="back-container" in:fade={{ duration: 300 }} out:fade={{ duration: 300 }}>
    <div class="main-back">
      <div class="container">
        <button on:click={toGame}>Play PVP</button>
        <button on:click={toFate}>Find your FATE</button>
        <button>Settings</button>
        <button on:click={closeWin}>Exit</button>
      </div>
    </div>
  </div>
{/if}


<style>

.container {
  position: relative;
  display: flex;
  flex-direction: column;
  padding-top: 20vh;
  justify-content: center;
  align-items: center;
  gap: 5vh;
}

button {
  font-size: 60px;
  color: black;
  font-family: "Indie Flower", cursive;
  background-color: transparent;
  border: none;
  cursor: pointer;
}

@media(max-width: 400px) {
  button {
    width: 60px;
  }
}

.main-back {
  width: 100vw;
  height: 100vh;
  background: url('../assets/background/mainmenu.gif') no-repeat center;
  background-size: cover;
}

</style>