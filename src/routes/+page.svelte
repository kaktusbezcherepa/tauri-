<script>
  import { onMount, onDestroy } from 'svelte';
  import { goto } from '$app/navigation';
  import { fade } from 'svelte/transition';
  import { window as tauriWindow } from "@tauri-apps/api";

  let isTransitioning = false;
  let showModal = false;
  let volumeValue = 20;
  let audio;
  let videoElement;

  onMount(() => {
    audio = new Audio('/src/assets/music/tilitili.mp3');
    audio.loop = true;
    setVolume(volumeValue);
    playAudio();
    if (videoElement) {
      videoElement.play();
    }
  });

  onDestroy(() => {
    if (audio) {
      audio.pause();
      audio.currentTime = 0;
    }
  });

  function setVolume(value) {
    if (audio) {
      audio.volume = value / 100;
    }
  }

  function playAudio() {
    if (audio) {
      audio.play().catch(error => console.error('Error playing audio:', error));
    }
  }

  $: if (audio && typeof volumeValue === 'number') {
    setVolume(volumeValue);
  }

  async function toGame() {
    isTransitioning = true;
    if (audio) {
      audio.pause();
    }
    await new Promise(resolve => setTimeout(resolve, 300)); 
    goto('/game');
  }

  async function toFate() {
    isTransitioning = true;
    if (audio) {
      audio.pause();
    }
    await new Promise(resolve => setTimeout(resolve, 300))
    goto('/fate_game')
  }

  const closeWin = async () => {
    if (audio) {
      audio.pause();
    }
    const appWindow = await tauriWindow.getCurrent();
    await appWindow.close();
  }

  function openModal() {
    showModal = true;
  }

  function closeModal() {
    showModal = false;
  }

  function handleKeydown(event) {
    if (event.key === 'Escape') {
      closeModal();
    }
  }
</script>

<svelte:window on:keydown={handleKeydown}/>

{#if !isTransitioning}
  <div class="back-container" in:fade={{ duration: 300 }} out:fade={{ duration: 300 }}>
    <video
      bind:this={videoElement}
      class="background-video"
      autoplay
      loop
      muted
      playsinline
    >
    <source src="/mainmenu.mp4" type="video/mp4">
    </video>
    <div class="main-back">
      <nav class="container">
        <button on:click={toGame}>Play PVP</button>
        <button on:click={toFate}>Find your FATE</button>
        <button on:click={openModal}>Settings</button>
        <button on:click={closeWin}>Exit</button>
      </nav>
    </div>
  </div>
{/if}

{#if showModal}
  <div 
    class="modal-backdrop" 
    transition:fade={{ duration: 300 }}
  >
    <div 
      class="modal-content" 
      role="dialog"
      aria-modal="true"
    >
      <button class="close-button" on:click={closeModal} aria-label="Close settings">×</button>
      <h2>Settings</h2>
      <label for="volume">Music Volume:</label>
      <input 
        type="range" 
        id="volume" 
        min="0" 
        max="100" 
        bind:value={volumeValue}
      />
      <p>Current volume: {volumeValue}%</p>
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
    background-size: cover;
  }

  .modal-backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }

  .modal-content {
    background: white;
    padding: 20px;
    border-radius: 5px;
    position: relative;
    font-family: "Indie Flower", cursive;
  }

  .close-button {
    position: absolute;
    top: -20px;
    right: -1px;
    border: none;
    background: none;
    font-size: 50px;
    cursor: pointer;
  }
  

</style>