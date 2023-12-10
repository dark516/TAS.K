# Rev - The four horsemen
## Writeup Author: kebabulon

---

### Task

The Cavaliere is retured. He is awake and he's ready to unleash the apocalypse. Are you the chosen one? Solving this challenge will give you the access to the war against the four horsemen. Be ready.

Attached file:
```
thehorsemen
```

---

### Solution

It's an executable, let's run it:

```
You are walking home, and on the pathway you find an old laptop. With a sticky note on it. That's what you read:

 12/06/2024
A year has passed. But now  he is awake. The greatest, the Cavaliere, the horseman. And he is ready to unleash the apocalypse.

You open that laptop and all you see is a prompt for a password. But you have NO WAY to know the password. On the other hand you are a great reverse engineer
Insert the password
>TAS.K
The password is wrong, the laptop begins ticking and then you see a blinding flash.
That's the last thing you see.
GAME OVER.
```

Well, we do not know the password.  
Let's try using ```strings```:

```
/lib64/ld-linux-x86-64.so.2
__cxa_finalize
__libc_start_main
puts
__isoc99_scanf
putchar
__stack_chk_fail
printf
libc.so.6
GLIBC_2.7
GLIBC_2.4
GLIBC_2.34
GLIBC_2.2.5
_ITM_deregisterTMCloneTable
__gmon_start__
_ITM_registerTMCloneTable
PTE1
u+UH
upgs{lbhH
er_ernqlH
_gb_fgbcH
_gur_ncbH
pnylcfr}H
Insert the password
The password is wrong, the laptop begins ticking and then you see a blinding flash.
That's the last thing you see.
GAME OVER.
You have successfully unlocked the mysterious laptop.
You open a file you find a key:
And next to the key you find the number %d.
You are walking home, and on the pathway you find an old laptop. With a sticky note on it. That's what you read:
12/06/2024
A year has passed. But now  he is awake. The greatest, the Cavaliere, the horseman. And he is ready to unleash the apocalypse.
You open that laptop and all you see is a prompt for a password. But you have NO WAY to know the password. On the other hand you are a great reverse engineer
:*3$"
GCC: (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0
.shstrtab
.interp
.note.gnu.property
.note.gnu.build-id
.note.ABI-tag
.gnu.hash
.dynsym
.dynstr
.gnu.version
.gnu.version_r
.rela.dyn
.rela.plt
.init
.plt.got
.plt.sec
.text
.fini
.rodata
.eh_frame_hdr
.eh_frame
.init_array
.fini_array
.dynamic
.data
.bss
.comment
```

And theres the flag:

```
...
upgs{lbhH
er_ernqlH
_gb_fgbcH
_gur_ncbH
pnylcfr}H
...
```

Cleaned up:

```
upgs{lbher_ernql_gb_fgbc_gur_ncbpnylcfr}
```

And after doing ROT13, we get the flag.

### Flag

```
hctf{youre_ready_to_stop_the_apocalypse}
```

