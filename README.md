# Fokus

A Pomodoro timer with a task list, written in plain HTML, CSS and JavaScript. Pick a task, run a focus session, and when the timer ends the task is marked as done. Tasks are saved in the browser, so they are still there after a reload.

**Live demo:** [fokus-jet.vercel.app](https://fokus-jet.vercel.app)

## What it does

- **Three timer modes.** Focus (30 minutes), short break (5) and long break (15). Switching mode changes the time, the page theme (through a `data-contexto` attribute on `<html>` that the CSS reads), the illustration and the headline.
- **Start and pause** with sound cues, and an optional looping background track you can toggle.
- **Task list.** Add tasks, click one to make it the active task, and rename it with the edit button. Everything is stored in `localStorage` and loaded back on startup.
- **Finishing a session.** When a focus timer reaches zero, the script dispatches a custom `FocoFinalizado` event on `document`. The task code listens for it and marks the active task as complete, which keeps the timer in `script.js` and the tasks in `script-crud.js` separate.
- **Cleanup.** Buttons remove only completed tasks or all of them.

The interface is in Portuguese.

## Run it

Asset paths start with `/` (for example `/imagens/...` and `/sons/...`), so the page has to be served from a web root. Opening `index.html` directly from disk will not find the images and sounds.

```bash
git clone https://github.com/victorhubarb/fokus.git
cd fokus
python3 -m http.server 8000     # then open http://localhost:8000
```

## Project structure

```
index.html
script.js        Timer, modes, audio
script-crud.js   Task list and localStorage
styles.css
imagens/, sons/
```

## Known gaps

- Changing the mode while the timer is running does not stop the countdown.
- The end of a session uses `alert()`.
- Renaming a task uses `prompt()`, and there is no way to delete a single task, only completed ones or all of them.
- Only one breakpoint set of responsive rules, so very small screens are not tuned.

---

Victor Hugo Barbosa · [GitHub](https://github.com/victorhubarb) · [LinkedIn](https://www.linkedin.com/in/victorhbarbosa/)
