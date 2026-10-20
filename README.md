# Ultrasonic Chirp Pong (>20 kHz)

🎮 **Play Live on GitHub Pages:** **[https://iamvinit.github.io/chirp-pong/](https://iamvinit.github.io/chirp-pong/)**

A two-player competitive paddle game where two phones pair and exchange the ball through **inaudible ultrasonic sound waves (>20 kHz)** using each phone's speaker and microphone, without Wi-Fi, Bluetooth, or user accounts.

---

## 📌 Provenance & Attribution

This project is an ultrasonic adaptation of **[Chirp Pong](https://tools.simonwillison.net/chirp-pong)**, originally created by **Simon Willison** in the **[simonw/tools](https://github.com/simonw/tools/blob/main/chirp-pong.html)** repository ([colophon documentation](https://tools.simonwillison.net/colophon#chirp-pong.html)).

The original game used audible FSK chirps in the ~1.5 kHz – ~4 kHz range.

---

## 🦇 Ultrasonic (>20 kHz) Modifications

1. **Carrier Frequencies Shifted Above 20,000 Hz**:
   - **Player 1 (Band A)**: 16 discrete FSK tones spanning `20,100 Hz` to `21,375 Hz` (85 Hz tone spacing at 48 kHz sample rate).
   - **Player 2 (Band B)**: 16 discrete FSK tones spanning `21,600 Hz` to `22,875 Hz` (85 Hz tone spacing).
   - **44.1 kHz Sample Rate Clamping**: If a device locks `AudioContext` at 44.1 kHz (where the Nyquist limit is 22,050 Hz), carrier tones automatically clamp to `20,050–21,700 Hz` (50 Hz spacing) to prevent aliasing.
   - **Near-Ultrasonic Fallback (`17.5–19.9 kHz`)**: A selectable fallback mode is included for smartphone microphones that have aggressive analog low-pass filters above 20 kHz.

2. **Click-Free Raised Envelope Shaping**:
   - Abruptly starting and stopping high-frequency sine waves causes audible sub-20 kHz click transients due to impulse harmonics. A 6 ms linear gain envelope was implemented on all bursts to keep transmissions completely inaudible to human ears.

3. **High-Resolution FFT & Raw Audio Capture**:
   - Browser voice DSP (`echoCancellation`, `noiseSuppression`, and `autoGainControl`) is explicitly disabled to avoid filtering out ultrasonic audio.
   - The receiver utilizes an 8,192-point FFT (~5.86 Hz bin resolution at 48 kHz) to detect tone peaks with high SNR.
   - Differential 16-FSK symbol transitions ensure reliable clock and edge recovery without a shared network clock.

---

## 🕹️ Game Features

- **📱📱 Play on Two Phones**: Pair two phones over sound. Lay them top-to-top, tap *Call* on one phone, and the other phone answers automatically.
- **🤖 Practice vs CPU**: Play offline against an AI opponent with ultrasonic or silent chirps.
- **🔬 2-CPU Modem Sim (`#sim`)**: Watch two CPU players duel over the real audio modem and simulated room acoustics.
- **Match Lengths**: Play first to 7, 11, or 15 points.
- **Spin & Smashes**: Swipe sideways as you hit to impart curve spin that carries over to the opponent's screen. Flick upward into the ball to trigger a high-velocity SMASH.
- **Trick Gems**: Hit gems on your court to trigger effects on the other phone when the ball arrives:
  - 🔥 **BLAZE**: Ball travels 45% faster trailing fire.
  - 👻 **PHANTOM**: Turns invisible in the middle of their court.
  - 🔱 **MIRAGE**: Splits into 3 balls (only 1 is real).
  - 💣 **BOMB**: Drops a bomb on their court that stuns their paddle.
  - 🌀 **VORTEX**: Spawns a black hole bending the ball's trajectory.
  - 🔄 **MIRROR**: Reverses their left/right paddle controls.
  - 🐜 **SHRINK**: Shrinks their paddle to half size.
- **Rally Heat**: Rallies of 6+ hits award ×2 points; rallies of 12+ hits award ×3 points.
- **Aimed Bombs**: Build up your bomb meter on returns; tap anywhere on the court while the ball is away to drop an aimed bomb onto their screen.

---

## 🚀 Hosting & Deployment

This repository is hosted via **GitHub Pages**. Any updates to `index.html` on the `main` branch are automatically deployed.
