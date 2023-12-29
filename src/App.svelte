
<script>
  let playerChoice;
  let computerChoice;
  let computerImage;
  let result;
  
  const choices = {
  'Rock': 'piedra.jpg',
  'Paper': 'papel.jpg',
  'Scissors': 'tijera.jpg'
  };
  
  function chooseRock() {
  playerChoice = 'Rock';
  playGame();
  }
  
  function choosePaper() {
  playerChoice = 'Paper';
  playGame();
  }
  
  function chooseScissors() {
  playerChoice = 'Scissors';
  playGame();
  }
  
  function playGame() {
  computerChoice = Object.keys(choices)[Math.floor(Math.random() * 3)];
  computerImage = choices[computerChoice];
  
  if (playerChoice === computerChoice) {
  result = 'It\'s a tie!';
  } else if ((playerChoice === 'Rock' && computerChoice === 'Scissors') ||
            (playerChoice === 'Paper' && computerChoice === 'Rock') ||
            (playerChoice === 'Scissors' && computerChoice === 'Paper')) {
  result = 'You win!';
  } else {
  result = 'Computer wins!';
  }
  }
  </script>
  
  <button on:click={chooseRock}>Rock</button>
  <button on:click={choosePaper}>Paper</button>
  <button on:click={chooseScissors}>Scissors</button>
  
  <p>{result ? result : ''}</p>
  
 
  <div class="image-container">
    <div class="choice">
      {#if playerChoice}
        <p>The user chose:</p>
        <img src="{choices[playerChoice]}" alt="User's choice">
      {:else}
        <p>No choice made yet.</p>
      {/if}
      </div>
  
    <div class="choice">
  {#if computerImage}
    <p>The computer chose:</p>
    <img src="{computerImage}" alt="Computer's choice">
  {:else}
    <p>Waiting for the user to make a choice...</p>
  {/if}
  </div>
  
  
  </div>
 