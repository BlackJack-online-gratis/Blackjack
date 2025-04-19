<!DOCTYPE html>
<html lang="it">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Blackjack Online Gratis - Gioca Subito Senza Registrazione</title>
<meta name="description" content="Gioca a Blackjack online gratis direttamente dal tuo browser. Nessuna registrazione, nessun download: solo puro divertimento con le regole ufficiali del Blackjack!" />
<meta name="google-adsense-account" content="ca-pub-7565515791909001">
<style>
  @import url('https://fonts.googleapis.com/css2?family=Nunito:wght@400;700&display=swap');

  /* --- Basic Theme Variables (Light/Green Theme Default - MODIFICATO) --- */
  :root {
    /* Colori per il tema verde (chiaro) */
    --bg-color: #1e5631; /* Verde tavolo da gioco */
    --text-color: #ffffff; /* Testo bianco per contrasto sul verde */
    --card-bg: white;
    --card-text-black: black;
    --card-text-red: red;
    --button-bg: #e0e0e0; /* Grigio chiaro per bottoni */
    --button-text: #333333; /* Testo scuro su bottoni chiari */
    --button-hover-bg: #d0d0d0;
    --button-disabled-opacity: 0.5;
    --highlight-color: #ffeb3b; /* Giallo per evidenziare */
    --border-color: rgba(255, 255, 255, 0.2); /* Bordi chiari sul verde */
    --panel-bg: rgba(0, 0, 0, 0.3); /* Pannelli scuri semi-trasparenti */
    --accent-color: #4fc3f7; /* Blu chiaro accento */
    --dealer-hidden-card-bg: #8b4513; /* Dorso carta marrone/legno */
    --font-main: 'Nunito', sans-serif; /* Font Applicato */

    /* Nuove variabili per risultato */
    --result-bg-color: rgba(0, 0, 0, 0.75);
    --result-text-color: #ffffff;
    --result-win-glow: rgba(76, 175, 80, 0.8); /* Verde per vittoria */
    --result-lose-glow: rgba(244, 67, 54, 0.8); /* Rosso per sconfitta */
    --result-push-glow: rgba(255, 152, 0, 0.8); /* Arancio per pareggio */
  }

  /* --- Dark Theme (MODIFICATO) --- */
  body[data-theme="dark"] {
    --bg-color: #1f1f1f; /* Grigio scuro per tema scuro */
    --text-color: #dcdcdc; /* Testo grigio chiaro */
    --card-bg: #383838;
    --card-text-black: #dcdcdc;
    --card-text-red: #ff9a8f;
    --button-bg: #4a4a4a; /* Bottoni grigio medio */
    --button-text: #dcdcdc; /* Testo chiaro su bottoni scuri */
    --button-hover-bg: #5a5a5a;
    --highlight-color: #ffd700; /* Oro */
    --border-color: rgba(255, 255, 255, 0.15); /* Bordi più tenui */
    --panel-bg: rgba(255, 255, 255, 0.1); /* Pannelli chiari semi-trasparenti */
    --accent-color: #4fc3f7; /* Stesso blu accento */
    --dealer-hidden-card-bg: #252525; /* Dorso carta scuro */

    /* Aggiunto gradiente radiale per profondità nel tema scuro */
    background-image: radial-gradient(circle at top center, hsl(0, 0%, 18%) 0%, var(--bg-color) 70%);
    background-attachment: fixed; /* Impedisce al gradiente di scrollare */
  }

  /* --- General Styles (MODIFICATO) --- */
  body {
    font-family: var(--font-main);
    text-align: center;
    background-color: var(--bg-color);
    color: var(--text-color); /* Usa il testo definito nel tema */
    padding-top: 15px;
    margin: 0;
    transition: background-color 0.3s, color 0.3s, background-image 0.3s;
    background-image: none; /* Rimuove il gradiente per il tema chiaro/verde */
    min-height: 100vh;
  }

  .game-container {
    max-width: 1100px;
    margin: 0 auto;
    padding: 20px;
    position: relative; /* Necessario per il posizionamento di #result */
    overflow-x: hidden; /* Previene scroll orizzontale se #result è troppo largo */
  }

  /* --- Cards --- (Stili quasi invariati, usano le variabili CSS) */
   .cards {
    margin: 15px auto;
    display: flex;
    justify-content: center;
    min-height: 115px; /* Adjusted */
    gap: 12px; /* More gap */
    flex-wrap: wrap;
    perspective: 1200px; /* Increased perspective */
  }

  .card {
    display: inline-block;
    border: 1px solid var(--border-color);
    border-radius: 8px; /* More rounded */
    background: var(--card-bg);
    width: 65px; /* Slightly wider */
    height: 95px; /* Slightly taller */
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4); /* Softer shadow */
    margin: 3px;
    position: relative;
    transform-style: preserve-3d;
    transition: transform 0.7s cubic-bezier(0.4, 0.0, 0.2, 1); /* Smoother transition */
    transform: rotateY(180deg);
  }

  .card-inner {
      position: relative;
      width: 100%;
      height: 100%;
      text-align: center;
      transform-style: preserve-3d;
  }

  .card-face {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    border-radius: 8px; /* Match parent */
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 5px;
    box-sizing: border-box;
  }

  .card-front {
    background-color: var(--card-bg);
    /* Subtle gradient for texture */
    background-image: linear-gradient(to bottom, rgba(255,255,255,0.05) 0%, rgba(0,0,0,0.05) 100%);
    color: var(--card-text-black);
    font-size: 22px; /* Larger rank */
    font-weight: bold;
    transform: rotateY(0deg);
    border: 1px solid rgba(0,0,0,0.1); /* Inner border effect */
  }

  .card-back {
    background-color: var(--dealer-hidden-card-bg);
    color: var(--text-color);
    transform: rotateY(180deg);
    background-image: linear-gradient(45deg, rgba(255,255,255,0.1) 25%, transparent 25%),
                      linear-gradient(-45deg, rgba(255,255,255,0.1) 25%, transparent 25%),
                      linear-gradient(45deg, transparent 75%, rgba(255,255,255,0.1) 75%),
                      linear-gradient(-45deg, transparent 75%, rgba(255,255,255,0.1) 75%);
    background-size: 18px 18px; /* Adjusted pattern size */
  }

  .card.flipped {
      transform: rotateY(0deg);
  }

  .card-front.red { color: var(--card-text-red); }
  .card-front.black { color: var(--card-text-black); }

  .card .suit {
    font-size: 16px; /* Larger suit */
    font-weight: normal;
    line-height: 1.1;
  }


  /* --- Buttons & Betting (Usano variabili CSS) --- */
  #buttons, #betting-buttons, #utility-buttons {
    margin-top: 20px;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
  }

  button, .toggle-switch label {
    padding: 12px 20px;
    font-size: 15px;
    font-weight: bold;
    margin: 5px;
    cursor: pointer;
    border: none;
    border-radius: 8px;
    background-color: var(--button-bg);
    color: var(--button-text);
    transition: background-color 0.2s ease, opacity 0.3s ease, transform 0.15s ease, box-shadow 0.2s ease;
    user-select: none;
    -webkit-user-select: none;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
    letter-spacing: 0.5px;
  }
  button:hover:not(:disabled) {
    background-color: var(--button-hover-bg);
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
  }
  button:active:not(:disabled) {
      transform: translateY(0px);
      box-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
  }
  button:disabled {
    opacity: var(--button-disabled-opacity);
    cursor: not-allowed;
    box-shadow: none;
    transform: none;
  }
  button.hint-highlight {
      box-shadow: 0 0 12px 4px var(--highlight-color);
      border: 1px solid var(--highlight-color);
      transform: translateY(-1px); /* Slight lift for hint */
  }

  /* --- Betting Area with Chips (Usano variabili CSS) --- */
   #betting-area {
    margin-bottom: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 15px;
  }

  #proposed-bet-display {
    font-size: 1.4em;
    font-weight: bold;
    color: var(--highlight-color);
    min-height: 1.5em;
    background-color: var(--panel-bg); /* Usa sfondo pannello */
    padding: 5px 15px;
    border-radius: 5px;
  }

  #clickable-chips {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 10px;
      margin-bottom: 15px;
  }

  .chip-button {
      width: 55px;
      height: 55px;
      cursor: pointer;
      border-radius: 50%;
      border: 3px solid rgba(255, 255, 255, 0.4);
      transition: transform 0.1s ease-out, opacity 0.3s ease, box-shadow 0.2s ease, border-color 0.2s ease;
      box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.5), 0 1px 2px rgba(0,0,0,0.2);
      user-select: none;
      -webkit-user-select: none;
      background-color: transparent;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
  }
   .chip-button img { display: block; width: 100%; height: 100%; }

  .chip-button:hover:not([disabled]) {
      transform: scale(1.03);
      border-color: white;
      box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.5), 0 0 10px 2px var(--highlight-color);
  }

  .chip-button:active:not([disabled]) {
      transform: scale(0.97);
      box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.6);
  }

  .chip-button[disabled] {
      opacity: 0.4;
      cursor: not-allowed;
      transform: none;
      border-color: rgba(255, 255, 255, 0.4);
      box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.5);
  }

  #bet-chips {
      min-height: 30px;
      margin-top: 10px;
      font-size: 1.2em;
      font-weight: bold;
      color: var(--text-color);
      background-color: var(--panel-bg); /* Usa sfondo pannello */
      padding: 3px 10px;
      border-radius: 5px;
  }


  /* --- Player/Dealer Info (Usano variabili CSS) --- */
  #player-info, #dealer-info {
    margin-bottom: 20px;
  }
  h2 { margin-bottom: 10px; font-size: 1.5em; text-transform: uppercase; letter-spacing: 1px;}

  /* --- Multiple Hands (Usano variabili CSS) --- */
  #player-hands-container {
      display: flex;
      justify-content: center;
      gap: 20px;
      flex-wrap: wrap;
      margin-top: 15px;
  }
  .player-hand {
      border: 2px solid var(--border-color);
      border-radius: 12px;
      padding: 15px;
      min-width: 180px;
      background-color: var(--panel-bg);
      position: relative;
      transition: border-color 0.3s, box-shadow 0.3s;
      box-shadow: 0 2px 5px rgba(0,0,0,0.3);
  }
  .player-hand h3 {
      margin-top: 0;
      margin-bottom: 8px;
      font-size: 1.1em;
      color: var(--accent-color);
      text-align: center;
  }
  .player-hand .cards { min-height: 100px; margin-bottom: 10px; }
  .player-score { font-size: 1em; margin-bottom: 5px; margin-top: 8px; font-weight: bold; }
  .hand-status { font-size: 1em; font-weight: bold; color: var(--highlight-color); min-height: 1.2em; text-align: center; }
  .player-hand.current-hand {
      border-color: var(--highlight-color);
      box-shadow: 0 0 15px rgba(255, 223, 0, 0.6);
  }


  /* --- Result Message (MODIFICATO PESANTEMENTE) --- */
  #result {
    /* Nascondi di default */
    opacity: 0;
    visibility: hidden;
    transform: translate(-50%, -50%) scale(0.8); /* Parte da piccolo */
    transition: opacity 0.4s ease-out, visibility 0.4s ease-out, transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275); /* Transizione fluida */

    /* Posizionamento e Stile */
    position: fixed; /* Sovrapposto */
    top: 50%;
    left: 50%;
    /* transform: translate(-50%, -50%); è gestito sopra con scale */
    z-index: 100; /* Sopra tutto il resto */
    background-color: var(--result-bg-color);
    color: var(--result-text-color);
    padding: 25px 40px;
    border-radius: 15px;
    font-size: 2.8em; /* Molto più grande */
    font-weight: bold;
    text-align: center;
    white-space: pre-line;
    min-width: 300px; /* Larghezza minima */
    max-width: 80%; /* Larghezza massima */
    box-shadow: 0 0 20px 5px rgba(0, 0, 0, 0.5); /* Ombra più marcata */
  }

  #result.result-show {
    /* Mostra con animazione */
    opacity: 1;
    visibility: visible;
    transform: translate(-50%, -50%) scale(1); /* Scala alla dimensione normale */
    /* L'animazione @keyframes può essere aggiunta se si vuole un effetto più complesso */
  }

  /* Classi opzionali per glow colorato */
   #result.win { box-shadow: 0 0 25px 10px var(--result-win-glow); }
   #result.lose { box-shadow: 0 0 25px 10px var(--result-lose-glow); }
   #result.push { box-shadow: 0 0 25px 10px var(--result-push-glow); }


  /* --- Trainer, Stats, Utilities (Usano variabili CSS) --- */
   #trainer-controls, #session-stats, #utility-controls {
     background-color: var(--panel-bg);
     border: 1px solid var(--border-color);
     border-radius: 10px;
     padding: 15px;
     margin: 20px auto;
     max-width: 450px;
     font-size: 1em;
     box-shadow: 0 3px 6px rgba(0,0,0,0.3);
   }
   #trainer-controls h3, #session-stats h3, #utility-controls h3 {
      margin-top: 0;
      margin-bottom: 15px;
      color: var(--accent-color);
      font-size: 1.2em;
      text-align: center;
      border-bottom: 1px solid var(--border-color);
      padding-bottom: 8px;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
   }
   #trainer-controls div, #session-stats div, #utility-controls div:not(:has(button#toggle-trainer-button)) {
      margin-bottom: 8px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 3px 0;
   }
   #utility-controls div:has(button#toggle-trainer-button) {
      margin-top: 15px;
      text-align: center;
   }
   #trainer-controls label, #utility-controls label {
      margin-right: 15px;
      font-weight: bold;
   }
   #trainer-controls span:last-child, #session-stats span:last-child {
      font-weight: bold;
      color: var(--highlight-color);
   }
   #session-stats #stats-win-rate {
      color: var(--accent-color);
   }

   /* --- Stile Bottone Info Hi-Lo --- */
   #hilo-info-button {
       padding: 0;
       margin: 0 0 0 10px;
       width: 24px;
       height: 24px;
       font-size: 15px;
       line-height: 22px;
       font-weight: bold;
       border-radius: 50%;
       background-color: var(--button-bg);
       color: var(--button-text);
       border: 1px solid var(--border-color);
       box-shadow: none;
       cursor: help;
       vertical-align: middle;
       transition: background-color 0.2s, border-color 0.2s;
       flex-shrink: 0;
   }
   #hilo-info-button:hover {
       background-color: var(--button-hover-bg);
       border-color: var(--accent-color);
       transform: none;
       box-shadow: none;
   }

   /* --- Toggle Switch (Usano variabili CSS) --- */
   .toggle-switch {
     position: relative;
     display: inline-block;
     width: 50px; height: 24px;
     vertical-align: middle;
   }
   .toggle-switch input { opacity: 0; width: 0; height: 0; }
   .slider { position: absolute; cursor: pointer; top: 0; left: 0; right: 0; bottom: 0; background-color: #555; transition: .4s; border-radius: 24px; }
   .slider:before { position: absolute; content: ""; height: 18px; width: 18px; left: 3px; bottom: 3px; background-color: white; transition: .4s; border-radius: 50%; }
   input:checked + .slider { background-color: var(--accent-color); }
   input:focus + .slider { box-shadow: 0 0 2px var(--accent-color); }
   input:checked + .slider:before { transform: translateX(26px); }


  /* --- Visually Hidden --- */
  .visually-hidden { position: absolute; width: 1px; height: 1px; margin: -1px; padding: 0; overflow: hidden; clip: rect(0, 0, 0, 0); border: 0; }

  /* --- Basic Responsiveness (Adattato per #result) --- */
  @media (max-width: 768px) {
      .card { width: 60px; height: 90px; border-radius: 6px;}
      .card-front { font-size: 20px; }
      .card .suit { font-size: 14px; }
      button, .toggle-switch label { font-size: 14px; padding: 10px 15px;}
      #hilo-info-button { width: 22px; height: 22px; font-size: 14px; line-height: 20px; }
      .player-hand { min-width: 160px; padding: 12px; border-radius: 10px;}
      h1 { font-size: 2em; }
      #trainer-controls, #session-stats, #utility-controls { max-width: 90%; padding: 12px; }
      .chip-button { width: 50px; height: 50px; border-width: 2px; }
      #result { font-size: 2.2em; padding: 20px 30px; } /* Adatta risultato */
  }

   @media (max-width: 480px) {
      body { padding-top: 10px; }
      .game-container { padding: 10px; }
      h1 { font-size: 1.6em; }
      .cards { min-height: 100px; gap: 8px;}
      .card { width: 50px; height: 75px; border-radius: 4px; margin: 2px;}
      .card-front { font-size: 16px; }
      .card .suit { font-size: 12px; }
      #buttons, #betting-buttons, #utility-buttons { margin-top: 15px; gap: 5px;}
      button, .toggle-switch label { font-size: 12px; padding: 8px 10px; margin: 3px;}
      #hilo-info-button { width: 20px; height: 20px; font-size: 12px; line-height: 18px; margin-left: 5px;}
      .player-hand { min-width: 130px; padding: 8px; gap: 8px; border-radius: 8px;}
      .player-hand .cards { min-height: 80px; }
      #player-hands-container { gap: 10px; }
      #result { font-size: 1.6em; padding: 15px 20px; min-width: 250px;} /* Adatta risultato */
      #trainer-controls, #session-stats, #utility-controls { padding: 10px; margin: 15px auto; font-size: 0.9em;}
      #trainer-controls h3 { font-size: 1.1em; }
      #trainer-controls div, #session-stats div, #utility-controls div:not(:has(button#toggle-trainer-button)) { flex-direction: row; align-items: center; }
      .chip-button { width: 45px; height: 45px; gap: 5px; border-width: 2px;}
      #proposed-bet-display { font-size: 1.2em; padding: 4px 10px; }
   }
</style>
</head>
<body>
<div class="game-container">
    <h1>Blackjack Trainer</h1>

    <div id="utility-controls">
        <h3>Utilità</h3>
        <div>
            <label for="theme-toggle">Tema Scuro</label>
            <label class="toggle-switch">
                <input type="checkbox" id="theme-toggle">
                <span class="slider"></span>
            </label>
        </div>
        <div>
             <label for="training-mode-toggle">Modalità Allenamento Conteggio</label>
             <label class="toggle-switch">
                 <input type="checkbox" id="training-mode-toggle">
                 <span class="slider"></span>
             </label>
        </div>
         <div>
             <label for="show-hints-toggle">Mostra Suggerimenti (Console)</label>
             <label class="toggle-switch">
                 <input type="checkbox" id="show-hints-toggle">
                 <span class="slider"></span>
             </label>
         </div>
         <div> <button id="toggle-trainer-button" onclick="toggleTrainer()">Mostra Contatore</button>
         </div>
    </div>

    <div id="trainer-controls" style="display: none;">
     <h3>
         Contatore Carte (Hi-Lo)
         <button id="hilo-info-button" onclick="showHiLoInfo()" aria-label="Informazioni sul conteggio Hi-Lo" title="Cos'è il conteggio Hi-Lo?">?</button>
     </h3>
     <div><span>Conteggio Corrente (Running Count):</span> <span id="running-count">0</span></div>
     <div><span>Mazzi Rimanenti (stimati):</span> <span id="decks-remaining">0.0</span></div>
     <div><span>Conteggio Reale (True Count):</span> <span id="true-count">0.0</span></div>
    </div>

    <div id="session-stats">
        <h3>Statistiche Sessione</h3>
        <div><span>Mani Giocate:</span> <span id="stats-hands">0</span></div>
        <div><span>Vittorie:</span> <span id="stats-wins">0</span></div>
        <div><span>Sconfitte:</span> <span id="stats-losses">0</span></div>
        <div><span>Pareggi:</span> <span id="stats-pushes">0</span></div>
        <div><span>Blackjack Vinti:</span> <span id="stats-bjs">0</span></div>
        <div><span>Win Rate (V/V+S):</span> <span id="stats-win-rate">N/A</span></div>
        <button id="reset-stats-button" onclick="resetStats()" style="margin-top: 10px; width:100%;">Azzera Statistiche</button>
    </div>


    <div id="player-info">
     <h2>Giocatore</h2>
     <p id="player-balance">Saldo: $1000</p>
     <div id="bet-chips">Puntata Mano: $0</div>
     <div id="player-hands-container">
         </div>
    </div>

    <div id="dealer-info">
     <h2>Banco</h2>
     <div id="dealer-cards" class="cards" aria-label="Carte del banco"></div>
     <p id="dealer-score">Punteggio: ???</p>
    </div>

    <div id="betting-area">
        <h3>Piazza la tua Puntata</h3>
        <div id="proposed-bet-display">Puntata: $0</div>

        <div id="clickable-chips">
           <img src="data:image/svg+xml;charset=utf-8,%3Csvg width='50' height='50' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='50' cy='50' r='48' fill='%23FFFFFF' stroke='%23000000' stroke-width='2'/%3E%3Ctext x='50' y='55' font-family='sans-serif' font-size='40' font-weight='bold' fill='%23000000' text-anchor='middle' dominant-baseline='middle'%3E10%3C/text%3E%3C/svg%3E" alt="Fiche da $10" class="chip-button" data-value="10" width="55" height="55" draggable="false">
            <img src="data:image/svg+xml;charset=utf-8,%3Csvg width='50' height='50' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='50' cy='50' r='48' fill='%23888888' stroke='%23000000' stroke-width='2'/%3E%3Ctext x='50' y='55' font-family='sans-serif' font-size='40' font-weight='bold' fill='%23FFFFFF' text-anchor='middle' dominant-baseline='middle'%3E20%3C/text%3E%3C/svg%3E" alt="Fiche da $20" class="chip-button" data-value="20" width="55" height="55" draggable="false">
            <img src="data:image/svg+xml;charset=utf-8,%3Csvg width='50' height='50' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='50' cy='50' r='48' fill='%23FF0000' stroke='%23000000' stroke-width='2'/%3E%3Ctext x='50' y='55' font-family='sans-serif' font-size='40' font-weight='bold' fill='%23FFFFFF' text-anchor='middle' dominant-baseline='middle'%3E50%3C/text%3E%3C/svg%3E" alt="Fiche da $50" class="chip-button" data-value="50" width="55" height="55" draggable="false">
            <img src="data:image/svg+xml;charset=utf-8,%3Csvg width='50' height='50' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='50' cy='50' r='48' fill='%23000000' stroke='%23FFFFFF' stroke-width='2'/%3E%3Ctext x='50' y='55' font-family='sans-serif' font-size='35' font-weight='bold' fill='%23FFFFFF' text-anchor='middle' dominant-baseline='middle'%3E100%3C/text%3E%3C/svg%3E" alt="Fiche da $100" class="chip-button" data-value="100" width="55" height="55" draggable="false">
            <img src="data:image/svg+xml;charset=utf-8,%3Csvg width='50' height='50' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='50' cy='50' r='48' fill='%23800080' stroke='%23FFFFFF' stroke-width='2'/%3E%3Ctext x='50' y='55' font-family='sans-serif' font-size='35' font-weight='bold' fill='%23FFFFFF' text-anchor='middle' dominant-baseline='middle'%3E500%3C/text%3E%3C/svg%3E" alt="Fiche da $500" class="chip-button" data-value="500" width="55" height="55" draggable="false">
            <img src="data:image/svg+xml;charset=utf-8,%3Csvg width='50' height='50' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='50' cy='50' r='48' fill='%23FFA500' stroke='%23000000' stroke-width='2'/%3E%3Ctext x='50' y='55' font-family='sans-serif' font-size='30' font-weight='bold' fill='%23000000' text-anchor='middle' dominant-baseline='middle'%3E1000%3C/text%3E%3C/svg%3E" alt="Fiche da $1000" class="chip-button" data-value="1000" width="55" height="55" draggable="false">
            <img src="data:image/svg+xml;charset=utf-8,%3Csvg width='50' height='50' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='50' cy='50' r='48' fill='%230000FF' stroke='%23FFFFFF' stroke-width='2'/%3E%3Ctext x='50' y='55' font-family='sans-serif' font-size='30' font-weight='bold' fill='%23FFFFFF' text-anchor='middle' dominant-baseline='middle'%3E2000%3C/text%3E%3C/svg%3E" alt="Fiche da $2000" class="chip-button" data-value="2000" width="55" height="55" draggable="false">
        </div>
        <div id="betting-buttons">
         <button id="place-bet-button" onclick="placeBet()" disabled aria-label="Piazza la puntata selezionata">Conferma Puntata</button>
         <button id="clear-bet-button" onclick="clearProposedBet()" disabled aria-label="Azzera la puntata selezionata">Azzera Puntata</button>
         <button id="all-in-button" onclick="playerAllIn()" disabled aria-label="Punta tutto il saldo disponibile">All-in</button>
         <button id="restore-bet-button" onclick="restoreBet()" disabled aria-label="Ripristina l'ultima puntata piazzata">Ripristina Puntata</button>
        </div>
    </div>
    <div id="buttons">
     <button id="hit-button" onclick="playerHit()" disabled aria-label="Chiedi un'altra carta (H)">Carta (H)</button>
     <button id="stand-button" onclick="playerStand()" disabled aria-label="Stai con le carte attuali (Spazio/S)">Stai (Spazio/S)</button>
     <button id="double-down-button" onclick="playerDoubleDown()" disabled aria-label="Raddoppia la puntata e prendi una sola carta (D)">Raddoppia (D)</button>
     <button id="surrender-button" onclick="playerSurrender()" disabled aria-label="Arrenditi e recupera metà puntata (R)">Resa (R)</button>
     <button id="split-button" onclick="playerSplit()" disabled aria-label="Dividi le carte (L)">Dividi (L)</button>
     <button id="new-game-button" onclick="resetGame(true)" disabled aria-label="Inizia una nuova partita (N)">Nuova Partita (N)</button>
    </div>

    <div id="result" aria-live="polite"></div>

</div>

<script>
    // --- Constants and Global Variables ---
    const suits = ['♥', '♦', '♣', '♠'];
    const ranks = ['2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K', 'A'];
    const numDecks = 6;
    const localStorageKey = 'blackjackBalance';
    const lastBetStorageKey = 'blackjackLastBet';
    const statsStorageKey = 'blackjackStats';
    const themeStorageKey = 'blackjackTheme'; // Chiave per salvare il tema

    let deck = [];
    let playerHands = [];
    let dealerHand = [];
    let gameOver = true;
    let playerBalance = 1000;
    let currentBet = 0;
    let baseBet = 0;
    let lastBet = 10;
    let proposedBet = 0;
    let currentPlayerHandIndex = 0;

    // --- New Feature Variables ---
    let runningCount = 0;
    let trueCount = 0;
    let isTrainingMode = false; // Lo stato viene ora gestito dal toggle
    let showHints = false;     // Lo stato viene ora gestito dal toggle
    let initialDeckSize = numDecks * 52;
    let stats = { handsPlayed: 0, wins: 0, losses: 0, pushes: 0, blackjacks: 0 };

    // --- DOM Elements ---
    // Buttons
    const hitButton = document.getElementById('hit-button');
    const standButton = document.getElementById('stand-button');
    const doubleDownButton = document.getElementById('double-down-button');
    const surrenderButton = document.getElementById('surrender-button');
    const splitButton = document.getElementById('split-button');
    const placeBetButton = document.getElementById('place-bet-button');
    const clearBetButton = document.getElementById('clear-bet-button');
    const allInButton = document.getElementById('all-in-button');
    const restoreBetButton = document.getElementById('restore-bet-button');
    const newGameButton = document.getElementById('new-game-button');
    const toggleTrainerButton = document.getElementById('toggle-trainer-button');

    // Display Areas
    const resultElement = document.getElementById('result');
    const playerBalanceElement = document.getElementById('player-balance');
    const playerHandsContainer = document.getElementById('player-hands-container');
    const dealerCardsContainer = document.getElementById('dealer-cards');
    const dealerScoreElement = document.getElementById('dealer-score');
    const clickableChipsContainer = document.getElementById('clickable-chips');
    const proposedBetDisplay = document.getElementById('proposed-bet-display');
    const betChipsContainer = document.getElementById('bet-chips');

    // Trainer Display Elements
    const trainerControls = document.getElementById('trainer-controls');
    const runningCountDisplay = document.getElementById('running-count');
    const trueCountDisplay = document.getElementById('true-count');
    const decksRemainingDisplay = document.getElementById('decks-remaining');

    // Stats Display Elements
    const statsHandsDisplay = document.getElementById('stats-hands');
    const statsWinsDisplay = document.getElementById('stats-wins');
    const statsLossesDisplay = document.getElementById('stats-losses');
    const statsPushesDisplay = document.getElementById('stats-pushes');
    const statsBjsDisplay = document.getElementById('stats-bjs');
    const statsWinRateDisplay = document.getElementById('stats-win-rate');

    // Utility Toggles
    const themeToggle = document.getElementById('theme-toggle');
    const trainingModeToggle = document.getElementById('training-mode-toggle');
    const showHintsToggle = document.getElementById('show-hints-toggle');

    // --- Sound Function ---
    function playSound(soundElement) {
        // Implementa la logica audio se necessario
    }

    // --- Persistence Functions ---
    function saveGameState() {
        try {
            localStorage.setItem(localStorageKey, playerBalance.toString());
            if (typeof lastBet === 'number' && lastBet > 0) {
                 localStorage.setItem(lastBetStorageKey, lastBet.toString());
            } else {
                 localStorage.removeItem(lastBetStorageKey);
            }
            localStorage.setItem(statsStorageKey, JSON.stringify(stats));
            // Salva il tema CORRENTE (dark o light)
            localStorage.setItem(themeStorageKey, document.body.dataset.theme || 'light');
        } catch (e) {
            console.error("Errore nel salvataggio dello stato in localStorage:", e);
        }
    }

    function loadGameState() {
        try {
            const savedBalance = localStorage.getItem(localStorageKey);
            playerBalance = (savedBalance !== null && !isNaN(parseInt(savedBalance)) && parseInt(savedBalance) >= 0) ? parseInt(savedBalance) : 1000;
            const savedLastBet = localStorage.getItem(lastBetStorageKey);
            lastBet = (savedLastBet !== null && !isNaN(parseInt(savedLastBet)) && parseInt(savedLastBet) > 0) ? parseInt(savedLastBet) : 10;
        } catch (e) {
            console.error("Errore caricamento balance/lastBet:", e);
            playerBalance = 1000; lastBet = 10;
        }
        if (playerBalance < 0) playerBalance = 0; // Assicura che non sia negativo al caricamento
        if (lastBet < 1) lastBet = 10;

        try {
            const savedStats = localStorage.getItem(statsStorageKey);
            if (savedStats) {
                const parsedStats = JSON.parse(savedStats);
                stats.handsPlayed = Number(parsedStats.handsPlayed) || 0;
                stats.wins = Number(parsedStats.wins) || 0;
                stats.losses = Number(parsedStats.losses) || 0;
                stats.pushes = Number(parsedStats.pushes) || 0;
                stats.blackjacks = Number(parsedStats.blackjacks) || 0;
            } else {
                resetStats(false); // Non aggiornare UI qui
            }
        } catch (e) {
          console.error("Errore caricamento stats:", e);
          resetStats(false); // Non aggiornare UI qui
        }

        // Carica il tema salvato, default a 'light' (verde)
        const savedTheme = localStorage.getItem(themeStorageKey) || 'light';
        document.body.dataset.theme = savedTheme;
        themeToggle.checked = (savedTheme === 'dark'); // Imposta il toggle

        // Carica stati toggle allenamento/suggerimenti (se vuoi salvarli)
        // isTrainingMode = localStorage.getItem('blackjackTrainingMode') === 'true';
        // showHints = localStorage.getItem('blackjackShowHints') === 'true';
        // trainingModeToggle.checked = isTrainingMode;
        // showHintsToggle.checked = showHints;

        updateStatsDisplay(); // Aggiorna la UI delle statistiche
        updateUI(); // Aggiorna il resto della UI (saldo, ecc.)
    }

    // --- Deck Functions ---
    function createCard(suit, rank) {
        return { suit, rank, value: getCardValue(rank), hiLoValue: getHiLoValue(rank), revealed: false };
    }

    function createDeck() {
        deck = [];
        for (let i = 0; i < numDecks; i++) {
            for (const suit of suits) {
                for (const rank of ranks) {
                    deck.push(createCard(suit, rank));
                }
            }
        }
        initialDeckSize = deck.length; // Conferma dimensione iniziale
        runningCount = 0; // Resetta conteggio Hi-Lo
        trueCount = 0;
    }

    function shuffleDeck() {
        for (let i = deck.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            [deck[i], deck[j]] = [deck[j], deck[i]];
        }
    }

    function dealCard(reveal = true) {
        if (deck.length < initialDeckSize * 0.25) { // Reshuffle se meno del 25% delle carte
            console.log("--- Mazzo rimescolato ---");
            createDeck();
            shuffleDeck();
            // Non resettare running count qui, si azzera in createDeck
        }
        if (deck.length === 0) {
            console.error("Mazzo finito!"); // Non dovrebbe succedere con il reshuffle
            return null;
        }
        const card = deck.pop();
        card.revealed = reveal; // Imposta se la carta è rivelata
        if (reveal) {
            updateRunningCount(card); // Aggiorna conteggio SOLO se rivelata
        }
        return card;
    }


    // --- Card Value and Hi-Lo Functions ---
    function getCardValue(rank) {
        if (['K', 'Q', 'J', '10'].includes(rank)) {
            return 10;
        } else if (rank === 'A') {
            return 11; // Gli Assi valgono 11 inizialmente
        } else {
            return parseInt(rank);
        }
    }

    function getHiLoValue(rank) {
        const value = getCardValue(rank); // Usa getCardValue per semplicità
        if (value >= 2 && value <= 6) return 1;
        if (value === 10 || value === 11 || rank === 'A') return -1; // Include l'asso (valore 11)
        return 0; // 7, 8, 9
    }

    function updateRunningCount(card) {
        if (!card || !card.revealed) return; // Non contare carte non rivelate
        runningCount += card.hiLoValue;
        updateTrueCount(); // Aggiorna true count ogni volta che cambia running count
        updateTrainerDisplay(); // Aggiorna UI del trainer
    }

    function updateTrueCount() {
        const decksRemaining = Math.max(0.5, Math.round((deck.length / 52) * 2) / 2); // Stima a 0.5 mazzi
        trueCount = decksRemaining > 0 ? runningCount / decksRemaining : 0;
        // Non chiamare updateTrainerDisplay qui per evitare chiamate doppie
    }


    // --- Hand Calculation ---
    function calculateHandValue(hand) {
        let value = 0;
        let aceCount = 0;
        for (const card of hand) {
            if(card.revealed) { // Calcola solo carte rivelate
                value += card.value;
                if (card.rank === 'A') {
                    aceCount++;
                }
            }
        }
        // Gestisce gli Assi (valgono 1 se il totale > 21)
        while (value > 21 && aceCount > 0) {
            value -= 10;
            aceCount--;
        }
        return value;
    }

    // --- Display Functions ---
    function displayCard(card, container, hidden = false) {
        const cardElement = document.createElement('div');
        cardElement.classList.add('card');

        const cardInner = document.createElement('div');
        cardInner.classList.add('card-inner');

        // Fronte della carta
        const cardFront = document.createElement('div');
        cardFront.classList.add('card-face', 'card-front');
        const rankSpan = document.createElement('span');
        rankSpan.textContent = card.rank;
        const suitSpan = document.createElement('span');
        suitSpan.classList.add('suit');
        suitSpan.textContent = card.suit;

        if (['♥', '♦'].includes(card.suit)) {
            cardFront.classList.add('red');
        } else {
            cardFront.classList.add('black');
        }
        cardFront.appendChild(rankSpan);
        cardFront.appendChild(suitSpan);

        // Retro della carta
        const cardBack = document.createElement('div');
        cardBack.classList.add('card-face', 'card-back');
        // Puoi aggiungere un design al retro se vuoi

        cardInner.appendChild(cardFront);
        cardInner.appendChild(cardBack);
        cardElement.appendChild(cardInner);

        // Aggiungi un piccolo ritardo per l'animazione flip
        setTimeout(() => {
             if (!hidden && card.revealed) {
                 cardElement.classList.add('flipped');
             }
        }, 50 + Math.random() * 100); // Ritardo leggermente randomizzato


        container.appendChild(cardElement);
    }

    // --- Game Flow Functions ---
    function resetGame(isNewGameButton = false) {
        gameOver = true; // Imposta a true finché non si piazza la puntata
        // Nascondi il risultato precedente
        resultElement.textContent = '';
        resultElement.className = 'result'; // Rimuove classi win/lose/push e show

        // Pulisci mani e display
        playerHands = [];
        dealerHand = [];
        currentPlayerHandIndex = 0;
        playerHandsContainer.innerHTML = '';
        dealerCardsContainer.innerHTML = '';
        dealerScoreElement.textContent = 'Punteggio: ???';
        betChipsContainer.textContent = 'Puntata Mano: $0'; // Resetta display puntata mano

        // Gestisci saldo zero ----> MODIFICA FATTA QUI <----
        if (playerBalance <= 0) {
            playerBalance = 1000; // Ridà 1000 invece di 100
            alert("Saldo esaurito! Ti sono stati aggiunti $1000 per continuare a giocare."); // Aggiornato anche il messaggio
        }
        // ----> FINE MODIFICA <----

        // Resetta e mescola il mazzo se necessario (es. nuova partita)
        if (isNewGameButton || deck.length < initialDeckSize * 0.25) {
             createDeck();
             shuffleDeck();
             console.log("Nuovo mazzo creato e mescolato.");
        } else {
            // Non resettare conteggio se non si mescola
            updateTrueCount(); // Ricalcola true count con carte rimanenti
        }

        proposedBet = 0; // Azzera puntata proposta
        updateUI(); // Aggiorna UI (saldo, bottoni puntata)
        updateTrainerDisplay(); // Mostra valori iniziali mazzi/conteggio

        // Abilita l'area di puntata
        enableBettingControls(true);
        updateActionButtons(); // Disabilita bottoni azione
    }

    function placeBet() {
        if (proposedBet <= 0 || proposedBet > playerBalance) {
            alert("Puntata non valida.");
            return;
        }

        currentBet = proposedBet; // La puntata effettiva è quella proposta
        baseBet = proposedBet; // Salva la puntata base per double/split
        lastBet = proposedBet; // Salva come ultima puntata
        playerBalance -= currentBet;
        gameOver = false;

        // Nascondi risultato precedente se ancora visibile
        resultElement.classList.remove('result-show');

        saveGameState(); // Salva dopo aver piazzato la puntata
        enableBettingControls(false); // Disabilita puntata
        dealInitialHands();
    }

    function dealInitialHands() {
        // Crea la prima (e unica all'inizio) mano del giocatore
        playerHands = [{
            id: 0, // ID univoco per la mano
            cards: [],
            bet: currentBet, // Assegna la puntata a questa mano
            outcome: null, // 'win', 'lose', 'push', 'blackjack', 'surrender'
            message: "",
            status: 'active', // 'active', 'stand', 'busted'
            isDoubled: false,
            fromSplitAces: false
        }];

        dealerHand = [];

        // Distribuisci carte
        playerHands[0].cards.push(dealCard());
        dealerHand.push(dealCard()); // Prima carta banco (rivelata)
        playerHands[0].cards.push(dealCard());
        dealerHand.push(dealCard(false)); // Seconda carta banco (coperta)

        currentPlayerHandIndex = 0; // Inizia con la prima mano
        updateUI();

        // Controlla Blackjack immediato
        const playerValue = calculateHandValue(playerHands[0].cards);
        const dealerValue = calculateHandValue(dealerHand); // Calcola con carta coperta (che è 0 ora)

        if (playerValue === 21) {
            revealDealerCard(); // Rivela subito la carta del banco
            const finalDealerValue = calculateHandValue(dealerHand);
            if (finalDealerValue === 21) {
                playerHands[0].outcome = 'push';
                playerHands[0].message = 'Push! (Entrambi Blackjack)';
                playerHands[0].status = 'push';
                playerBalance += playerHands[0].bet; // Restituisce puntata
                stats.pushes++;
            } else {
                playerHands[0].outcome = 'blackjack';
                playerHands[0].message = 'Blackjack!';
                playerHands[0].status = 'blackjack';
                playerBalance += playerHands[0].bet * 2.5; // Paga 3:2
                stats.blackjacks++;
                stats.wins++; // Conta come vittoria
            }
            gameOver = true;
            stats.handsPlayed++;
            saveGameState();
            updateUI(); // Aggiorna UI con risultato Blackjack
            showResult(playerHands[0].message, playerHands[0].outcome); // Mostra messaggio risultato
        } else {
             // Il gioco continua normalmente, abilita i bottoni azione
             updateActionButtons();
             if (showHints) provideHint();
        }
    }

    // --- Player Actions ---
    function playerHit() {
        if (gameOver || playerHands.length === 0 || playerHands[currentPlayerHandIndex].status !== 'active') return;

        const currentHand = playerHands[currentPlayerHandIndex];
        currentHand.cards.push(dealCard());
        updateUI();

        const handValue = calculateHandValue(currentHand.cards);
        if (handValue > 21) {
            currentHand.status = 'busted';
            currentHand.outcome = 'lose';
            currentHand.message = 'Sballato!';
            stats.losses++;
            stats.handsPlayed++;
            saveGameState();
            moveToNextHandOrDealer(); // Passa alla mano successiva o al banco
        } else {
             // Dopo Hit, non puoi più raddoppiare o arrenderti (anche se tecnicamente potresti)
             // Di solito double è solo sulle prime due carte. Surrender anche.
             updateActionButtons(); // Aggiorna i bottoni (disabilita double/surrender)
             if (showHints) provideHint();
        }
    }

    function playerStand() {
        if (gameOver || playerHands.length === 0 || playerHands[currentPlayerHandIndex].status !== 'active') return;

        const currentHand = playerHands[currentPlayerHandIndex];
        currentHand.status = 'stand';
        currentHand.message = 'Stai';
        moveToNextHandOrDealer(); // Passa alla mano successiva o al banco
    }

    function playerDoubleDown() {
        if (gameOver || playerHands.length === 0 || playerHands[currentPlayerHandIndex].status !== 'active') return;

        const currentHand = playerHands[currentPlayerHandIndex];
        if (currentHand.cards.length !== 2 || playerBalance < currentHand.bet) {
             console.warn("Non puoi raddoppiare ora.");
             return; // Solitamente possibile solo con 2 carte e saldo sufficiente
        }

        playerBalance -= currentHand.bet; // Scala seconda puntata
        currentHand.bet *= 2;
        currentHand.isDoubled = true;

        // Distribuisci una sola carta
        const card = dealCard();
        currentHand.cards.push(card);
        updateUI(); // Aggiorna UI prima di controllare il risultato

        const handValue = calculateHandValue(currentHand.cards);
        if (handValue > 21) {
            currentHand.status = 'busted';
            currentHand.outcome = 'lose';
            currentHand.message = `Sballato (${handValue})`;
            stats.losses++;
        } else {
            currentHand.status = 'stand'; // Forzato stand dopo double
            currentHand.message = `Stai (${handValue})`;
        }
        stats.handsPlayed++; // La mano è conclusa
        saveGameState();
        moveToNextHandOrDealer();
    }

    function playerSurrender() {
        if (gameOver || playerHands.length === 0 || playerHands[currentPlayerHandIndex].status !== 'active') return;

        const currentHand = playerHands[currentPlayerHandIndex];
         // Di solito permesso solo come prima azione su due carte, non dopo split, non contro BJ banco
        if (currentHand.cards.length !== 2 || playerHands.length > 1) {
             console.warn("Non puoi arrenderti ora.");
             return;
        }
        // Controllo opzionale se il banco ha Asso o 10 visibile (potrebbe avere BJ)
        // In alcune regole non ci si arrende se il banco mostra A o 10. Qui lo permettiamo.

        currentHand.status = 'surrender';
        currentHand.outcome = 'surrender';
        currentHand.message = 'Resa';
        playerBalance += currentHand.bet / 2; // Recupera metà puntata

        stats.losses++; // Considerata una perdita nelle statistiche semplici
        stats.handsPlayed++;
        gameOver = true; // La mano termina qui per il giocatore
        saveGameState();
        updateUI();
        // Non c'è bisogno di moveToNextHandOrDealer perché la partita finisce qui
        showResult("Hai scelto la Resa!", 'lose'); // Mostra messaggio
        enableBettingControls(false); // Assicurati che puntata sia disabilitata
        updateActionButtons(); // Aggiorna bottoni (abilita Nuova Partita)
    }

    function playerSplit() {
        if (gameOver || playerHands.length === 0 || playerHands[currentPlayerHandIndex].status !== 'active') return;

        const currentHand = playerHands[currentPlayerHandIndex];
        // Condizioni per split: 2 carte, stesso valore (non necessariamente rango), saldo sufficiente
        if (currentHand.cards.length !== 2 ||
            getCardValue(currentHand.cards[0].rank) !== getCardValue(currentHand.cards[1].rank) ||
            playerBalance < currentHand.bet) {
             console.warn("Split non possibile");
             return;
        }

        playerBalance -= currentHand.bet; // Paga per la nuova mano

        // Crea la nuova mano
        const secondCard = currentHand.cards.pop(); // Prendi la seconda carta
        const newHand = {
            id: playerHands.length, // Nuovo ID
            cards: [secondCard], // Inizia con la seconda carta
            bet: currentHand.bet, // Stessa puntata dell'originale
            outcome: null,
            message: "",
            status: 'active',
            isDoubled: false,
            fromSplitAces: currentHand.cards[0].rank === 'A' // Segna se splitta Assi
        };

        // Modifica la mano corrente
        currentHand.fromSplitAces = currentHand.cards[0].rank === 'A';

        // Aggiungi la nuova mano all'array DOPO quella corrente
        playerHands.splice(currentPlayerHandIndex + 1, 0, newHand);

        // Distribuisci una nuova carta a CIASCUNA mano splittata
        currentHand.cards.push(dealCard());
        newHand.cards.push(dealCard());

        // Caso speciale: Split di Assi (solitamente si riceve solo 1 carta per Asso)
        if (currentHand.fromSplitAces) {
            currentHand.status = 'stand'; // Forza stand sulla prima mano di assi
            currentHand.message = calculateHandValue(currentHand.cards) === 21 ? '21 (Asso split)' : `Stai (${calculateHandValue(currentHand.cards)})`;
            newHand.status = 'stand';     // Forza stand sulla seconda mano di assi
            newHand.message = calculateHandValue(newHand.cards) === 21 ? '21 (Asso split)' : `Stai (${calculateHandValue(newHand.cards)})`;

             // Se entrambe le mani splittate di assi sono 'stand', passa alla prossima mano non 'stand' o al banco
             if (playerHands.every(hand => hand.status !== 'active')) {
                 revealDealerCard();
                 dealerTurn();
             } else {
                 // Potrebbe esserci un'altra mano attiva se si è splittato più volte
                 moveToNextHandOrDealer(); // Questo gestirà il passaggio alla mano giusta
             }
        }

        saveGameState();
        updateUI(); // Aggiorna tutta l'interfaccia
        // updateActionButtons(); // Aggiorna i bottoni per la mano corrente (che è ancora currentPlayerHandIndex)
         if (showHints && !currentHand.fromSplitAces) provideHint(); // Suggerimento per la prima mano splittata (se non assi)

    }

    function moveToNextHandOrDealer() {
        currentPlayerHandIndex++;
        if (currentPlayerHandIndex < playerHands.length) {
            // C'è un'altra mano del giocatore da giocare
            updateUI(); // Evidenzia la nuova mano corrente
            // Se la nuova mano è già 'stand' (es. split assi), passa oltre
            if (playerHands[currentPlayerHandIndex].status === 'stand') {
                moveToNextHandOrDealer();
            } else {
                // Altrimenti, aggiorna i bottoni per la nuova mano attiva
                updateActionButtons();
                if (showHints) provideHint();
            }
        } else {
            // Tutte le mani del giocatore sono concluse, tocca al banco
            revealDealerCard(); // Rivela la carta coperta
            dealerTurn();
        }
    }

    // --- Dealer Logic ---
    function revealDealerCard() {
        const hiddenCard = dealerHand.find(card => !card.revealed);
        if (hiddenCard) {
            hiddenCard.revealed = true;
            updateRunningCount(hiddenCard); // Conta la carta ora che è rivelata
            updateUI(); // Aggiorna display banco
        }
    }

    function dealerTurn() {
        if (gameOver || playerHands.every(hand => hand.status === 'busted' || hand.status === 'surrender')) {
            // Se tutte le mani del giocatore sono sballate o arrese, il banco non gioca
            gameOver = true;
            determineWinner(); // Determina subito (perdita per tutte le mani attive)
            return;
        }

        disableActionButtons(); // Disabilita bottoni giocatore durante turno banco

        // Funzione ricorsiva o ciclo con ritardo per l'azione del banco
        function dealerAction() {
            let dealerValue = calculateHandValue(dealerHand);
            updateUI(); // Aggiorna punteggio banco

            if (dealerValue < 17) {
                 // Il banco deve tirare (Hit)
                 console.log("Banco prende carta...");
                 dealerHand.push(dealCard());
                 revealDealerCard(); // Assicura sia rivelata (dovrebbe esserlo da dealCard)
                 setTimeout(dealerAction, 800); // Attendi un po' prima della prossima azione
            } else {
                 // Il banco sta (Stand)
                 console.log("Banco sta.");
                 gameOver = true;
                 determineWinner();
            }
        }

        // Inizia il turno del banco dopo un breve ritardo
        setTimeout(dealerAction, 500);
    }

    // --- Determine Winner ---
    function determineWinner() {
        const dealerValue = calculateHandValue(dealerHand);
        let finalMessage = "";
        let handsStillInPlay = false; // Ci sono mani non sballate/arrese?

        playerHands.forEach(hand => {
            // Salta mani già definite (busted, surrender, blackjack vs non-blackjack)
            if (hand.outcome) return;

            handsStillInPlay = true;
            const playerValue = calculateHandValue(hand.cards);

            if (dealerValue > 21) {
                hand.outcome = 'win';
                hand.message = `Vinto! (Banco sballa: ${dealerValue})`;
                playerBalance += hand.bet * 2; // Vinci puntata x2
                stats.wins++;
            } else if (playerValue > dealerValue) {
                hand.outcome = 'win';
                hand.message = `Vinto! (${playerValue} vs ${dealerValue})`;
                playerBalance += hand.bet * 2;
                stats.wins++;
            } else if (playerValue < dealerValue) {
                hand.outcome = 'lose';
                hand.message = `Perso. (${playerValue} vs ${dealerValue})`;
                stats.losses++;
            } else { // playerValue === dealerValue
                hand.outcome = 'push';
                hand.message = `Push! (${playerValue} vs ${dealerValue})`;
                playerBalance += hand.bet; // Restituisci puntata
                stats.pushes++;
            }
            stats.handsPlayed++; // Incrementa mani giocate solo per quelle risolte qui
        });

        if (!handsStillInPlay && playerHands.length > 0) {
             // Caso in cui tutte le mani erano sballate/arrese prima del turno del banco
             finalMessage = "Tutte le mani hanno perso prima del turno del banco.";
             // Le statistiche dovrebbero essere già state aggiornate
        } else if (playerHands.length > 0) {
            // Costruisci messaggio finale basato sui risultati delle singole mani
            finalMessage = playerHands.map(h => `Mano ${h.id + 1}: ${h.message}`).join('\n');
            // Aggiungi un riepilogo generale? (Opzionale)
            const totalWin = playerHands.filter(h=>h.outcome === 'win' || h.outcome === 'blackjack').length;
            const totalLoss = playerHands.filter(h=>h.outcome === 'lose' || h.outcome === 'surrender').length;
            const totalPush = playerHands.filter(h=>h.outcome === 'push').length;
            if (playerHands.length > 1) {
                finalMessage += `\n---\nRiepilogo: ${totalWin} Vinte, ${totalLoss} Perse, ${totalPush} Pareggi`;
            }
        } else {
            finalMessage = "Errore: Nessuna mano giocatore trovata.";
        }


        gameOver = true;
        saveGameState();
        updateUI(); // Aggiorna UI finale (saldo, punteggi, stati mano)
        showResult(finalMessage, determineOverallOutcome()); // Mostra messaggio risultato
    }

    // Funzione helper per determinare un outcome generale per l'animazione
    function determineOverallOutcome() {
        if (playerHands.length === 0) return 'push'; // Default
        const wins = playerHands.some(h => h.outcome === 'win' || h.outcome === 'blackjack');
        const losses = playerHands.some(h => h.outcome === 'lose' || h.outcome === 'surrender' || h.outcome === 'busted'); // Considera busted una perdita qui

        if (wins && !losses) return 'win'; // Solo vittorie/push
        if (losses && !wins) return 'lose'; // Solo sconfitte/push/busted
        // Se ci sono sia vittorie che sconfitte (o busted), consideralo un push per l'animazione? O win?
        return 'push'; // Compromesso per glow neutro se misto
    }


    // --- UI Update Functions ---
    function updateUI() {
        // Saldo
        playerBalanceElement.textContent = `Saldo: $${playerBalance}`;

        // Display puntata mano corrente (se esiste e non è finita)
        const activeHand = playerHands.find(h => h.status === 'active');
        betChipsContainer.textContent = `Puntata Mano: $${activeHand ? activeHand.bet : (playerHands.length > 0 ? playerHands[0].bet : currentBet)}`; // Mostra puntata attiva o prima mano o ultima bet


        // Mani Giocatore
        playerHandsContainer.innerHTML = ''; // Pulisci prima di ridisegnare
        playerHands.forEach((hand, index) => {
            const handDiv = document.createElement('div');
            handDiv.classList.add('player-hand');
            if (index === currentPlayerHandIndex && !gameOver && hand.status === 'active') {
                handDiv.classList.add('current-hand'); // Evidenzia mano attiva
            }
            handDiv.dataset.handId = hand.id;

            const title = document.createElement('h3');
            title.textContent = `Mano ${hand.id + 1}`;
            handDiv.appendChild(title);

            const cardsDiv = document.createElement('div');
            cardsDiv.classList.add('cards');
            hand.cards.forEach(card => displayCard(card, cardsDiv, !card.revealed));
            handDiv.appendChild(cardsDiv);

            const scoreP = document.createElement('p');
            scoreP.classList.add('player-score');
            scoreP.textContent = `Punteggio: ${calculateHandValue(hand.cards)}`;
            handDiv.appendChild(scoreP);

            const statusP = document.createElement('p');
            statusP.classList.add('hand-status');
            // Aggiorna testo stato/messaggio
             if (hand.status === 'busted') {
                 statusP.textContent = `Sballato (${calculateHandValue(hand.cards)})`;
                 hand.message = statusP.textContent; // Assicura che il messaggio sia aggiornato
             } else {
                 statusP.textContent = hand.message || (hand.status === 'active' ? 'Attiva' : hand.status.charAt(0).toUpperCase() + hand.status.slice(1));
             }
            handDiv.appendChild(statusP);


            const betP = document.createElement('p');
            betP.textContent = `Puntata: $${hand.bet}`;
            handDiv.appendChild(betP);

            playerHandsContainer.appendChild(handDiv);
        });

        // Mano Banco
        dealerCardsContainer.innerHTML = '';
        let dealerScoreIsFinal = false; // Flag per sapere se il punteggio del banco è definitivo
        dealerHand.forEach((card, index) => {
            let hideDealerCard = false;
            // La carta è nascosta se è la seconda (index 1), il gioco non è finito,
            // il giocatore non ha BJ o Resa, e c'è ancora almeno una mano attiva
            if (index === 1 && !gameOver && playerHands.length > 0 && playerHands[0].status !== 'blackjack' && playerHands[0].status !== 'surrender' && playerHands.some(h => h.status === 'active')) {
                 hideDealerCard = true;
            } else if (index === 1) {
                // Se non è nascosta e non era già rivelata, la riveliamo ora
                 if (!card.revealed) {
                    revealDealerCard(); // Questa funzione aggiorna anche il count e la UI
                 }
                 dealerScoreIsFinal = true; // Se la seconda carta è visibile, il punteggio è (potenzialmente) finale
            }
            // Caso speciale: se tutte le mani del giocatore sono sballate e il banco non ha ancora giocato
            if (playerHands.every(h => h.status === 'busted') && index === 1 && !card.revealed) {
                 hideDealerCard = false;
                 revealDealerCard();
                 dealerScoreIsFinal = true;
            }

            displayCard(card, dealerCardsContainer, hideDealerCard);
        });

        // Mostra punteggio banco solo se è definitivo (tutte le mani giocatore finite o tutti sballati)
        const showDealerScore = dealerHand.length > 0 && (gameOver || playerHands.every(h => h.status !== 'active'));
        dealerScoreElement.textContent = showDealerScore ? `Punteggio: ${calculateHandValue(dealerHand)}` : 'Punteggio: ???';


        // Aggiorna bottoni azione e puntata
        updateActionButtons();
        updateBettingUI(); // Aggiorna UI puntata (fiches, bottoni)

        // Aggiorna display trainer e statistiche
        updateTrainerDisplay();
        updateStatsDisplay();
    }

    function updateActionButtons() {
        const handExists = playerHands.length > 0 && currentPlayerHandIndex < playerHands.length;
        const currentHand = handExists ? playerHands[currentPlayerHandIndex] : null;
        const isActiveHand = handExists && currentHand?.status === 'active';

        // Abilita/Disabilita bottoni azione
        hitButton.disabled = gameOver || !isActiveHand;
        standButton.disabled = gameOver || !isActiveHand;

        // Double Down: non game over, mano attiva, 2 carte, saldo sufficiente, non da split assi
        doubleDownButton.disabled = gameOver || !isActiveHand || currentHand.cards.length !== 2 || playerBalance < currentHand.bet || currentHand.fromSplitAces;

        // Surrender: non game over, mano attiva, 2 carte, prima mano (no split)
        surrenderButton.disabled = gameOver || !isActiveHand || currentHand.cards.length !== 2 || playerHands.length > 1;

        // Split: non game over, mano attiva, 2 carte, valore uguale, saldo sufficiente
        const canSplit = isActiveHand && currentHand.cards.length === 2 &&
                         getCardValue(currentHand.cards[0].rank) === getCardValue(currentHand.cards[1].rank) &&
                         playerBalance >= currentHand.bet;
        splitButton.disabled = gameOver || !canSplit;

        // Nuova Partita: solo se game over
        newGameButton.disabled = !gameOver;

        // Rimuovi highlight dai bottoni
         hitButton.classList.remove('hint-highlight');
         standButton.classList.remove('hint-highlight');
         doubleDownButton.classList.remove('hint-highlight');
         surrenderButton.classList.remove('hint-highlight');
         splitButton.classList.remove('hint-highlight');
    }


    function disableActionButtons() {
         hitButton.disabled = true;
         standButton.disabled = true;
         doubleDownButton.disabled = true;
         surrenderButton.disabled = true;
         splitButton.disabled = true;
         // Rimuovi highlight
          hitButton.classList.remove('hint-highlight');
          standButton.classList.remove('hint-highlight');
          doubleDownButton.classList.remove('hint-highlight');
          surrenderButton.classList.remove('hint-highlight');
          splitButton.classList.remove('hint-highlight');
    }

    function enableBettingControls(enable) {
         clickableChipsContainer.querySelectorAll('.chip-button').forEach(chip => {
            const value = parseInt(chip.dataset.value);
            chip.disabled = !enable || value > playerBalance; // Disabilita se non si può puntare o non si ha saldo
         });
         placeBetButton.disabled = !enable || proposedBet === 0 || proposedBet > playerBalance;
         clearBetButton.disabled = !enable || proposedBet === 0;
         allInButton.disabled = !enable || playerBalance <= 0;
         restoreBetButton.disabled = !enable || lastBet <= 0 || lastBet > playerBalance;

         // Se si abilita la puntata, assicurarsi che i bottoni azione siano disabilitati
         if (enable) {
            disableActionButtons();
            newGameButton.disabled = true; // Disabilita new game durante puntata
         } else {
            // Se si disabilita la puntata (cioè si è puntato), abilita new game solo se game over
             newGameButton.disabled = !gameOver;
         }
    }

    function updateBettingUI() {
         // Aggiorna display puntata proposta
         proposedBetDisplay.textContent = `Puntata: $${proposedBet}`;

         // Aggiorna stato bottoni puntata in base a proposedBet e playerBalance
         enableBettingControls(gameOver && playerBalance > 0); // Ri-valuta stato bottoni puntata
    }

    function updateTrainerDisplay() {
        // Aggiorna i valori solo se il pannello è visibile
        if (trainerControls.style.display !== 'none') {
             const decksRemaining = Math.max(0.5, Math.round((deck.length / 52) * 2) / 2);
             runningCountDisplay.textContent = runningCount;
             decksRemainingDisplay.textContent = decksRemaining.toFixed(1);
             trueCountDisplay.textContent = trueCount.toFixed(1);
        }
    }

    function updateStatsDisplay() {
         statsHandsDisplay.textContent = stats.handsPlayed;
         statsWinsDisplay.textContent = stats.wins;
         statsLossesDisplay.textContent = stats.losses;
         statsPushesDisplay.textContent = stats.pushes;
         statsBjsDisplay.textContent = stats.blackjacks;
         const totalDecisions = stats.wins + stats.losses;
         const winRate = totalDecisions > 0 ? ((stats.wins / totalDecisions) * 100).toFixed(1) + '%' : 'N/A';
         statsWinRateDisplay.textContent = winRate;
    }

    // NUOVA: Funzione per mostrare/nascondere risultato con animazione
    function showResult(message, outcomeType = 'push') { // outcomeType per glow: 'win', 'lose', 'push'
        resultElement.textContent = message;
        resultElement.className = 'result'; // Reset classi
        // Applica classe colore in base all'esito generale
        if (outcomeType === 'win') {
             resultElement.classList.add('result-win');
        } else if (outcomeType === 'lose') {
             resultElement.classList.add('result-lose');
        } else {
             resultElement.classList.add('result-push');
        }
        resultElement.classList.add('result-show'); // Aggiunge classe per animazione/visibilità
        updateActionButtons(); // Assicura che "Nuova Partita" sia abilitato
    }

    // --- Betting Actions ---
    function addChipValue(value) {
        if (!gameOver) return; // Non aggiungere se il gioco è in corso
        const numericValue = parseInt(value);
        if (isNaN(numericValue)) return;

        if (proposedBet + numericValue <= playerBalance) {
            proposedBet += numericValue;
            updateBettingUI();
        } else {
            // Non mostrare alert, semplicemente non aggiungere se non basta
            // O potresti aggiungere solo fino al massimo possibile?
            // Esempio: proposedBet = playerBalance;
        }
    }


    function clearProposedBet() {
        if (!gameOver) return;
        proposedBet = 0;
        updateBettingUI();
    }

    function playerAllIn() {
        if (!gameOver || playerBalance <= 0) return;
        proposedBet = playerBalance;
        updateBettingUI();
    }

    function restoreBet() {
        if (!gameOver || lastBet <= 0) return;
        if (lastBet <= playerBalance) {
            proposedBet = lastBet;
            updateBettingUI();
        } else {
            // alert("Saldo insufficiente per ripristinare l'ultima puntata. Punta il massimo possibile.");
            proposedBet = playerBalance; // Punta tutto se non basta per lastBet
            updateBettingUI();
        }
    }


    // --- Utility Functions ---
    function toggleTrainer() {
        const isHidden = trainerControls.style.display === 'none';
        trainerControls.style.display = isHidden ? 'block' : 'none';
        toggleTrainerButton.textContent = isHidden ? 'Nascondi Contatore' : 'Mostra Contatore';
        if (isHidden) {
            updateTrainerDisplay(); // Aggiorna i valori quando viene mostrato
        }
    }

    function showHiLoInfo() {
        alert("Conteggio Hi-Lo:\n\nAssegna un valore ad ogni carta vista:\n- Carte 2-6: +1\n- Carte 7-9: 0\n- Carte 10, J, Q, K, A: -1\n\n- Running Count: Somma dei valori di tutte le carte viste.\n- True Count: Running Count diviso per il numero di mazzi rimasti (stima).\n\nUn True Count alto indica che nel mazzo rimangono più carte alte (10, Assi), favorendo il giocatore. Un True Count basso o negativo indica più carte basse rimaste, favorendo il banco.");
    }

    function resetStats(update = true) {
        stats = { handsPlayed: 0, wins: 0, losses: 0, pushes: 0, blackjacks: 0 };
        if (update) {
             saveGameState(); // Salva statistiche azzerate
             updateStatsDisplay(); // Aggiorna UI
             console.log("Statistiche azzerate.");
        }
    }

    // MODIFICATA: Funzione per cambiare tema
    function toggleTheme() {
        const currentTheme = document.body.dataset.theme;
        const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
        document.body.dataset.theme = newTheme;
        themeToggle.checked = (newTheme === 'dark'); // Sincronizza checkbox
        localStorage.setItem(themeStorageKey, newTheme); // Salva la preferenza
    }

    function toggleTrainingMode() {
        isTrainingMode = trainingModeToggle.checked;
        // localStorage.setItem('blackjackTrainingMode', isTrainingMode); // Salva preferenza (opzionale)
        console.log("Modalità Allenamento Conteggio:", isTrainingMode ? "Attivata" : "Disattivata");
        // Qui potresti aggiungere logica specifica per la modalità allenamento,
        // ad esempio mostrare il conteggio dopo ogni carta, fare quiz, ecc.
        // Al momento, serve solo a "sapere" che l'utente vuole allenarsi.
    }

    function toggleHints() {
        showHints = showHintsToggle.checked;
        // localStorage.setItem('blackjackShowHints', showHints); // Salva preferenza (opzionale)
        console.log("Mostra Suggerimenti (Console):", showHints ? "Attivato" : "Disattivato");
        if (showHints && !gameOver && playerHands.length > 0 && playerHands[currentPlayerHandIndex]?.status === 'active') {
            provideHint(); // Mostra subito suggerimento se attivato a metà mano
        }
    }

    // --- Basic Strategy Hint --- (Funzione base per Hit/Stand, aggiunge Double/Split basilari)
    function provideHint() {
        if (!showHints || gameOver || playerHands.length === 0 || !playerHands[currentPlayerHandIndex] || playerHands[currentPlayerHandIndex].status !== 'active') return;

        const playerHand = playerHands[currentPlayerHandIndex];
        const playerCards = playerHand.cards;
        const playerValue = calculateHandValue(playerCards);
        const dealerCard = dealerHand.find(card => card.revealed);
        const dealerUpCardValue = dealerCard ? getCardValue(dealerCard.rank) : 0; // Valore carta scoperta banco (Asso=11)

        let hint = "Azione Suggerita (Base): ";
        let suggestedAction = ''; // 'hit', 'stand', 'double', 'split', 'surrender'

        const isSoft = playerCards.some(c => c.rank === 'A') && playerValue !== calculateHandValue([{rank:'2', value:2, revealed: true}, ...playerCards.filter(c=> c.rank !== 'A')]);
        const canDouble = playerCards.length === 2 && playerBalance >= playerHand.bet && !playerHand.fromSplitAces;
        const canSplit = playerCards.length === 2 && getCardValue(playerCards[0].rank) === getCardValue(playerCards[1].rank) && playerBalance >= playerHand.bet;

        // 1. Check Split (priorità alta)
        if (canSplit) {
             const cardVal = getCardValue(playerCards[0].rank); // Valore carta (A=11)
             if (cardVal === 11 || cardVal === 8) { // Sempre split A, 8
                 suggestedAction = 'split';
             } else if (cardVal === 10) { // Mai split 10, J, Q, K
                 suggestedAction = 'stand'; // Stai con 20
             } else if (cardVal === 9) {
                 suggestedAction = ([2,3,4,5,6,8,9].includes(dealerUpCardValue)) ? 'split' : 'stand'; // Split vs 2-6, 8, 9; Stand vs 7, 10, A
             } else if (cardVal === 7) {
                 suggestedAction = (dealerUpCardValue >= 2 && dealerUpCardValue <= 7) ? 'split' : 'hit'; // Split vs 2-7
             } else if (cardVal === 6) {
                 suggestedAction = (dealerUpCardValue >= 2 && dealerUpCardValue <= 6) ? 'split' : 'hit'; // Split vs 2-6
             } else if (cardVal === 5) {
                 suggestedAction = (dealerUpCardValue >= 2 && dealerUpCardValue <= 9) ? 'double' : 'hit'; // Mai split 5s, è un Double o Hit
             } else if (cardVal === 4) {
                 suggestedAction = ([5, 6].includes(dealerUpCardValue) && canDouble) ? 'split' : 'hit'; // Split solo vs 5, 6 se Double non permesso post-split (qui lo assumiamo)
             } else { // 2s, 3s
                 suggestedAction = (dealerUpCardValue >= 2 && dealerUpCardValue <= 7) ? 'split' : 'hit'; // Split vs 2-7
             }
             // Se l'azione è split, abbiamo finito
             if (suggestedAction === 'split') {
                 hint += "Dividi";
                 highlightHintButton(suggestedAction);
                 console.log(hint);
                 return;
             }
             // Se non splitta, continua con la logica Hit/Stand/Double sotto, usando il valore della mano (es. 10 per due 5)
        }


        // 2. Check Soft Totals (dopo split check)
        if (isSoft) {
             if (playerValue >= 19) suggestedAction = 'stand'; // Soft 19+
             else if (playerValue === 18) {
                 if (canDouble && [2,3,4,5,6].includes(dealerUpCardValue)) suggestedAction = 'double'; // Double vs 2-6
                 else if ([2, 7, 8].includes(dealerUpCardValue)) suggestedAction = 'stand'; // Stand vs 2, 7, 8
                 else suggestedAction = 'hit'; // Hit vs 9, 10, A
             } else if (playerValue === 17) {
                  suggestedAction = (canDouble && [3,4,5,6].includes(dealerUpCardValue)) ? 'double' : 'hit'; // Double vs 3-6
             } else if (playerValue === 16 || playerValue === 15) {
                  suggestedAction = (canDouble && [4,5,6].includes(dealerUpCardValue)) ? 'double' : 'hit'; // Double vs 4-6
             } else { // Soft 13, 14
                 suggestedAction = (canDouble && [5,6].includes(dealerUpCardValue)) ? 'double' : 'hit'; // Double vs 5-6
             }
        }
        // 3. Check Hard Totals (dopo split e soft checks)
        else {
             if (playerValue >= 17) suggestedAction = 'stand';
             else if (playerValue >= 13 && playerValue <= 16) { // 13-16
                 suggestedAction = (dealerUpCardValue >= 2 && dealerUpCardValue <= 6) ? 'stand' : 'hit';
             } else if (playerValue === 12) {
                 suggestedAction = (dealerUpCardValue >= 4 && dealerUpCardValue <= 6) ? 'stand' : 'hit';
             } else if (playerValue === 11) {
                 suggestedAction = canDouble ? 'double' : 'hit'; // Double vs tutti
             } else if (playerValue === 10) {
                 suggestedAction = (canDouble && dealerUpCardValue >= 2 && dealerUpCardValue <= 9) ? 'double' : 'hit'; // Double vs 2-9
             } else if (playerValue === 9) {
                 suggestedAction = (canDouble && dealerUpCardValue >= 3 && dealerUpCardValue <= 6) ? 'double' : 'hit'; // Double vs 3-6
             } else { // 8 or less
                 suggestedAction = 'hit';
             }
        }

        // Final Hint Text
        if (suggestedAction === 'hit') hint += "Carta";
        else if (suggestedAction === 'stand') hint += "Stai";
        else if (suggestedAction === 'double') hint += "Raddoppia";
        // Split gestito sopra

        console.log(hint);
        highlightHintButton(suggestedAction);
    }


    function highlightHintButton(action) {
        // Rimuovi highlight precedenti da TUTTI i bottoni azione
         hitButton.classList.remove('hint-highlight');
         standButton.classList.remove('hint-highlight');
         doubleDownButton.classList.remove('hint-highlight');
         surrenderButton.classList.remove('hint-highlight'); // Anche se non suggerita qui
         splitButton.classList.remove('hint-highlight');

        // Aggiungi highlight al bottone suggerito
        switch (action) {
            case 'hit':
                if (!hitButton.disabled) hitButton.classList.add('hint-highlight');
                break;
            case 'stand':
                 if (!standButton.disabled) standButton.classList.add('hint-highlight');
                break;
            case 'double':
                if (!doubleDownButton.disabled) doubleDownButton.classList.add('hint-highlight');
                break;
            case 'split':
                if (!splitButton.disabled) splitButton.classList.add('hint-highlight');
                break;
            // Surrender non è suggerito da questa logica base
        }
    }



    // --- Event Listeners ---
    // Toggles Utilità
    themeToggle.addEventListener('change', toggleTheme);
    trainingModeToggle.addEventListener('change', toggleTrainingMode);
    showHintsToggle.addEventListener('change', toggleHints);

    // Click sulle fiches
    clickableChipsContainer.addEventListener('click', (event) => {
        if (event.target.classList.contains('chip-button') && !event.target.disabled) { // Controlla anche disabled
             const value = event.target.dataset.value;
             addChipValue(value);
        }
    });

    // Keyboard shortcuts
    document.addEventListener('keydown', (event) => {
        // Ignora input se l'utente sta scrivendo in un campo testo (non presente qui, ma buona pratica)
        // if (event.target.tagName === 'INPUT' || event.target.tagName === 'TEXTAREA') {
        //     return;
        // }

        if (gameOver && !newGameButton.disabled) { // Se il gioco è finito, N inizia nuova partita
            if (event.key === 'n' || event.key === 'N') {
                 event.preventDefault(); // Previene comportamento default (se presente)
                resetGame(true);
            }
        } else if (!gameOver && playerHands.length > 0 && playerHands[currentPlayerHandIndex]?.status === 'active') { // Se è il turno del giocatore
            let actionTaken = false;
            switch (event.key.toLowerCase()) { // Usa toLowerCase per semplicità
                case 'h': // Hit
                    if (!hitButton.disabled) { playerHit(); actionTaken = true; }
                    break;
                case ' ': // Stand (Spacebar)
                case 's':
                    if (!standButton.disabled) { playerStand(); actionTaken = true; }
                    break;
                case 'd': // Double
                    if (!doubleDownButton.disabled) { playerDoubleDown(); actionTaken = true; }
                    break;
                 case 'r': // Surrender (Resa)
                     if (!surrenderButton.disabled) { playerSurrender(); actionTaken = true; }
                     break;
                 case 'l': // Split (Lettera 'elle')
                     if (!splitButton.disabled) { playerSplit(); actionTaken = true; }
                     break;
            }
             if (actionTaken) {
                 event.preventDefault(); // Previene scroll pagina con spazio, ecc.
             }
        } else if (gameOver && !placeBetButton.disabled) { // Se si sta puntando
             if (event.key === 'Enter') { // Conferma puntata con Invio
                  event.preventDefault();
                 placeBet();
             }
             // Potresti aggiungere shortcut per le fiches (1-7?) o clear (Backspace?)
             // else if (event.key === 'Backspace') { clearProposedBet(); event.preventDefault(); }
        }
    });


    // --- Initialization ---
    window.onload = () => {
        loadGameState(); // Carica stato salvato (include saldo, stats, tema)
        resetGame(true); // Inizia il gioco (crea mazzo, abilita puntata)
    };

</script>
</body>
</html>
