# Generative Music Tools

Two browser-based generative music tools inspired by **Alvin Lucier** and **Éliane Radigue**.

Built with the Web Audio API. No server required, no dependencies, no installation. Open `index.html` in any modern browser and it works.

→ **[Read the article](https://www.jordanelias.de/blog/generative-music/)** for the full context: the history and philosophy behind both composers, the physics of room acoustics, and the connections between generative music and psychotherapy.

---

## How to use

**Option 1 — use it live**
Visit the hosted version at [jordanelias.de/blog/generative-music/](https://www.jordanelias.de/blog/generative-music/) — the tools are embedded directly in the article.

**Option 2 — download and open locally**
Click the green **Code** button → **Download ZIP**. Unzip it, open `index.html` in Chrome, Firefox, or Safari. No internet connection required after the initial page load (Google Fonts will be absent offline but everything else works).

**Option 3 — clone the repo**
```bash
git clone https://github.com/jordan-elias/generative-music-tools.git
cd generative-music-tools
open index.html
```

---

## The tools

### Lucier: iterative room processing

Inspired by *I Am Sitting in a Room* (1969). Choose either the generated voice, an uploaded audio file, or a direct microphone recording. Each time you press **+ iterate**, the audio passes through a bank of resonant bandpass filters modelling a room's modal frequencies. The room reinforces certain frequencies and attenuates others. Each iteration squares that effect. After 8–15 passes, speech or noise transforms into sustained tones determined by the room's geometry rather than the original content.

Volume is normalised after each iteration so the output stays consistently audible regardless of how many passes you run.

Features:
- Generated voice, file upload (any browser-supported format), or microphone recording (up to 6 seconds)
- Loop mode for continuous playback of any iteration
- Iteration counter and status display
- Download as WAV: select from/to iteration, number of loops, renders offline

### Radigue: evolving drone

Inspired by the drone compositions of Éliane Radigue. Two or three sine wave oscillators slightly detuned from each other produce slow beating at their difference frequencies. Each oscillator has its own LFO running at a slightly different rate, so the beating patterns drift continuously over time. The sound changes too slowly to notice moment to moment but is clearly different after several minutes.

Features:
- Base frequency, detuning, drift rate, noise floor, and volume controls
- 2 or 3 oscillator mode
- Live frequency readout (monospaced for layout stability)
- Download as WAV: 1, 3, 5, 10, or 20 minutes. The LFO drift is modelled in the offline render

---

## Try it in a real room

The physical version of the Lucier process requires only two devices. Record yourself speaking on one. Play that recording back in a room and record it on a second device. Play the second recording and record it on the first device again. Repeat four or five times. Each pass through the real room reinforces its resonant frequencies. Positioning matters — placing the microphone near a wall or corner emphasises room modes more strongly. Different rooms (bathroom, stairwell, large hallway) produce completely different results from the same source material.

---

## Technical notes

- `OfflineAudioContext` is used for iteration processing and WAV export
- WAV export is 16-bit mono (Lucier) or stereo (Radigue) at 44100 Hz
- Pink noise is generated using Paul Kellet's algorithm
- No external JavaScript libraries

---

Use freely, modify freely, credit appreciated.

## About

Made by [Jordan Elias](https://www.jordanelias.de) — music therapist, researcher, and educator based in Berlin.
