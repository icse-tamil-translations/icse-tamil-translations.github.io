<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ICSE Tamil Translations</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background-color: #f5f5f7;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
        Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
      color: #1d1d1f;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      text-align: center;
    }

    h1 {
      font-size: 2.5rem;
      margin-bottom: 0.5rem;
    }

    h2 {
      font-weight: 400;
      color: #6e6e73;
      margin-bottom: 2rem;
    }

    .type-wrapper {
      font-size: 3rem;
      font-weight: 500;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 1rem;
      font-family: 'Latha', 'Noto Sans Tamil', sans-serif;
      min-height: 3rem;
    }

    .arrow {
      font-size: 2rem;
      color: #333;
    }

    .typing-text {
      min-width: 8ch;
      white-space: nowrap;
      overflow: hidden;
    }

    .button {
      margin-top: 3rem;
      background-color: #0071e3;
      color: white;
      padding: 0.75rem 1.5rem;
      border: none;
      border-radius: 0.5rem;
      font-size: 1rem;
      cursor: pointer;
      text-decoration: none;
      transition: background-color 0.3s ease;
    }

    .button:hover {
      background-color: #005bb5;
    }
  </style>
</head>
<body>
  <h1>ICSE Tamil Translations</h1>
  <h2>Hosting English translations of Sarithra Sambavangal and Veerapandiya Kattabomman</h2>

  <div class="type-wrapper">
    <div id="typing" class="typing-text"></div>
    <div class="arrow">↔</div>
    <div id="typing2" class="typing-text"></div>
  </div>

  <a href="https://icse-tamil-translations.github.io/" class="button" target="_blank">Visit Website</a>

  <script>
    const tamil = 'தமிழ்';
    const english = 'English';

    const typingEl1 = document.getElementById('typing');
    const typingEl2 = document.getElementById('typing2');

    let i = 0;
    let j = 0;
    let state = 'typingTamil';

    function typeLoop() {
      if (state === 'typingTamil') {
        typingEl1.textContent = tamil.substring(0, i);
        i++;
        if (i > tamil.length) {
          state = 'typingEnglish';
          i = tamil.length;
          j = 0;
          setTimeout(typeLoop, 500);
          return;
        }
      } else if (state === 'typingEnglish') {
        typingEl2.textContent = english.substring(0, j);
        j++;
        if (j > english.length) {
          state = 'clearingEnglish';
          setTimeout(typeLoop, 1000);
          return;
        }
      } else if (state === 'clearingEnglish') {
        typingEl2.textContent = english.substring(0, --j);
        if (j === 0) {
          state = 'clearingTamil';
          setTimeout(typeLoop, 300);
          return;
        }
      } else if (state === 'clearingTamil') {
        typingEl1.textContent = tamil.substring(0, --i);
        if (i === 0) {
          state = 'typingTamil';
        }
      }
      setTimeout(typeLoop, 100);
    }

    typeLoop();
  </script>
</body>
</html>
