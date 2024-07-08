<script>
  // import { goto } from '$app/navigation';

  // let name = "";

  // function greet() {
  //   goto('/greeting?name=' + encodeURIComponent(name));
  // }
</script>

  <div class="back-container">
    <video src="../assets/background/mainmenu.mp4" autoplay muted loop></video>
    <div class="container">
      <button>Play</button>
      <button>Settings</button>
      <button>Exit</button>
    </div>
  </div>

<style>
/* .back-container {
  position: relative;
  height: 100vh;
  z-index: 1;
}

.back-container::before {
  content: "";
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  /* background: url("../assets/background/") center center no-repeat;
  background-size: cover; */
  /* filter: blur(3px) contrast(120%);
} */ 

.container {
  position: relative;
  display: flex;
  flex-direction: column;
  padding-top: 45vh;
  padding-left: 5vw;
  justify-content: center;
  align-items: flex-start;
  gap: 5vh;
}

button {
  width: 7vw;
  height: 5vh;
  border: 2px solid black;
  border-radius: 8px;
  background-color: transparent;
  font-size: 20px;
  color: white;
  background-color: black;
}

@media(max-width: 400px) {
  button {
    width: 60px;
  }
}
</style>