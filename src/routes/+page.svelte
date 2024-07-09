<script>
  // import { goto } from '$app/navigation';

  // let name = "";

  // function greet() {
  //   goto('/greeting?name=' + encodeURIComponent(name));
  // }
</script>

  <div class="back-container">
    <div class="main-back">
    <div class="container">
      <button>Play</button>
      <button>Settings</button>
      <button>Exit</button>
    </div>
  </div>
</div>

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
}

@media(max-width: 400px) {
  button {
    width: 60px;
  }
}

.main-back {
  width: 100vw;
  height: 100vh;
  background: url('../assets/background/giphy.gif') no-repeat center;
  background-size: cover;
}

</style>