# Bean65

6502 homebrew computer that can take advantage of BeanBoard peripherals which were originally designed for the Z80 BeanZee.

See also: [PainfulDiodes Blog: Bean65](https://painfuldiodes.wordpress.com/category/bean65/)

- W65C02S CPU
- 2MHz clock
- 32k ROM
- 16k RAM
- W65C22N VIA

The CPU bus carries only ROM, RAM and the VIA, decoded with a single 74HCT00 following Garth Wilson's [simple ROM/RAM/VIA design](https://wilsonminesco.com/6502primer/potpourri.html): RAM at 0000-3FFF, the VIA at 4000-7FFF and ROM at 8000-FFFF.

Every peripheral sits on a "slow bus" behind the VIA,  under software control, allowing for slower devices to be connected (and 6502's dummy reads can't reach them).

The "slow bus" provides 6502-style signals - address and R/W#, with the addition of an I/O (enable) strobe. These map economically onto BeanBoard's Z80-style bus: the strobe acts as IORQ#, R/W# serves directly as WR#, and one spare 74HCT00 gate inverts it for RD#. This can work because every BeanBoard device that drives the bus is gated by IORQ#, so BeanBoard works unchanged.

Bean65 plugs into BeanBoard's sockets.

The BeanPort USB interface can plug into Bean65's two 2x7 VIA Interface headers (in Garth Wilson's VIA connector format). When BeanPort is not connected, these connectors can serve as a general-purpose VIA connector.

## Links

- [Garth Wilson's 6502 primer](https://wilsonminesco.com/6502primer/)
- [BeanZee](https://github.com/PainfulDiodes/BeanZee)
- [BeanBoard](https://github.com/PainfulDiodes/BeanBoard)
- [BeanPort](https://github.com/PainfulDiodes/BeanPort)
