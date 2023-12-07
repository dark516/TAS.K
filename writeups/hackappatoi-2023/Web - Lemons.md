# Web - Lemons
## Writeup Author: kebabulon

---

### Task

Perhaps not everyone knows that Italy produces top-quality lemons. No wonder that forgetting them at the counter is a very serious matter...  

https://lemons.hackappatoi.com 

![Lemons site](assets/images/Lemons_1.png)

---

### Solution


First of all I checked ```robots.txt```:

```
User-agent: *
Disallow: /flag

User-agent: AdsBot-Google
Disallow: /signora
```

We got 2 pages to check, lets start with ```/flag```

Well.. we do not talk about that (it was a rick roll)

Now lets try ```/signora```:

![/signora](assets/images/Lemons_2.png)

This is one of the ugliest websites I have ever seen.

---

### Flag

```
hctf{e4sy_p3asy_th3_lem0ns_mada4a4aam!} 
```
