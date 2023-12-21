# Crypto - Scrambled
## Writeup Author: kebabulon

---

### Task

Шреддеры - самая ужасная вещь на свете! Я случайно кинул туда свой листочек с паролем, и теперь не могу вспомнить, какой он был... Поможете?

**scrambled.zip**:
```
-- scrambled.zip
   |-- file0.png
   |-- file1.png
   |-- file2.png
   |-- file3.png
   |-- file4.png
   |-- file5.png
   |-- file6.png
   |-- file7.png
   |-- file8.png
   |-- file9.png
   |-- file10.png
   |-- file11.png
   |-- file12.png
```

---

## Solution

Every image has text on it.  
The text on the image ```file12.png``` is ```Cg==```, which tells us that the flag is base64 encoded.

Let's extract all the text out and base64 decode it:

```
n, it's very
ss0rs_4r3_th
te it to you
 hard to wri
3_b3st_t00l_
f0r_CTF!!1!}
JOHN! Don't
forget the p
of paper! It
assword agai
's
flag{sc1
 on a piece
```

Well it's all scrambled. Of course it is.

Unscrambled:

```
JOHN! Don't forget the password again, it's very hard to write it to you on a piece
of paper! It's flag{sc1ss0rs_4r3_th3_b3st_t00l_f0r_CTF!!1!}
```

---

### Flag

```
flag{sc1ss0rs_4r3_th3_b3st_t00l_f0r_CTF!!1!}
```
