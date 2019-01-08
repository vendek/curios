# CuriOS

> **cur·​ios** (ˈkjuːɹiːˌo͡ʊs) **_pn._** objects considered novel, strange, or interesting; curiosities

CuriOS is an experimental OS drawing inspiration from [TempleOS](https://www.templeos.org/), [gittup](http://gittup.org/gittup/), [TCCBOOT](https://bellard.org/tcc/tccboot.html), [Nebulet](https://github.com/nebulet/nebulet), [NixOS](https://nixos.org/), and [Singularity](https://www.microsoft.com/en-us/research/project/singularity).
CuriOS has several ambitious (maybe impossible—we'll find out!) goals, here listed roughly in order of palatability for a ~~mere mortal~~ normal human:

- Memory safety without an MMU is achieved by mandating all code is written in safe Rust (effectively, unsafe code is root). Barring serious bugs in rustc, it is impossible to even get a raw pointer, let alone poke & peek other applications' memory.
- There is no shell. The way the user interacts with the computer is by writing Rust. This may be as simple as calling `app::run()` or as complex as booting with nothing but a prompt like an Apple ][.
- No attempt is made at compatibility with previous systems. All code is clean-slate (or at least blurring the lines between a port and a reimplementation).
- There should be Only One Way To Do It™: in the base system, there will never be more than one implementation of *anything*.
- All system source code is stored in one big tree. Any code on the system can be modified by simply pointing an editor to the right file.
- Everything in the tree is compiled/JITed at startup; there are no binaries. The compiler is the bootloader.
- By having no binaries, linkers and other tools are a thing of the past.
- The tree is version-controlled; reverting to a previous software state is as easy as booting `HEAD@{1}`. The version control is the package manager.
- The tree is also content-addressable. Integrity of the entire system (aside from [the compiler](https://www.archive.ece.cmu.edu/~ganger/712.fall02/papers/p761-thompson.pdf)) is ensured by choosing what code to run by its hash, not by its filesystem location. The compiler doesn't even know where to find code that doesn't match the signature given at boot time.
- The entire system is portable to any of rustc/[cranelift](https://github.com/CraneStation/cranelift)'s targets. It can run anywhere from a [RISC-V Arduino](https://www.sifive.com/boards/hifive1) to Linux userspace; the only hard dependencies are a supported architecture and a timer interrupt.

More information will be given in the design document when that's done (probably never).
This project will be finished in like 20 years when I am actually good at Rust.
