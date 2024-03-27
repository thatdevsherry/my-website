Definition from ITU-T Rec. H.264:

>A byte equal to `0x03` that may be present within a NAL unit. The presence of emulation prevention bytes ensures that no sequence of consecutive byte-aligned bytes in the NAL unit contains a start code prefix.

The sequence `0x00_00_01` inside a NALU payload can **emulate** a start code, but could be part of the payload itself, so we add a `0x03` b/w the second and third byte to **prevent** start code **emulation**.

```
() = start code
[] = NALU

[02 02 00 00 01 02 02] (00 00 01) [03...
       _uh oh__

emulates start code, but is not a start code

add a 0x03 byte b/w 2nd and 3rd byte

[02 02 00 00 03 01 02 02] (00 00 01) [03...
       __we good__
```

Note that emulation prevention doesn't just happen for `0x00_00_01`, but also for the following cases:
- `0x00_00_00`
- `0x00_00_02`
- `0x00_00_03`

## References
[`h264-reader`](https://docs.rs/h264-reader/latest/h264_reader/rbsp/index.html)