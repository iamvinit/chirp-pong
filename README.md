# Chirp Pong — Ultrasonic (>20 kHz) & Audible FSK Edition

🎮 **Live GitHub Pages URL:** **[https://iamvinit.github.io/chirp-pong/](https://iamvinit.github.io/chirp-pong/)**

A real-time two-player paddle game where two phones pair and exchange the ball back and forth **carried solely by sound waves** using each phone's microphone and speaker — no Wi-Fi, Bluetooth, local network, or user accounts required.

---

## 📌 Provenance & Attribution

This project is a standalone enhanced edition of **[Chirp Pong](https://tools.simonwillison.net/chirp-pong)**, originally designed and built by **[Simon Willison](https://simonwillison.net/)** in the **[simonw/tools](https://github.com/simonw/tools/blob/main/chirp-pong.html)** repository ([colophon notes](https://tools.simonwillison.net/colophon#chirp-pong.html)).

The core acoustic modem architecture was created by Simon Willison, featuring:
- Differential 16-ary Frequency Shift Keying (FSK) with a 100 ms sync preamble and CRC-8 integrity verification.
- Real-time sliding Goertzel filters with Hanning windowing for sample-accurate tone demodulation.
- Stop-and-wait reliable link protocol with ACKs and retry timers.
- Two-player synchronized physics, swipe-induced Magnus effect curve spin, flick smashes, aimed bomb drops, heat multipliers, and 7 collectible trick gems.

---

## ⚡ Frequency Modes

You can select the active transmission frequency profile directly on the title screen or in the lobby:

1. **🔊 Audible FSK (1.4 – 5.0 kHz) — [Simon's Original]**:
   - Band 0 (Player 1 / Caller): `1,406 Hz` to `3,000 Hz`
   - Band 1 (Player 2 / Answer): `3,375 Hz` to `4,969 Hz`
   - **Recommended for first test**: Audibly verify chirps and acoustic pairing on any phone, tablet, or laptop.

2. **🦇 Near-Ultrasonic (16.5 – 19.9 kHz)**:
   - Band 0 (Player 1): `16,500 Hz` to `18,094 Hz`
   - Band 1 (Player 2): `18,281 Hz` to `19,875 Hz`
   - Inaudible or faint to adult human ears while remaining within the high-sensitivity passband of standard smartphone microphones and speakers.

3. **⚡ Strict Ultrasonic (>20 kHz)**:
   - Band 0 (Player 1): `20,062 Hz` to `21,656 Hz`
   - Band 1 (Player 2): `21,844 Hz` to `23,438 Hz`
   - Strictly above the nominal human hearing threshold (20,000 Hz). Requires 48 kHz Web Audio hardware support.

---

## 📱 How to Play & Pair

### Option A: Acoustic Auto-Pairing (Sound Handshake)
1. Open **[https://iamvinit.github.io/chirp-pong/](https://iamvinit.github.io/chirp-pong/)** on **both** phones.
2. Turn the media volume **all the way up** (ensure silent/vibrate switch is off).
3. Tap **Play on two phones** on both devices.
4. Place the phones **top-to-top**, approximately 2–5 cm apart on a table.
5. Tap **📣 Call other phone** on **ONE** phone only.
6. The calling phone will chirp `HELLO`; the other phone will detect it, reply with `WELCOME`, and both courts will immediately launch!

### Option B: Instant Manual Start (Direct Duel Override)
If ambient room noise is high or microphones are hardware-filtered:
1. On Phone 1, tap **🔵 P1 Force**.
2. On Phone 2, tap **🔴 P2 Force**.
3. Both phones start playing immediately in synchronized duel mode, with ball crossings transmitted over audio.

---

## 🕹️ Controls & Mechanics

- **Paddle Movement**: Drag anywhere on the court. The paddle floats just above your finger.
- **Angle Control**: Hit with the edge of the paddle to deflect the ball at sharp angles.
- **Spin**: Swipe sideways across the paddle on contact to impart spin (Magnus effect curves the ball in flight).
- **Smash**: Flick sharply upward into the ball to trigger a 135% speed SMASH.
- **Trick Gems**: Strike gems that spawn on the court to trigger effects on your opponent's screen:
  - 🔥 **BLAZE**: Ball accelerates 45% faster trailing fire.
  - 👻 **PHANTOM**: Turns invisible through mid-court.
  - 🔱 **MIRAGE**: Splits into three balls (only one is real).
  - 💣 **BOMB**: Drops a bomb on their court that stuns their paddle.
  - 🌀 **VORTEX**: Opens a black hole bending trajectory.
  - 🔄 **MIRROR**: Inverts opponent's left/right controls.
  - 🐜 **SHRINK**: Halves opponent's paddle size.
- **Rally Heat**: Rallies of 6+ hits award ×2 points; rallies of 12+ hits award ×3 points.
- **Aimed Bombs**: Build up your bomb meter on returns; tap anywhere on your court while the ball is away to drop an aimed bomb onto their screen.

---

## 🔬 Single-Browser Testing

To test the audio modem directly on a single computer without two phones:
- Navigate to **[https://iamvinit.github.io/chirp-pong/#sim](https://iamvinit.github.io/chirp-pong/#sim)**.
- This boots the simulated room environment with two virtual phones playing against each other via the real Goertzel FSK modem with simulated acoustic reverberation and transmission delay.
