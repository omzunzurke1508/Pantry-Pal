# PantryPal — your kitchen, your next meal

PantryPal is a beginner-friendly recipe helper. It stores preferences, pantry ingredients, saved recipes, and the shopping list in your browser. Its optional chat helper uses a small private server so the secret key never goes into browser files.

## Start here

1. Install **Node.js LTS** from [nodejs.org](https://nodejs.org/) and **Visual Studio Code** from [code.visualstudio.com](https://code.visualstudio.com/). Restart your computer if the installer asks.
2. Open VS Code. Choose **File → Open Folder…** and open the `pantrypal` folder.
3. Open a terminal in VS Code: choose **Terminal → New Terminal** from the menu.
4. Copy and paste these commands in the terminal:

   ```powershell
   npm install
   npm install --prefix client
   npm install --prefix server
   npm run dev
   ```

5. Open the address printed by Vite, usually `http://localhost:5173`.
6. To stop the app, click the terminal and press **Ctrl+C**.

The first two minutes can take a little longer while Node.js downloads the app's helper packages. Keep the terminal window open while PantryPal is running.

## What is in the folders?

- `client/` contains the screens you see in your browser, the style rules, and the recipe collection.
- `server/` contains the small helper program that keeps the AI key out of the browser.
- `client/src/recipes.json` holds 25 starter recipes. Edit it to add or change recipes.
- `.env.example` shows the optional secret settings. Copy it to a file named `.env` in the main `pantrypal` folder before adding a key. Never share `.env` or post it online.

## Optional AI chat key

The app works without a key. Chat then uses its friendly quick-help response and local keyword actions. For smarter replies, create an API key in your OpenAI account's API key settings at [platform.openai.com/api-keys](https://platform.openai.com/api-keys). API usage may cost money; check your account's current pricing and usage limits before making requests.

In VS Code, open the main `pantrypal` folder. Copy `.env.example`, paste the copy next to `package.json`, and rename the copy to `.env` (the name starts with a dot). Open `.env` and replace `paste_your_secret_key_here` with your key. Save, stop the running app with **Ctrl+C**, then run `npm run dev` again. Do not put the key in a file inside `client/` or share a screenshot of `.env`.

## Voice

Press **Enable voice**, approve the microphone prompt, and say “Hey Pantry” followed by a command. Examples include “open my shopping list”, “what can I cook in 20 minutes”, “add eggs to my pantry”, and “start a timer for 10 minutes”. Voice uses the browser's built-in speech features; Chrome or Edge is recommended. Microphone access typically requires a secure page (HTTPS) or `localhost`. Audio is not saved by PantryPal. Browser speech recognition support and permission rules vary; the app displays an explanation if it is unavailable or permission is denied.

## Walkthrough video

The animated eight-part walkthrough plays automatically on the home screen. To replace it with your own video, put an MP4 named `walkthrough.mp4` in `client/public/`. If the file is present, PantryPal displays the video in the tour's video area; the captions and slideshow remain available beneath it.

## What to try

- Add ingredients to your pantry and make a plan for a chosen time and serving count.
- Set an allergy or avoided food and confirm recipes containing it disappear.
- Open a recipe, change its serving count, then add its missing ingredients to the shopping list.
- Check off or delete shopping items; heart a recipe and find it under Saved.
- Refresh the page and confirm your browser has remembered your details.
- On the home page, pause, resume, and skip through the tour; try the floating chat and the voice button.

## Put it online for free

The client can be published to a static host such as Netlify or Vercel. The optional Express chat server also needs a Node-capable host; deploy it separately and set `OPENAI_API_KEY` as a private environment variable in that host's settings. Configure the client's `/api` proxy for the deployed server URL (the local Vite proxy is only for your own computer). Browser data remains in each visitor's own browser and does not transfer between devices. Free hosting plans and features change, so check the host's current terms before publishing.

## Ideas for later

1. Add a recipe search box and ingredient substitutions.
2. Let people scan pantry labels with their camera.
3. Add nutrition estimates with clear source notes.
4. Sync favorites across devices with optional accounts.
5. Add more cuisines, regional measurements, and seasonal recipes.

## Plain-English guide to the code

React is the tool that redraws a screen when you tap a button. Vite serves the screens while you work and creates the publishable files. The browser's local storage is a small private shelf in that browser for this app's saved choices. The Node server handles optional AI requests; it reads the secret key from `.env` on your own computer, not from the page shown to visitors.
