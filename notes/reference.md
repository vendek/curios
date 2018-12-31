# Code Reference

- [HermitCore-rs](https://github.com/hermitcore/libhermit-rs) (BSD license) is already a Rust unikernel. A quick-and-dirty way of getting this project working on bare metal would be to implement it on top of HermitCore.
  - [scheduler](https://github.com/hermitcore/libhermit-rs/blob/master/librs/src/scheduler/mod.rs)
- [Redox](https://gitlab.redox-os.org/redox-os/redox) (MIT license) is a little more "real-world," although its design is lacking IMO. This would be a good place to start for a bare-metal x86 port.
  - [scheduler](https://gitlab.redox-os.org/redox-os/kernel/blob/master/src/context/switch.rs)
  - [ralloc](https://gitlab.redox-os.org/redox-os/ralloc) has a "shim" layer that we can replace
  - [relibc](https://gitlab.redox-os.org/redox-os/relibc)? Not sure the concept of a libc even applies 😁
- [smoltcpd](https://github.com/m-labs/smoltcp) ([0BSD](https://opensource.org/licenses/0BSD), effectively public domain)
