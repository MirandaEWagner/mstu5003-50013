# mstu5003-50013
The project is a single file: [index.html](/Users/mirandaeinhorn/Documents/ChatGPT/wheel/index.html).

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Build a Flow</title>
    <style>
      :root {
        --ink: #24312c;
        --paper: #fff8ef;
      }

      * { box-sizing: border-box; }

      body {
        align-items: center;
        background:
          radial-gradient(circle at 12% 12%, #ffd8a8 0 8%, transparent 8.5%),
          radial-gradient(circle at 88% 86%, #c5e8dc 0 9%, transparent 9.5%),
          var(--paper);
        color: var(--ink);
        display: flex;
        font-family: Georgia, "Times New Roman", serif;
        justify-content: center;
        margin: 0;
        min-height: 100vh;
        padding: 2rem;
      }

      main { text-align: center; width: min(100%, 640px); }
      h1 { font-size: clamp(2.3rem, 8vw, 4.8rem); font-weight: 400; letter-spacing: -.06em; margin: 0 0 .15rem; }
      .subtitle { font-family: system-ui, sans-serif; font-size: .78rem; letter-spacing: .18em; margin: 0 0 1.8rem; text-transform: uppercase; }

      .spinner {
        background: transparent;
        border: 0;
        cursor: pointer;
        display: block;
        margin: auto;
        padding: 0;
        position: relative;
        width: min(88vw, 480px);
      }

      .pointer {
        border-left: 18px solid transparent;
        border-right: 18px solid transparent;
        border-top: 38px solid var(--ink);
        height: 0;
        left: 50%;
        position: absolute;
        top: -5px;
        transform: translateX(-50%);
        width: 0;
        z-index: 2;
      }

      .wheel {
        animation: spin 1s linear infinite;
        aspect-ratio: 1;
        background: conic-gradient(
          #ff847c 0deg 45deg, #ffd166 45deg 90deg, #9adfce 90deg 135deg,
          #77bdfb 135deg 180deg, #b9a7ef 180deg 225deg, #f49ac2 225deg 270deg,
          #ffae6d 270deg 315deg, #a5d66c 315deg 360deg
        );
        border: 10px solid #fffdf8;
        border-radius: 50%;
        display: block;
        box-shadow: 0 15px 34px rgb(50 60 49 / .20);
        overflow: hidden;
        position: relative;
      }

      .wheel::after {
        background: var(--paper);
        border: 6px solid var(--ink);
        border-radius: 50%;
        content: "✦";
        display: grid;
        font-size: 2.2rem;
        height: 21%;
        left: 39.5%;
        place-items: center;
        position: absolute;
        top: 39.5%;
        width: 21%;
        z-index: 1;
      }

      .spinner:not(.is-spinning) .wheel { animation-play-state: paused; }

      .pose {
        color: #25312d;
        font-family: system-ui, sans-serif;
        font-size: clamp(.63rem, 2.4vw, .96rem);
        font-weight: 750;
        left: var(--x);
        letter-spacing: .03em;
        line-height: 1.1;
        position: absolute;
        text-align: center;
        text-shadow: 0 1px 0 rgb(255 255 255 / .45);
        top: var(--y);
        transform: translate(-50%, -50%);
        width: 25%;
      }

      .pose span { display: block; font-size: 1.35em; margin-bottom: .2rem; }
      .status { font-family: system-ui, sans-serif; font-size: .92rem; margin: 1.7rem 0 0; }
      .spinner:focus-visible { outline: 4px solid var(--ink); outline-offset: 8px; }

      @keyframes spin { to { transform: rotate(360deg); } }
      @media (prefers-reduced-motion: reduce) { .wheel { animation-duration: 22s; } }
    </style>
  </head>
  <body>
    <main>
      <h1>Build a Flow</h1>
      <p class="subtitle">click the wheel to chose your next pose</p>

      <button class="spinner is-spinning" type="button" aria-label="Spinning yoga pose wheel. Click to stop." aria-pressed="true">
        <span class="pointer" aria-hidden="true"></span>
        <span class="wheel" aria-hidden="true">
          <span class="pose" style="--x: 62%; --y: 22%"><span>🐕</span>Downward<br>Dog</span>
          <span class="pose" style="--x: 78%; --y: 38%"><span>🧘</span>Warrior 2</span>
          <span class="pose" style="--x: 78%; --y: 62%"><span>✈️</span>Warrior 3</span>
          <span class="pose" style="--x: 62%; --y: 78%"><span>⛰️</span>Mountain<br>Pose</span>
          <span class="pose" style="--x: 38%; --y: 78%"><span>🛌</span>Shavasana</span>
          <span class="pose" style="--x: 22%; --y: 62%"><span>🐈</span>Cat / Cow</span>
          <span class="pose" style="--x: 22%; --y: 38%"><span>🌲</span>Tree Pose</span>
          <span class="pose" style="--x: 38%; --y: 22%"><span>🪑</span>Chair Pose</span>
        </span>
      </button>

      <p class="status" aria-live="polite">Spinning — click to stop</p>
    </main>

    <script>
      const spinner = document.querySelector('.spinner');
      const status = document.querySelector('.status');

      spinner.addEventListener('click', () => {
        const spinning = spinner.classList.toggle('is-spinning');

        spinner.setAttribute('aria-pressed', String(spinning));
        spinner.setAttribute(
          'aria-label',
          spinning
            ? 'Spinning yoga pose wheel. Click to stop.'
            : 'Yoga pose wheel stopped. Click to spin.'
        );

        status.textContent = spinning
          ? 'Spinning — click to stop'
          : 'Stopped — click to spin again';
      });
    </script>
  </body>
</html>
```
