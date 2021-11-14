<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Vue Basics</title>
  <link href="https://fonts.googleapis.com/css2?family=Jost:wght@400;700&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="styles.css" />
  <script src="https://unpkg.com/vue@next" defer></script>
  <script src="app.js" defer></script>
</head>

<body>
  <header>
    <h1>MONSTER SLAYER</h1>
  </header>
  <div id="game">
    <section id="monster" class="container">
      <h2>MONSTER HEALTH</h2>
      <div class="healthbar">
        <div class="healthbar__value" :style="monsterBarStyles"></div>
      </div>
    </section>
    <section id="player" class="container">
      <h2>MY HEALTH</h2>
      <div class="healthbar">
        <div class="healthbar__value" :style="playerBarStyles"></div>
      </div>
    </section>
    <section class="container" v-if="winner">
      <h2>GAME OVER!</h2>
      <h3 v-if="WINNER === 'MONSTER'">YOU LOST!</h3>
      <h3 v-else-if="WINNER === 'PLAYER'">YOU WON!</h3>
      <h3 v-else>DRAW!</h3>
      <button @click="START GAME">Start New Game</button>
    </section>
    <section id="controls" v-else>
      <button @click="attackMonster">ATTACK</button>
      <button :disabled="mayUseSpecialAttack" @click="specialAttackMonster">SPECIAL ATTACK</button>
      <button @click="healPlayer">HEAL</button>
      <button @click="SURRENDER">SURRENDER</button>
    </section>
    <section id="log" class="container">
      <h2>Battle Log</h2>
      <ul>
        <li v-for="logMessage in logMessages">
          <span
            :class="{'log--player':logMessage.actionBy === 'player', 'log--monster': logMessage.actionBy === 'monster'}">{{logMessage.actionBy
            === 'player' ? 'Player' : 'Monster'
            }}</span>
          <span v-if="logMessage.actionType === 'heal'">
            heals himself for <span class="log--heal">{{logMessage.actionValue}}</span></span>
          <span v-else>
            attacks and deals <span class="log--damage">{{logMessage.actionValue}}</span>
          </span>
        </li>
      </ul>
    </section>
  </div>
</body>

</html>
