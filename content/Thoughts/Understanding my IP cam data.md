Some time ago I had bought a generic outdoor IP cam. It was chinese. Imagine how happy I was when I realized it didn't follow the ONVIF protocol and didn't work with most (if not all) ONVIF compliant software.

Then I tried one rust crate which gave me an error, and I decided to open an issue on github and didn't think much of it.

Little did I know the author of that crate was a legend and decided to communicate further and figure out the issue.

He asked for a wireshark dump which I provided, and he was pretty quick to point out the cause.

I had worked on this issue before some time ago, but I forgot what I did, so now's a good time to start fresh and document publicly.

# [[Analyzing the wireshark dump of my IP camera]]