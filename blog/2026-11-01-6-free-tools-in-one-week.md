# I'm a BCA student from Dumka. I shipped 6 free tools in one week — with AI as my pair programmer

*By Anish ([@heyyanixx](https://github.com/heyyanixx)) · 1 November 2026 · ~6 min read*

![Cover: 6 free tools in one week — built in public](https://raw.githubusercontent.com/heyyanixx/heyyanixx/main/blog/cover.png)

I'm Anish. I'm in my first semester of BCA (AI) through VGU Online, I live in Dumka, Jharkhand, and until last month most of my "tech" life was editing Free Fire Shorts and making AI visuals for my Instagram.

I've only just started learning C. I'm not going to pretend otherwise.

But in the last week I put six free things on the internet that people can actually use. This post is the honest version of how that happened — what I built, how much of it was AI, what broke, and what I learned.

## What I shipped

All of these are free, work in the browser, and are live right now:

1. **[Full ADCA Tools](https://heyyanixx-tools.sites.tab.bot/)** — an office suite for students who don't have a laptop with paid software: a word processor, a spreadsheet with formulas and charts, slides, a small database, a PDF toolkit, plus an image editor, YouTube thumbnail maker, video trim/MP3/GIF and an in-browser OCR. Everything runs on your device; nothing is uploaded.
2. **[Learn Arcade](https://heyyanixx-learn.sites.tab.bot/)** — learning as games: typing practice, commerce/GST basics, Sarkari GK, and a video-editing zone. Because revision is easier when it feels like a game.
3. **[Notes AI](https://heyyanixx-notes.sites.tab.bot/)** — notes for students who are stressed about notes (me and my friends): a ready offline library of exam topics, plus tools to turn a pasted transcript, a photo or a PDF into short notes, flashcards and a quick quiz.
4. **[PayPoster](https://github.com/heyyanixx/payposter)** — my first proper open-source repo. Type your UPI ID, pick a style, and get a clean QR poster (Story, Square or A4) and a shareable pay link. Made for chai stalls, college fest desks, creators and friends splitting a bill. MIT licensed. → [live demo](https://heyyanixx-payposter.sites.tab.bot/)
5. **[HEYYANIXX app](https://github.com/heyyanixx/heyyanixx-app)** — an Android app (and PWA) that opens all of the above in one place, with some games that work offline.
6. **[One links page](https://heyyanixx-links.sites.tab.bot/)** — because "link in bio" should be one link.

## The honest part: how much was AI?

A lot. I'll say it plainly, because I think hiding it would be the cringe move in 2026.

I used an AI assistant that can write code, run it, test it in a real browser and publish it. My job was the part AI can't do for me:

- **Choosing the problem.** Every tool here started from something I see around me: lots of small shops still have a faded photo of a bank QR on the counter, many students don't have paid office software on a laptop (or a laptop at all), and notes stress is real — for me and for the kids I know.
- **Saying what "good" means.** Black and gold, Hinglish where it helps, must work on a ₹10k phone, no fake buttons — if something isn't built yet it says "Coming soon".
- **Testing like a user.** Opening it on my phone, breaking it, sending screenshots of what looked wrong.
- **Saying no.** Features that sounded cool but nobody would use got cut.

That is still building. It's just building at a different layer. And I'm learning the code underneath by reading it — PayPoster is small enough that I can follow every file.

## What I learned shipping PayPoster

PayPoster is the one I'm proudest of, because it's open source and small enough to explain.

**1. A UPI QR is just a link.** Every UPI QR code contains a link like this:

```
upi://pay?pa=yourname@okaxis&pn=Your%20Name&am=49.00&cu=INR&tn=Chai
```

`pa` is the UPI ID, `pn` the name, `am` the amount, `tn` the note. Encode that text into a QR and any UPI app can read it. Once I understood that, the whole tool made sense.

**2. Tests matter more than looks.** A pretty poster with a QR that doesn't scan is worse than useless — someone prints it, sticks it on a counter, and loses customers. So the project has a browser test that generates every style in every size and then *decodes the QR back* with OpenCV to check it says exactly the right thing. All of them pass. I also gave the QR a wide white border (the "quiet zone") so it still scans when printed small.

**3. Small decisions are the real product.** When you split ₹1000 between 3 people, is it ₹333.33 each? Then you collect ₹999.99 and someone is short a paisa. PayPoster rounds *up* (₹333.34) and tells you the total you'll actually collect. Nobody will notice that detail — until it's wrong.

**4. Privacy is a feature you can explain in one line.** "Nothing is uploaded" is easy to say when there is no server. PayPoster is just HTML, CSS and JavaScript. The pay link keeps your details in the part of the URL after `#`, which browsers don't send to any server.

**5. Being honest in the FAQ builds trust.** Some UPI apps ignore the pre-filled amount for personal UPI IDs. I could hide that. Instead the FAQ says it, and says that the payer should always check the name their app shows before paying.

## What didn't go well

- **I built too much, too fast, and told too few people.** Six things in a week and almost nobody knows they exist. That's why I'm writing this.
- **Some features depend on the phone.** The on-device AI parts (OCR, transcripts, notes from audio) are slow or don't run on older phones. Those tools say so instead of pretending.
- **My own coding skills are behind my projects.** I'm fixing that the slow way: my BCA C lab programs, and reading the code of my own tools.

## What's next

- **Build in public, every day.** Short reels on Instagram and YouTube showing one tool at a time — what it does in 30 seconds.
- **Make PayPoster better with other people.** New poster styles (Diwali, minimal white), a logo on the poster, and "counter cards" for fixed amounts. If you've never made an open-source contribution, a new poster style is a perfect first PR — it's one object in one file.
- **Learn C properly** and write about that journey here too.

## If you want to help

- ⭐ Star [PayPoster on GitHub](https://github.com/heyyanixx/payposter) if you find it useful — it genuinely helps other people discover it.
- Try the [tools](https://heyyanixx-tools.sites.tab.bot/) on your phone and open an issue if something breaks.
- Share PayPoster with one shopkeeper or fest organiser you know.

And if you're a student who thinks you're "not technical enough" to ship something: you probably are. Start with one real problem you see every day. The rest is learning in public.

— Anish · [GitHub](https://github.com/heyyanixx) · [Instagram](https://www.instagram.com/heyyy.anixx_/) · [YouTube](https://www.youtube.com/@smart_anish69)
