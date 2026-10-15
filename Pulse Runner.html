<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Pulse Runner</title>
  <style>
    :root {
      color-scheme: dark;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      background: #080b18;
      color: #f4f7ff;
    }

    * { box-sizing: border-box; }

    body {
      min-height: 100vh;
      margin: 0;
      display: grid;
      place-items: center;
      padding: 24px;
      background:
        radial-gradient(ellipse at 50% 0%, rgba(45, 53, 109, .48), transparent 55%),
        #080b18;
    }

    .game {
      width: min(100%, 960px);
    }

    h1 {
      margin: 0 0 6px;
      color: #73f5ff;
      font-size: clamp(1.7rem, 4vw, 2.4rem);
      letter-spacing: .12em;
      text-align: center;
      text-shadow: 0 0 22px rgba(115, 245, 255, .55);
    }

    .help {
      margin: 0 0 14px;
      color: #b8c2e8;
      text-align: center;
    }

    .stage {
      position: relative;
      overflow: hidden;
      border: 2px solid #73f5ff;
      border-radius: 14px;
      box-shadow: 0 0 30px rgba(74, 202, 255, .2);
      background: #10162a;
    }

    canvas {
      display: block;
      width: 100%;
      height: auto;
      aspect-ratio: 16 / 9;
    }

    .screen {
      position: absolute;
      inset: 0;
      display: grid;
      align-content: center;
      justify-items: center;
      gap: 12px;
      overflow-y: auto;
      padding: 22px;
      background: rgba(5, 8, 20, .88);
      text-align: center;
    }

    .screen[hidden] { display: none; }

    #menu {
      align-content: start;
    }

    .screen h2 {
      margin: 0;
      color: #73f5ff;
      font-size: clamp(1.5rem, 4vw, 2.2rem);
    }

    .screen p {
      max-width: 600px;
      margin: 0;
      color: #d6defa;
    }

    .mode-grid {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 8px;
      width: min(100%, 720px);
      margin: 4px 0;
    }

    .level-picker {
      display: grid;
      grid-template-columns: repeat(6, minmax(0, 1fr));
      gap: 8px;
      width: min(100%, 480px);
    }

    .editor-tools {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 8px;
      max-width: 720px;
    }

    .preset-grid {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 8px;
      width: min(100%, 720px);
    }

    .editor-status {
      min-height: 1.4em;
      color: #b8c2e8;
    }

    #editor {
      background: rgba(5, 8, 20, .46);
    }

    button {
      min-height: 42px;
      padding: 9px 12px;
      border: 1px solid #55628e;
      border-radius: 8px;
      background: #18213c;
      color: #f4f7ff;
      font: inherit;
      font-weight: 650;
      cursor: pointer;
    }

    button:hover, button:focus-visible {
      border-color: #73f5ff;
      outline: 2px solid rgba(115, 245, 255, .35);
      background: #243257;
    }

    button.selected {
      border-color: #73f5ff;
      background: #174359;
      color: #9ff9ff;
    }

    button.primary {
      min-width: 180px;
      border-color: #73f5ff;
      background: #08748a;
    }

    @media (max-width: 620px) {
      body { padding: 12px; }
      .screen { gap: 8px; padding: 12px; }
      .mode-grid { grid-template-columns: repeat(3, minmax(0, 1fr)); gap: 6px; }
      .mode-grid button { padding: 7px 4px; font-size: .82rem; }
    }
  </style>
</head>
<body>
  <main class="game">
    <h1>PULSE RUNNER</h1>
    <p class="help">Choose any number of modes and obstacle presets, then select a level from 1 to 12 to start. New layouts are generated each run.</p>
    <div class="stage">
      <canvas id="game" width="960" height="540" aria-label="Pulse Runner game"></canvas>
      <section id="menu" class="screen" aria-label="Choose game mode">
        <h2>Choose a level and mode</h2>
        <p id="mode-description">Choose one or more gameplay modes and obstacle presets.</p>
        <div id="level-picker" class="level-picker" role="group" aria-label="Choose a level to start"></div>
        <p class="help">Obstacle presets (choose one or more; selected presets mix together):</p>
        <div id="preset-grid" class="preset-grid" role="group" aria-label="Obstacle layout presets"></div>
        <p class="help">Click mode buttons to combine them. When modes conflict, the last selected setting takes priority.</p>
        <div class="editor-tools">
          <button id="editor-open" type="button">Open Level Editor</button>
          <button id="custom-play" type="button" hidden>Play Saved Level</button>
        </div>
        <div id="mode-grid" class="mode-grid" role="group" aria-label="Choose gameplay modes; multiple can be combined"></div>
      </section>
      <section id="editor" class="screen" aria-label="Level editor" hidden>
        <h2>Level Editor</h2>
        <p>Choose an object, then click anywhere in the playfield (not on a button) to place it. Positions snap to the grid.</p>
        <div class="editor-tools">
          <button type="button" data-editor-tool="spike" class="selected">Spike</button>
          <button type="button" data-editor-tool="block">Block</button>
          <button type="button" data-editor-tool="pad">Pulse Pad</button>
          <button id="editor-undo" type="button">Undo</button>
          <button id="editor-clear" type="button">Clear</button>
          <button id="editor-save" type="button">Save Level</button>
          <button id="editor-play" type="button" class="primary">Save &amp; Play</button>
          <button id="editor-back" type="button">Back to Menu</button>
        </div>
        <p id="editor-status" class="editor-status" aria-live="polite">Place objects by clicking in the level area.</p>
      </section>
      <section id="message" class="screen" hidden>
        <h2 id="message-title"></h2>
        <p id="message-detail"></p>
        <button id="message-button" class="primary"></button>
      </section>
    </div>
    <p class="help">↑ jump · Q open menu · R restart · after a crash, press any key to retry. Pulse pads bounce you up.</p>
  </main>

  <script>
    "use strict";

    const canvas = document.querySelector("#game");
    const ctx = canvas.getContext("2d");
    const menu = document.querySelector("#menu");
    const editor = document.querySelector("#editor");
    const modeGrid = document.querySelector("#mode-grid");
    const presetGrid = document.querySelector("#preset-grid");
    const modeDescription = document.querySelector("#mode-description");
    const levelPicker = document.querySelector("#level-picker");
    const message = document.querySelector("#message");
    const messageTitle = document.querySelector("#message-title");
    const messageDetail = document.querySelector("#message-detail");
    const messageButton = document.querySelector("#message-button");
    const editorStatus = document.querySelector("#editor-status");
    const customPlayButton = document.querySelector("#custom-play");

    const width = canvas.width;
    const height = canvas.height;
    const floor = 448;
    const modes = [
      { name: "Classic", description: "The original challenge: jump over the obstacles." },
      { name: "Double Jump", description: "Jump once more while you are still in the air.", doubleJump: true },
      { name: "Low Gravity", description: "Float higher and stay in the air longer.", gravity: 0.68 },
      { name: "Heavy Gravity", description: "Fall quickly, so time your jumps carefully.", gravity: 1.45 },
      { name: "Speed Rush", description: "Everything moves faster. React quickly.", speed: 1.28 },
      { name: "Tiny Runner", description: "A smaller player has a smaller collision box.", size: 0.68 },
      { name: "Big Runner", description: "A bigger player makes every jump trickier.", size: 1.28 },
      { name: "Pad Boost", description: "Pulse pads give you an extra powerful bounce.", padBoost: true },
      { name: "Moving Hazards", description: "Obstacles move up and down as they approach.", movingHazards: true },
      { name: "Shield", description: "Survive one collision in each level.", shield: true },
      { name: "Gravity Flip", description: "Gravity switches every few seconds; ↑ jumps away from the surface.", gravityFlip: true },
      { name: "Pulse Jump", description: "Jump power pulses. A bright ring means a stronger jump.", pulseJump: true }
    ];

    const obstaclePresets = [
      { id: "balanced", name: "Balanced", description: "A varied mix of spikes, blocks, and pads." },
      { id: "spikes", name: "Spike Trail", description: "More spike runs and double spikes." },
      { id: "pads", name: "Pad Practice", description: "More pulse pads mixed with hazards." },
      { id: "blocks", name: "Block Party", description: "More solid blocks to jump over." }
    ];
    let selectedMode = 0;
    const selectedModes = new Set([0]);
    let selectedLevel = 1;
    const selectedPresets = new Set(["balanced"]);
    let gameState = "menu";
    let level = 1;
    let distance = 0;
    let elapsed = 0;
    let lastFrame = 0;
    let score = 0;
    let obstacles = [];
    let shieldAvailable = false;
    let transitionTime = 0;
    let attemptLevel = 0;
    let attemptCount = 0;
    let gravityDirection = 1;
    let nextGravityFlip = 0;
    let jumpBufferTime = 0;
    const jumpBufferDuration = 0.16;
    const player = { x: 150, y: 0, width: 42, height: 42, velocityY: 0, jumps: 0, grounded: true };
    const customLevelStorageKey = "pulse-runner-custom-level-v1";
    const editorLength = 3600;
    let customObstacles = loadCustomLevel();
    let customRun = false;
    let editorTool = "spike";

    function makeModeButtons() {
      modes.forEach((mode, index) => {
        const button = document.createElement("button");
        button.type = "button";
        button.textContent = `${index + 1}. ${mode.name}`;
        button.setAttribute("aria-pressed", String(selectedModes.has(index)));
        button.classList.toggle("selected", selectedModes.has(index));
        button.addEventListener("click", () => {
          selectMode(index);
        });
        modeGrid.append(button);
      });
    }

    function selectMode(index) {
      selectedMode = (index + modes.length) % modes.length;
      if (selectedModes.has(selectedMode)) {
        selectedModes.delete(selectedMode);
        if (selectedModes.size === 0) selectedModes.add(0);
      } else {
        selectedModes.add(selectedMode);
      }
      modeDescription.textContent = `Modes: ${[...selectedModes].map(modeIndex => modes[modeIndex].name).join(" + ")}. ${[...selectedModes].filter(modeIndex => modeIndex !== 0).map(modeIndex => modes[modeIndex].description).join(" ")}`;
      modeGrid.querySelectorAll("button").forEach((item, itemIndex) => {
        const selected = selectedModes.has(itemIndex);
        item.classList.toggle("selected", selected);
        item.setAttribute("aria-pressed", String(selected));
      });
    }

    function makePresetButtons() {
      obstaclePresets.forEach(preset => {
        const button = document.createElement("button");
        button.type = "button";
        button.textContent = preset.name;
        button.setAttribute("aria-pressed", String(selectedPresets.has(preset.id)));
        button.classList.toggle("selected", selectedPresets.has(preset.id));
        button.title = preset.description;
        button.addEventListener("click", () => {
          if (selectedPresets.has(preset.id)) {
            if (selectedPresets.size === 1) return;
            selectedPresets.delete(preset.id);
          } else {
            selectedPresets.add(preset.id);
          }
          updatePresetButtons();
        });
        presetGrid.append(button);
      });
    }

    function updatePresetButtons() {
      presetGrid.querySelectorAll("button").forEach((button, index) => {
        const selected = selectedPresets.has(obstaclePresets[index].id);
        button.classList.toggle("selected", selected);
        button.setAttribute("aria-pressed", String(selected));
      });
    }

    function selectLevel(nextLevel) {
      selectedLevel = ((nextLevel - 1 + 12) % 12) + 1;
      levelPicker.querySelectorAll("button").forEach((item, itemIndex) => {
        const selected = itemIndex + 1 === selectedLevel;
        item.classList.toggle("selected", selected);
        item.setAttribute("aria-pressed", String(selected));
      });
    }

    function makeLevelButtons() {
      for (let levelNumber = 1; levelNumber <= 12; levelNumber += 1) {
        const button = document.createElement("button");
        button.type = "button";
        button.textContent = String(levelNumber);
        button.setAttribute("aria-label", `Level ${levelNumber}`);
        button.setAttribute("aria-pressed", String(levelNumber === selectedLevel));
        button.classList.toggle("selected", levelNumber === selectedLevel);
        button.addEventListener("click", () => {
          selectLevel(levelNumber);
          startGame();
        });
        levelPicker.append(button);
      }
    }

    function currentMode() {
      const activeModes = [...selectedModes]
        .filter(index => index !== 0)
        .map(index => modes[index]);
      const combined = Object.assign({}, ...activeModes);
      return {
        ...combined,
        name: activeModes.length ? activeModes.map(mode => mode.name).join(" + ") : modes[0].name,
        description: activeModes.map(mode => mode.description).join(" ")
      };
    }

    function levelLength() {
      if (customRun) return editorLength;
      return 2600 + (level - 1) * 280;
    }

    function worldSpeed() {
      const levelBoost = 1 + (level - 1) * 0.08;
      const modeBoost = currentMode().speed || 1;
      return 330 * levelBoost * modeBoost;
    }

    function createObstacles() {
      if (customRun) {
        obstacles = customObstacles.map(obstacle => ({ ...obstacle, phase: 0, activated: false }));
        return;
      }

      obstacles = [];
      const random = Math.random;

      let x = 690;
      while (x < levelLength() + 250) {
        const presetIds = [...selectedPresets];
        const preset = presetIds[Math.floor(random() * presetIds.length)] || "balanced";
        const roll = random();
        const type = (preset === "pads" && roll > 0.48) ||
          (preset === "balanced" && roll > 0.84) ? "pad" : "hazard";
        const doubleChance = preset === "spikes"
          ? Math.min(0.58, 0.36 + (level - 1) * 0.02)
          : Math.min(0.45, 0.22 + (level - 1) * 0.02);
        const double = random() > 1 - doubleChance;
        const block = preset === "blocks" ? random() > 0.45 : random() > 0.76;
        const obstacleWidth = type === "pad" ? 62 : block ? 48 : double ? 82 : 42;
        const obstacleHeight = type === "pad" ? 16 : block ? 58 : 46;
        obstacles.push({
          x,
          width: obstacleWidth,
          height: obstacleHeight,
          type,
          block,
          phase: random() * Math.PI * 2,
          activated: false
        });
        const gap = Math.max(205, 360 - (level - 1) * 10) + random() * 110;
        x += obstacleWidth + gap;
      }
    }

    function startLevel(nextLevel, useCustom = customRun) {
      customRun = useCustom;
      if (nextLevel !== attemptLevel) {
        attemptLevel = nextLevel;
        attemptCount = 1;
      } else {
        attemptCount += 1;
      }
      level = nextLevel;
      distance = 0;
      elapsed = 0;
      score = 0;
      transitionTime = 0;
      gravityDirection = 1;
      nextGravityFlip = 4;
      shieldAvailable = Boolean(currentMode().shield);
      const scale = currentMode().size || 1;
      player.width = 42 * scale;
      player.height = 42 * scale;
      player.x = 150;
      player.y = floor - player.height;
      player.velocityY = 0;
      player.jumps = 0;
      player.grounded = true;
      jumpBufferTime = 0;
      createObstacles();
      gameState = "playing";
      menu.hidden = true;
      editor.hidden = true;
      message.hidden = true;
    }

    function startGame() {
      startLevel(selectedLevel, false);
    }

    function startCustomGame() {
      customRun = true;
      startLevel(selectedLevel, true);
    }

    function returnToMenu() {
      gameState = "menu";
      editor.hidden = true;
      message.hidden = true;
      menu.hidden = false;
      menu.scrollTop = 0;
    }

    function openEditor() {
      gameState = "editor";
      menu.hidden = true;
      message.hidden = true;
      editor.hidden = false;
      editorStatus.textContent = "Place objects by clicking in the level area.";
    }

    function editorPlaceAtPointer(event) {
      if (gameState !== "editor") return;
      const rect = canvas.getBoundingClientRect();
      const screenX = (event.clientX - rect.left) * width / rect.width;
      if (screenX < 150 || screenX > width - 20) return;
      const x = Math.round((350 + ((screenX - 150) / (width - 170)) * (editorLength - 350)) / 20) * 20;
      const type = editorTool === "pad" ? "pad" : "hazard";
      customObstacles.push({
        x,
        width: editorTool === "pad" ? 62 : editorTool === "block" ? 48 : 42,
        height: editorTool === "pad" ? 16 : editorTool === "block" ? 58 : 46,
        type,
        block: editorTool === "block",
        phase: 0,
        activated: false
      });
      editorStatus.textContent = `${editorTool === "pad" ? "Pulse pad" : editorTool} added at ${x} units.`;
    }

    function saveCustomLevel() {
      try {
        const saved = customObstacles.map(({ x, width: obstacleWidth, height: obstacleHeight, type, block }) => ({
          x, width: obstacleWidth, height: obstacleHeight, type, block
        }));
        if (saved.length) localStorage.setItem(customLevelStorageKey, JSON.stringify(saved));
        else localStorage.removeItem(customLevelStorageKey);
        customPlayButton.hidden = saved.length === 0;
        editorStatus.textContent = `Saved your level with ${saved.length} object${saved.length === 1 ? "" : "s"}.`;
        return true;
      } catch (error) {
        editorStatus.textContent = `Could not save level: ${error.message}`;
        return false;
      }
    }

    function loadCustomLevel() {
      try {
        const saved = localStorage.getItem(customLevelStorageKey);
        if (!saved) return [];
        const parsed = JSON.parse(saved);
        if (!Array.isArray(parsed) || parsed.some(item =>
          !item || !Number.isFinite(item.x) || !Number.isFinite(item.width) ||
          !Number.isFinite(item.height) || !["hazard", "pad"].includes(item.type) ||
          typeof item.block !== "boolean"
        )) {
          throw new Error("Saved level data is invalid.");
        }
        customPlayButton.hidden = parsed.length === 0;
        return parsed.map(item => ({ ...item, phase: 0, activated: false }));
      } catch (error) {
        customPlayButton.hidden = true;
        editorStatus.textContent = `Could not load saved level: ${error.message}`;
        return [];
      }
    }

    function finishGame(won) {
      gameState = won ? "won" : "over";
      messageTitle.textContent = won
        ? customRun ? "Custom level complete!" : "You beat all 12 levels!"
        : "Game over";
      messageDetail.textContent = won
        ? `Great run in ${currentMode().name} mode!`
        : `You reached Level ${level}. Press any key to try again.`;
      messageButton.textContent = won ? "Play again" : "Retry now";
      messageButton.hidden = false;
      messageButton.onclick = () => startLevel(level);
      message.hidden = false;
    }

    function tryJump() {
      if (gameState !== "playing") return false;
      const mode = currentMode();
      const canDoubleJump = mode.doubleJump && player.jumps < 2;
      if (!player.grounded && !canDoubleJump) return false;
      const gravity = 1900 * (mode.gravity || 1);
      const peakHeight = mode.pulseJump && Math.sin(elapsed * Math.PI * 2) > 0.65 ? 88 : 78;
      player.velocityY = -Math.sqrt(2 * gravity * peakHeight) * gravityDirection;
      player.grounded = false;
      player.jumps += 1;
      jumpBufferTime = 0;
      return true;
    }

    function requestJump() {
      if (gameState !== "playing") return;
      jumpBufferTime = jumpBufferDuration;
      tryJump();
    }

    function playerBounds() {
      const inset = Math.max(5, player.width * 0.12);
      return {
        left: player.x + inset,
        right: player.x + player.width - inset,
        top: player.y + inset,
        bottom: player.y + player.height - inset
      };
    }

    function obstacleBounds(obstacle) {
      const mode = currentMode();
      const wave = mode.movingHazards ? Math.sin(elapsed * 4 + obstacle.phase) * 42 : 0;
      const screenX = obstacle.x - distance;
      const horizontalInset = 5;
      if (gravityDirection < 0) {
        return {
          left: screenX + horizontalInset,
          right: screenX + obstacle.width - horizontalInset,
          top: 4,
          bottom: obstacle.height + wave - 4
        };
      }
      return {
        left: screenX + horizontalInset,
        right: screenX + obstacle.width - horizontalInset,
        top: floor - obstacle.height + wave + 4,
        bottom: floor - 2
      };
    }

    function intersects(a, b) {
      return a.left < b.right && a.right > b.left && a.top < b.bottom && a.bottom > b.top;
    }

    function update(delta) {
      if (gameState === "between") {
        transitionTime -= delta;
        if (transitionTime <= 0) startLevel(level);
        return;
      }
      if (gameState !== "playing") return;

      const mode = currentMode();
      elapsed += delta;
      jumpBufferTime = Math.max(0, jumpBufferTime - delta);
      distance += worldSpeed() * delta;
      score = Math.floor(distance / 10);

      if (mode.gravityFlip && elapsed >= nextGravityFlip) {
        gravityDirection *= -1;
        nextGravityFlip += 4;
        player.velocityY = 0;
        player.grounded = false;
      }

      const gravity = 1900 * (mode.gravity || 1) * gravityDirection;
      const wasGrounded = player.grounded;
      player.velocityY += gravity * delta;
      const previousY = player.y;
      player.y += player.velocityY * delta;

      if (gravityDirection > 0 && player.velocityY >= 0) {
        for (const obstacle of obstacles) {
          if (obstacle.type !== "pad" || obstacle.activated) continue;
          const padLeft = obstacle.x - distance;
          const padTop = floor - obstacle.height;
          const padInset = 5;
          const crossedPad = (wasGrounded || previousY + player.height <= padTop + 8) &&
            player.y + player.height >= padTop + 4 &&
            player.x + player.width - padInset > padLeft + padInset &&
            player.x + padInset < padLeft + obstacle.width - padInset;
          if (crossedPad) {
            player.y = padTop - player.height;
            const padPeakHeight = mode.padBoost ? 105 : 92;
            player.velocityY = -Math.sqrt(2 * 1900 * (mode.gravity || 1) * padPeakHeight);
            player.grounded = false;
            player.jumps = 1;
            obstacle.activated = true;
            break;
          }
        }
      }

      if (gravityDirection > 0 && player.y + player.height >= floor) {
        player.y = floor - player.height;
        player.velocityY = 0;
        player.grounded = true;
        player.jumps = 0;
      } else if (gravityDirection < 0 && player.y <= 0) {
        player.y = 0;
        player.velocityY = 0;
        player.grounded = true;
        player.jumps = 0;
      } else {
        player.grounded = false;
      }

      if (jumpBufferTime > 0 && player.grounded) tryJump();

      for (const obstacle of obstacles) {
        if (obstacle.type === "pad") continue;
        const bounds = obstacleBounds(obstacle);
        if (intersects(playerBounds(), bounds)) {
          if (shieldAvailable) {
            shieldAvailable = false;
            obstacle.x = -1000;
          } else {
            finishGame(false);
            return;
          }
        }
      }

      if (distance >= levelLength()) {
        if (!customRun && level < 12) {
          const nextLevel = level + 1;
          gameState = "between";
          transitionTime = 1.4;
          messageTitle.textContent = `Level ${level} complete!`;
          messageDetail.textContent = `Get ready — Level ${nextLevel} is faster and has more obstacles.`;
          messageButton.hidden = true;
          message.hidden = false;
          level = nextLevel;
        } else {
          finishGame(true);
        }
      }
    }

    function drawBackground() {
      const gradient = ctx.createLinearGradient(0, 0, 0, height);
      gradient.addColorStop(0, "#121b38");
      gradient.addColorStop(1, "#080d1b");
      ctx.fillStyle = gradient;
      ctx.fillRect(0, 0, width, height);

      ctx.strokeStyle = "rgba(115, 245, 255, .08)";
      ctx.lineWidth = 1;
      for (let x = -((distance * 0.16) % 60); x < width; x += 60) {
        ctx.beginPath();
        ctx.moveTo(x, 0);
        ctx.lineTo(x, floor);
        ctx.stroke();
      }
      for (let y = 50; y < floor; y += 60) {
        ctx.beginPath();
        ctx.moveTo(0, y);
        ctx.lineTo(width, y);
        ctx.stroke();
      }
    }

    function drawGround() {
      ctx.fillStyle = "#172440";
      ctx.fillRect(0, floor, width, height - floor);
      ctx.fillStyle = "#73f5ff";
      ctx.fillRect(0, floor, width, 4);
      if (gravityDirection < 0) {
        ctx.fillStyle = "#ffcf6e";
        ctx.fillRect(0, 0, width, 4);
      }
    }

    function drawObstacles() {
      obstacles.forEach(obstacle => {
        const x = obstacle.x - distance;
        if (x > width || x + obstacle.width < 0) return;
        if (obstacle.type === "pad") {
          const y = floor - obstacle.height;
          ctx.save();
          ctx.shadowColor = obstacle.activated ? "#73839c" : "#ffe27a";
          ctx.shadowBlur = obstacle.activated ? 4 : 20;
          ctx.fillStyle = obstacle.activated ? "#64738d" : "#ffd95f";
          ctx.fillRect(x, y, obstacle.width, obstacle.height);
          ctx.fillStyle = "#fff8d1";
          ctx.fillRect(x + 8, y + 4, obstacle.width - 16, 3);
          ctx.restore();
          return;
        }
        const bounds = obstacleBounds(obstacle);
        ctx.fillStyle = obstacle.block ? "#ff4f86" : "#86ffb2";
        ctx.shadowColor = ctx.fillStyle;
        ctx.shadowBlur = 12;
        if (obstacle.block) {
          ctx.fillRect(x, bounds.top, obstacle.width, bounds.bottom - bounds.top);
        } else {
          ctx.beginPath();
          if (gravityDirection > 0) {
            ctx.moveTo(x, bounds.bottom);
            ctx.lineTo(x + obstacle.width / 2, bounds.top);
            ctx.lineTo(x + obstacle.width, bounds.bottom);
          } else {
            ctx.moveTo(x, bounds.top);
            ctx.lineTo(x + obstacle.width / 2, bounds.bottom);
            ctx.lineTo(x + obstacle.width, bounds.top);
          }
          ctx.closePath();
          ctx.fill();
        }
        ctx.shadowBlur = 0;
      });
    }

    function drawEditorObjects() {
      customObstacles.forEach(obstacle => {
        const x = 150 + ((obstacle.x - 350) / (editorLength - 350)) * (width - 170);
        if (x < 150 || x > width - 20) return;
        if (obstacle.type === "pad") {
          const y = floor - obstacle.height;
          ctx.fillStyle = "#ffd95f";
          ctx.shadowColor = "#ffe27a";
          ctx.shadowBlur = 12;
          ctx.fillRect(x, y, obstacle.width * .65, obstacle.height);
          ctx.shadowBlur = 0;
        } else {
          ctx.fillStyle = obstacle.block ? "#ff4f86" : "#86ffb2";
          if (obstacle.block) {
            ctx.fillRect(x, floor - obstacle.height, obstacle.width * .65, obstacle.height);
          } else {
            ctx.beginPath();
            ctx.moveTo(x, floor);
            ctx.lineTo(x + obstacle.width * .325, floor - obstacle.height);
            ctx.lineTo(x + obstacle.width * .65, floor);
            ctx.closePath();
            ctx.fill();
          }
        }
      });
    }

    function drawPlayer() {
      ctx.save();
      ctx.shadowColor = "#ff4fbb";
      ctx.shadowBlur = 18;
      ctx.fillStyle = "#ff4fbb";
      ctx.fillRect(player.x, player.y, player.width, player.height);
      ctx.shadowBlur = 0;
      ctx.fillStyle = "#fff4a8";
      const eyeSize = Math.max(4, player.width * .14);
      ctx.fillRect(player.x + player.width * .22, player.y + player.height * .24, eyeSize, eyeSize);
      ctx.fillRect(player.x + player.width * .62, player.y + player.height * .24, eyeSize, eyeSize);
      ctx.restore();
    }

    function drawHud() {
      ctx.fillStyle = "#f4f7ff";
      ctx.font = "bold 20px system-ui, sans-serif";
      ctx.fillText(customRun ? "CUSTOM LEVEL" : `LEVEL ${level} / 12`, 24, 34);
      ctx.font = "16px system-ui, sans-serif";
      ctx.fillStyle = "#b8c2e8";
      ctx.fillText(`${currentMode().name} · Score ${score}`, 24, 60, width - 280);
      ctx.fillStyle = "#30405f";
      ctx.fillRect(24, 76, 230, 8);
      ctx.fillStyle = "#73f5ff";
      ctx.fillRect(24, 76, 230 * Math.min(1, distance / levelLength()), 8);
      ctx.fillStyle = "#8e9ab9";
      ctx.font = "12px system-ui, sans-serif";
      ctx.fillText(`ATTEMPT ${attemptCount}`, 24, 101);
      if (currentMode().shield && shieldAvailable) {
        ctx.fillStyle = "#ffe27a";
        ctx.fillText("SHIELD READY", width - 150, 34);
      }
      if (currentMode().pulseJump) {
        const pulse = Math.sin(elapsed * Math.PI * 2) > .65;
        ctx.strokeStyle = pulse ? "#ffe27a" : "rgba(255, 226, 122, .25)";
        ctx.lineWidth = 3;
        ctx.beginPath();
        ctx.arc(player.x + player.width / 2, player.y + player.height / 2, player.width * .8, 0, Math.PI * 2);
        ctx.stroke();
      }
    }

    function draw() {
      drawBackground();
      drawGround();
      if (gameState === "editor") drawEditorObjects();
      else drawObstacles();
      if (gameState === "playing" || gameState === "between" || gameState === "over" || gameState === "won") {
        drawPlayer();
        drawHud();
      }
      if (currentMode().darkness && gameState === "playing") {
        ctx.save();
        ctx.fillStyle = "rgba(0, 0, 0, .87)";
        ctx.fillRect(0, 0, width, height);
        const glow = ctx.createRadialGradient(player.x + player.width / 2, player.y + player.height / 2, 18, player.x + player.width / 2, player.y + player.height / 2, 190);
        glow.addColorStop(0, "rgba(0, 0, 0, 0)");
        glow.addColorStop(1, "rgba(0, 0, 0, 1)");
        ctx.globalCompositeOperation = "destination-out";
        ctx.fillStyle = glow;
        ctx.fillRect(0, 0, width, height);
        ctx.restore();
      }
    }

    function frame(timestamp) {
      const delta = lastFrame ? Math.min((timestamp - lastFrame) / 1000, 0.04) : 0;
      lastFrame = timestamp;
      update(delta);
      draw();
      requestAnimationFrame(frame);
    }

    document.querySelector("#editor-open").addEventListener("click", openEditor);
    customPlayButton.addEventListener("click", () => {
      if (customObstacles.length) startCustomGame();
    });
    document.querySelectorAll("[data-editor-tool]").forEach(button => {
      button.addEventListener("click", () => {
        editorTool = button.dataset.editorTool;
        document.querySelectorAll("[data-editor-tool]").forEach(toolButton => {
          toolButton.classList.toggle("selected", toolButton === button);
        });
      });
    });
    document.querySelector("#editor-undo").addEventListener("click", () => {
      customObstacles.pop();
      editorStatus.textContent = "Removed the most recently added object.";
    });
    document.querySelector("#editor-clear").addEventListener("click", () => {
      customObstacles = [];
      editorStatus.textContent = "Cleared the level.";
    });
    document.querySelector("#editor-save").addEventListener("click", saveCustomLevel);
    document.querySelector("#editor-play").addEventListener("click", () => {
      if (saveCustomLevel() && customObstacles.length) startCustomGame();
      else if (!customObstacles.length) editorStatus.textContent = "Add at least one object before playing your level.";
    });
    document.querySelector("#editor-back").addEventListener("click", returnToMenu);
    editor.addEventListener("pointerdown", event => {
      if (event.target.closest("button")) return;
      editorPlaceAtPointer(event);
    });
    canvas.addEventListener("pointerdown", event => {
      if (gameState === "editor") editorPlaceAtPointer(event);
      else requestJump();
    });

    document.addEventListener("keydown", event => {
      if (gameState === "over") {
        event.preventDefault();
        startLevel(level);
        return;
      }
      if (gameState === "editor" && event.key === "Escape") {
        returnToMenu();
        return;
      }
      if (event.key.toLowerCase() === "q") {
        event.preventDefault();
        returnToMenu();
        return;
      }
      if (gameState === "menu") {
        if (event.code === "ArrowLeft") {
          event.preventDefault();
          selectMode(selectedMode - 1);
        } else if (event.code === "ArrowRight") {
          event.preventDefault();
          selectMode(selectedMode + 1);
        } else if (event.code === "ArrowUp") {
          event.preventDefault();
          selectLevel(selectedLevel - 1);
        } else if (event.code === "ArrowDown") {
          event.preventDefault();
          selectLevel(selectedLevel + 1);
        } else if (event.code === "Enter") {
          startGame();
        }
        return;
      }
      if (event.code === "ArrowUp") {
        event.preventDefault();
        if (!event.repeat) requestJump();
      } else if (event.key.toLowerCase() === "r") {
        if (gameState === "won") startGame();
        else if (gameState === "playing" || gameState === "over") startLevel(level);
      }
    });
    makeModeButtons();
    makeLevelButtons();
    makePresetButtons();
    requestAnimationFrame(frame);
  </script>
</body>
</html>
