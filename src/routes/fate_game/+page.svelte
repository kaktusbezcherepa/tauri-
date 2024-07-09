<script>
  
</script>


  <div class="playing-field">
    <div class="player-field-1">
    </div>
    <div class="player-field-2">
      <button class="player-button"></button>
    </div>
  </div>


<style>
.playing-field {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-direction: column;
  background-color: black;
  height: 100vh;
  width: 100%;
  z-index: 1;
  }
.player-field-1,
.player-field-2 {
  height: 20vh;
  width: 100%;
  background-color: white;
  z-index: 2;
}
.player-button {
  height: 30vh;
  width: 10vw;
  background-color: red;
  margin-left: 80%;
  margin-top: -70%;
  z-index: 3;
}

</style>