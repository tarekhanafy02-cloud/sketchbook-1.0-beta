# testphysics

A browser driving game on a 5000 x 5000 m map: a blocky character, 10 parkable cars, 4 sports cars, a plane, a stunt area, crash damage (dents, torn-off bumpers and hood, a visible engine) and online multiplayer with Socket.IO.

## Controls
WASD move or drive, Shift run, Space jump or handbrake, E enter or leave a car or the plane, R repair your car, drag to look, scroll to zoom, Esc for the menu.
Plane: hold W to take off, Up/Down arrows climb or dive, A/D turn.

## Option 1: GitHub Pages (single player works straight away)
1. Push this folder to a GitHub repository (branch `main`).
2. In the repo go to **Settings > Pages** and set **Source** to **GitHub Actions**. The included workflow publishes the `public` folder.
3. Open `https://YOUR-NAME.github.io/YOUR-REPO/`. Single player works on its own.
4. For multiplayer, host the Node server somewhere (see Option 2), then put its **https** address in `public/config.js` (`window.SERVER_URL`), or type it into the Server address box on the Multiplayer screen.

## Option 2: Replit (or Render, Railway) runs the whole thing, multiplayer included
1. Create a Node.js Repl and import this repo (the `.replit` file must be at the top level), or upload the files.
2. Press **Run**. The server serves the game and the multiplayer. Share the link.
3. Locally: `npm install` then `npm start`, and open http://localhost:3000.

## Admin panel
Choose the name `tarek` or `bucket_birb11` on the main menu.
- **Single player:** you get the admin panel offline (announce, reset and repair all cars, teleports, paint all cars, spawn the admin car). Nothing is checked, it is just for testing.
- **Multiplayer:** the server decides who is an admin. You also get kick, bring and go-to for other players.
The panel opens with the "Admin panel" button (top right) or the backtick key.

Anyone can type those names while the real owner is offline, so set an `ADMIN_PASSWORD` environment variable (a Replit secret, for example). Once it is set, those names must enter the password to get admin online. Change the admin names with an `ADMINS` variable (comma separated).

## Notes
- Online, crashes and repairs are shared. Props and broken-off parts are not, so each player sees their own debris.
- Models live in `public/models` and load with relative paths, so the game works under any GitHub Pages sub-path.

## Admin car
In the admin panel, **Spawn admin car** puts a black box car with a jet engine next to you. It reaches 1405 km/h (0 to 100 km/h in under a second), cannot be damaged, and only admins can drive it. **Flight: ON/OFF** decides whether it can fly: with flight on, hold the Up arrow above 70 km/h to take off, then W/S throttle, Up/Down climb or dive and A/D bank. **Remove** puts it away. Online, it is shared with every player.

## Stunt park (Madalin-style)
North of the lot: kicker ramps with landing ramps, curved quarter-pipes, a mega ramp (26 m tall, with a landing ramp 100 m away), a spiral ramp that climbs 18 m (drive up it and jump off the top), loops and a giant sphere. West of the lot there is a stunt bowl, and east of the lot a train of four jumps. Loops, the sphere and the elevated track are scenery only.
The game shows an "early beta" banner at the top of the screen.
