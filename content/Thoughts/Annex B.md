Annex B is a format for specifying how NALUs can be combined together in a stream.

This is because a NALU itself does not contain the size of its payload, so simply placing them one after another as a stream will not work as we won't know when individual NALUs end [`[1]`](https://stackoverflow.com/a/24890903).

Annex B specifies **start codes** which are added to start of every NAL, which is in the form of either:
- Two consecutive zero bytes followed by `0x01` i.e. `[0x00_00_01]`
- Three consecutive zero bytes followed by `0x01` i.e. `[0x00_00_00_01]`

So we can use an Annex B stream for transmitting several NALUs together.

## Escaping in payload

In programming, we encounter situations where we have to add a quote inside a string literal e.g. python.

```python
my_string = 'I'm kewl' # invalid because the second quote ended the string
my_string_escaped = 'I\'m kewl'
```

We wanted to add a quote inside the string, but the quote also acts as the start/end of the string, so we escape the inner quote to tell that this is part of the string, and not a start/end quote.

Similarly, it is possible to have bytes like `0x00_00_01` or `0x00_00_00_01` inside the payload, which is actually part of the payload and not a start code, and there is a defined way of escaping them called [**Emulation Prevention**](Emulation%20Prevention).