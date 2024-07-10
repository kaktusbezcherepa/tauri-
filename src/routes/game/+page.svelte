<script>
  import { onMount } from 'svelte';

  let card = "/src/assets/background/newcoloda2.jpg";
  let cardSlots = [null, null, null];
  let availableCards = [];
  let showedCards = 0;
  const TOTAL_CARDS = 22;

  onMount(() => {
    availableCards = Array.from({length: TOTAL_CARDS}, (_, i) => `/src/assets/cards/card${i + 1}.jpg`);
  });

  function getRandomCard() {
    if (availableCards.length === 0) return null;
    const randomIndex = Math.floor(Math.random() * availableCards.length);
    return availableCards.splice(randomIndex, 1)[0];
  }

  function handleClick() {
    const emptySlotIndex = cardSlots.findIndex(slot => slot === null);
    if (emptySlotIndex !== -1) {
      const randomCard = getRandomCard();
      if (randomCard) {
        cardSlots[emptySlotIndex] = randomCard;
        cardSlots = [...cardSlots];
        showedCards += 1;
      } else {
        alert('Карты закончились');
      }
    } else {
      alert('Слотов больше нет');
    }
  }

  function handleKeyPress(event) {
    if (event.key === 'Enter') {
      handleClick();
    }
  }

  function reset() {
    cardSlots = [null, null, null];
    availableCards = Array.from({length: TOTAL_CARDS}, (_, i) => `/src/assets/cards/card${i + 1}.jpg`);
    showedCards = 0;
  }
</script>

<div class="back">
  <div class="card-slots">
    {#each cardSlots as slot, i}
      <div class="card-slot">
        {#if slot}
          <img src={slot} alt="card" class="card-image"/>
        {/if}
      </div>
    {/each}
  </div>
</div>

<button class="image-button" on:click={handleClick} on:keypress={handleKeyPress}>
  <img class="name" src={card} alt="newtaro">
</button>

{#if showedCards === 3}
  <button class="reset-button" on:click={reset}>Reset</button>
{/if}

<style>
  .back {
    display: flex;
    position: fixed;
    width: 100%;
    height: 100%;
    background: url('/src/assets/background/gameback.jpg') no-repeat center;
    background-size: cover;
    z-index: -1;
  }

  .card-slots {
    position: absolute;
    bottom: 15%;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 30px;
  }

  .card-slot {
    width: 240px;
    height: 360px;
    background-color: rgba(204, 204, 204, 0.7);
    border-radius: 10px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
  }

  .card-image {
    max-width: 100%;
    max-height: 100%;
    object-fit: contain;
  }

  .image-button {
    border: none;
    background: none;
    cursor: pointer;
    padding: 0;
    position: fixed;
    right: 20px;
    bottom: 20px;
  }

  .name {
    height: 150px;
    width: auto;
    z-index: 4;
    clip-path: inset(5%);
    transform: rotate(90deg);
  }
  .reset-button {
   position: absolute;
   left: 50%;
   top: 80%;
  }
</style>