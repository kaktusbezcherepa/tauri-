<script>
  let card = "/src/assets/background/coloda.png";

  function handleClick() {
    alert('Нажал на картинку');
  }

  function handleKeyPress(event) {
    if (event.key === 'Enter') {
      handleClick();
    }
  }
</script>

<div class="back"></div>
<button class="image-button" on:click={handleClick} on:keypress={handleKeyPress}>
  <img class="name" src={card} alt="newtaro">
</button>

<style>
.back {
  position: fixed;
  width: 100%;
  height: 100%;
  background: url('/src/assets/background/gameback.jpg') no-repeat center;
  transform: rotate(180deg);
  background-size: cover;
  z-index: -1;
}

.image-button {
  border: none;
  background: none;
  cursor: pointer;
  padding: 0;
  margin-left: 80%;
  margin-top: 15%;
}

.name {
  height: auto;
  width: 350px;
  z-index: 4;
  clip-path: inset(5%);
}
</style>