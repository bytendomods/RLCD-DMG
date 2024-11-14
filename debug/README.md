# Bytendo Debugger

## What is it

An open source handy little breakout board to debug and flash the main driver board while it is installed in your console.

## Building

While most of the board is straightforward to build with an iron, I have found the fine pitch on the 10p connector is easier to work with if you have a hot plate. Order a board using the provided gerbers.

## v0.2 BOM

| Designator | Qty | Value/Part Number    | Package        | Description           | Source                                                                                                                           |
|------------|-----|----------------------|----------------|-----------------------|----------------------------------------------------------------------------------------------------------------------------------|
| D1         | 1   | NSR0320MW2T1G        | SOD323         | Shottkey Diode        | https://www.digikey.ch/en/products/detail/onsemi/NSR0320MW2T1G/1218949                                                           |
| DB1        | 1   | F32R-1A7H1-11010     |                | 10POS 0.5MM Debug FFC | https://www.digikey.ch/en/products/detail/amphenol-cs-fci/F32R-1A7H1-11010/11564543?s=N4IgTCBcDaIGYGYwCcC0BGAhgdgBbo3QAZiQBdAXyA |
| J1         | 1   | USB4105-GF-A         |                | USB-C Receptacle      | https://www.digikey.ch/en/products/detail/gct/USB4105-GF-A/11198441                                                              |
| J2         | 1   | SM03B-SRSS-TB        |                | 3-pin Header          | https://www.digikey.ch/en/products/detail/jst-sales-america-inc/SM03B-SRSS-TB/926709                                             |
| R1, R2     | 2   | 5.1k                 | 603            | Resistor              | https://www.digikey.ch/en/products/detail/yageo/RC0603FR-075K1L/727268                                                           |
| SW1        | 1   | PTS645SK43SMTR92 LFS | SW_SPST_PTS645 | Tactile switch        | https://www.digikey.it/it/products/detail/c-k/PTS645SK43SMTR92-LFS/1162181                                                       |

#### Notes on the v0.1 Debugger

* While most of the board is pretty straightforward to build with an iron, I have found the fine pitch on the 10p connector is easier to work with if you have a hot plate.
* I've noticed it's easy to kinda wiggle the 10p ribbon around even after it's seated and locked into the connector, which can cause the board not to connect. I'm not thrilled with the connector I picked, but in my experience its mostly fine if you are careful.
