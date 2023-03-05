# llama-dl

This repository contains a high-speed download of LLaMA, Facebook's 65B parameter model that was recently made available via torrent. (Discussion: [Facebook LLAMA is being openly distributed via torrents](https://news.ycombinator.com/item?id=35007978))

It downloads all model weights (7B, 13B, 30B, 65B) at around 200 MB/s:

![image](https://user-images.githubusercontent.com/59632/222940196-e763d8a0-2282-4f78-8bbe-14c559eea90f.png)


```
real    19m21.173s
user    3m30.473s
sys     2m30.847s
```

## Download

To download all model weights, `cd` into the directory you want them, then run this:

```sh
curl -o- https://raw.githubusercontent.com/shawwn/llama-dl/b093f5e3ad85a6437f40c4b20641e11f6955521d/llama.sh | bash
```

Running random bash scripts generally isn't a good idea, but I'll stake my personal reputation on the fact that this link is safe. (It points to a specific SHA-1 hash rather than https://raw.githubusercontent.com/shawwn/llama-dl/main/llama.sh so that it's still safe even in the event that my repo or account got compromised.)

## How do I know this is safe?

I ran this:

```
mkdir LLaMA
cd LLaMA
time curl -o- https://raw.githubusercontent.com/shawwn/llama-dl/b093f5e3ad85a6437f40c4b20641e11f6955521d/llama.sh | bash
cd ..
webtorrent 'magnet:?xt=urn:btih:b8287ebfa04f879b048d4d4404108cf3e8014352&dn=LLaMA&tr=udp%3a%2f%2ftracker.opentrackr.org%3a1337%2fannounce'
```

Webtorrent began seeding immediately, which means every file is identical to what you would've gotten via the torrent. So this is just a faster version of the torrent.

<img width="310" alt="image" src="https://user-images.githubusercontent.com/59632/222940942-0051a645-b561-4f0b-878c-3d195354d526.png">

<img width="310" alt="image" src="https://user-images.githubusercontent.com/59632/222941107-b4ef0b21-3fa7-40d1-ae56-cbe385e6ac00.png">

## How much faster?

Roughly 18x. As of March 4 2023, the torrent seems to download at around 11MB/s. Whereas this download script downloads at around 120MB/s on average, bursting occasionally up to 220MB/s.

<img width="300" alt="image" src="https://user-images.githubusercontent.com/59632/222940992-f037b12c-c077-4136-8960-b2b1667ddc79.png">

## Will I get in trouble for using this download link?

I doubt it. This is the download link that was leaked in the original torrent. (i.e. the leaker accidentally leaked their own unique download link that Facebook sent them.)

Technically, it may be illegal to knowingly use a private download link that was intended for someone else. Realistically, Facebook would risk their ML reputation by going after people who are merely trying to use what they themselves advertise as "open source."

## Final thoughts

I was shocked that this script was distributed with the original torrent, and that no one seemed to notice (a) that it still works, and (b) is almost 20x faster than the torrent method. I was impatient and curious to try to run 65B on an 8xA100 cluster, so I didn't want to wait till tomorrow and started poking around, which is when I found this. I decided to just tweet it out and let you, fellow scientists and hackers, enjoy it before Facebook notices and shuts it off.

"Power to the people" is an overused trope, but as a research scientist, I feel it's important to let individual hackers be able to experiment with the same tools, techniques, and systems that professional ML researchers are fortunate to have access to. This is a tricky situation, because at some point between now and 10 years from now, this might become dangerous -- AI alarmists often ask "Would you want random people experimenting with nuclear weapons in their basement?" My answer is "No, but we're not there yet."

Word on Twitter is that LLaMA's samples seem worse than GPT-3 by a large margin, but then I realized no one has really been able to try the full 65B model yet, for a combination of reasons. (Mostly lack of access to 8xA100 hardware.) So I decided to try it out for myself and see.

Even if it's GPT-3 level, the fact is, LLaMA is already openly available. The torrent isn't going anywhere. So my own thoughts on this are mostly irrelevant; determined hackers can get it themselves anyway.

But for what it's worth, my personal opinion is that LLaMA probably isn't OpenAI-grade -- there's a big difference between training a model in an academic setting vs when your entire company depends on it for wide-scale commercial success. I wasn't impressed that 35B didn't seem to know who Captain Picard was.

People have already started decrying this leak as dangerous. But everyone used to say the same thing about 1.5B. (In fact, the allure of 1.5B's grandiose claims was what drove me to take ML seriously in 2019.) Turns out, four years later, no one really cares about 1.5B anymore, and it certainly didn't cause wide-scale societal harm. I doubt LLaMA will either.

2023 will be interesting. I can't wait for 2024.

Signed with love,

Shawn Presser

twitter: [theshawwn](https://twitter.com/theshawwn)

HN: [sillysaurusx](https://news.ycombinator.com/user?id=sillysaurusx)


