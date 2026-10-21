# Baat — English phrases with Hindi meanings

Flashcards and a searchable phrasebook for Mummy, for talking with her Swedish daughter-in-law at home and while
travelling through India to family in the mountains. Front: the English phrase with how to say it
in Devanagari, e.g. **How are you?** *हाउ आर यू?*. Back: the Hindi meaning, `तुम कैसी हो?`. The
topic is shown top-left on each card.

The app is a PWA (web app) you install on your phone from the browser. It works offline.

## The phrases

The 395 phrases are in `docs/phrases.json`, one per line:

```json
["How are you?", "हाउ आर यू?", "तुम कैसी हो?", "नमस्ते · Hello & welcome"]
```

`[English, pronunciation, Hindi, topic]`. They are grouped into 23 topics: welcome, talking,
family, food, at the table, at home, taking care, health, travel, the mountains, visiting family,
temple & customs, festivals, shopping, compliments, goodbyes and so on. The speaker is Mummy (a woman:
*गई हूँ*, *दूँगी*), talking to her daughter-in-law (*तुम*, *थक गई हो?*). The English is short and
simple, the way it's actually spoken.

*वो कहेगी · You'll hear* has things the daughter-in-law is likely to say, so Mummy can recognise them.
*थोड़ी स्वीडिश · A little Swedish* has a few Swedish words to surprise her with; those lines have a
5th field, `"sv"`, so 🔊 reads them with a Swedish voice.

To add a phrase, add a line. The English must be unique: it's how the app remembers what's learnt.

## Try it on your computer

```sh
python3 -m http.server -d docs 8000   # open http://localhost:8000
```

## Put it on your phone

1. Commit and push to GitHub.
2. On GitHub: **Settings → Pages → Source: Deploy from a branch → `main` / `/docs`** → Save
   (the repo must be public on a free account).
3. On the phone, open `https://kund17.github.io/hinglish/`.
   - **Android (Chrome):** tap **⬇ Baat को ऐप की तरह इंस्टॉल करें**, or menu (⋮) → **Install app**.
   - **iPhone (Safari):** Share ⬆︎ → **Add to Home Screen**.

The app saves itself on the phone on the first visit and then works fully offline. After you push
changes, bump `CACHE` in `docs/sw.js` and open the app once while online; the update appears the time after that.

## Using the app

- **कार्ड · Cards / सूची · List** switches between flashcards and the phrasebook. The dropdown picks
  a topic or *सभी विषय · All topics*.
- **Cards:** tap the card to flip it. **← पीछे** / **आगे →** move through the phrases. **याद है ✓**
  hides the phrase for good (saved on the phone); **✓ याद हुए** lists them, with **↩ वापस** and
  **सब वापस लाएँ**. 🔀 shuffles.
- **List:** every phrase in the topic, with a search box that matches English, Hindi or the
  pronunciation. Handy for finding a phrase mid-conversation, or for showing her the screen.
- 🔊 says the phrase out loud in English (an Indian English voice if the phone has one).

## Icon

`docs/poppy.svg` is a Himalayan blue poppy on dark green. The PNGs are rendered from it with headless Chrome:

```sh
cd docs && for s in 512 192 180; do
  echo "<body style='margin:0'><img src='file://$PWD/poppy.svg' width=$s height=$s>" > /tmp/icon.html
  "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --hide-scrollbars \
    --allow-file-access-from-files --window-size=$s,$s --screenshot="$PWD/poppy-$s.png" file:///tmp/icon.html
done
```

## Copyright

© 2026 Kunal Deoskar. All rights reserved. See [LICENSE](LICENSE).
