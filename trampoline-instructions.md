# Finding the stack with 'jmp esp'

While working on a wargame with an otherwise ordinary remote buffer
overflow, I found myself having trouble finding the address of my
shellcode on the stack. Creating as large of a nopsled as I could fit
and probing memory address around what worked locally (or in gdb) were
all for naught. Thankfully a friend let me in on a secret: **jmp esp is
a valid instruction and is found in many binaries including libc**

Since esp points right under the recently popped return address,
returning to a 'jmp esp' instruction will jump back to the stack
(precisely the memory beneath the return address you just overwrote).
Even in a case like mine, where the number of writable bytes past the
return address is limited, it only requires a few instructions to
subtract from esp and then jump there again (back to the beginning of
your buffer).

Even nicer is that there exist tools that make searching binaries for
instructions, like 'jmp esp', trivially easy. For example in
[peda](https://github.com/longld/peda):


    gdb-peda$ ropsearch "jmp esp" libc
    Searching for ROP gadget: 'jmp esp' in: libc ranges
    0xf7f8ffff : (ffe4c2) jmp esp; ret 0x2;
    0xf7f8f367 : (ffe4730200f0c3) jmp esp; jae 0xf7f8f36d; add al,dh; ret;
    gdb-peda$
