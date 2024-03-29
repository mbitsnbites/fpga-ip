# PLL (Phase Locked Loop)

A PLL entity can be used for deriving different clocks from a source clock. Typically an FPGA will have an external clock (e.g. generated by an [oscillator](https://en.wikipedia.org/wiki/Electronic_oscillator)), which can be used to derive several different internal clocks in the FPGA.

Usage example (VHDL):

```vhdl
  pll_1: entity work.pll
    generic map (
      REFERENCE_CLOCK_FREQUENCY => "50 MHz",
      NUMBER_OF_CLOCKS => 2,
      OUTPUT_CLOCK_FREQUENCY0 => "120.0 MHz",  -- CPU clock
      OUTPUT_CLOCK_FREQUENCY1 => "74.250 MHz"  -- VGA clock: HD 1280x720 60 Hz
    )
    port map
    (
      i_rst	=> s_pll_rst,
      i_refclk => CLOCK_50,
      o_clk0 => s_cpu_clk,
      o_clk1 => s_vga_clk,
      o_locked => s_pll_locked
    );
```
