<script>
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
<div class="colodaclass" on:click={handleClick} on:keypress={handleKeyPress} tabindex="0" role="button"></div>


<style>
    
.back {
    position: fixed;
    width: 100%;
    height: 100%;
    background: url('/src/assets/background/scale_1200.png') no-repeat center;
    background-size: cover;
    z-index: -1;
}

.colodaclass {
    position: fixed; 
    left: 85%;
    top: 40%;
    width: 20%;
    height: 20%;
    background: url('/src/assets/background/newtaro.png') no-repeat; 
    background-size: contain; 
    z-index: 0;
    transform: rotate(90deg);
}

</style>