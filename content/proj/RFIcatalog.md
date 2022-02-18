---
title: "RFIcatalog"
date: 2022-02-18T17:30:17-05:00
draft: false
---


I've been working on a catalog of all known possible sources of RFI using various databases, [available here.](https://docs.google.com/spreadsheets/d/1MAK5FBJo5xIQESxf3t1DqE8f7ujrwv9_bjh3k_xaB28/edit?usp=sharing). This spreadsheet has an entry for every recorded wireless transmission source from:

 - [Met. Sat. database](http://mdkenny.customer.netspace.net.au/metsat_frequencies.html)
 - [OSCAR](https://space.oscar.wmo.int/satellitefrequencies)
 - [SigID Wiki](https://www.sigidwiki.com/wiki/Signal_Identification_Guide)
 - [JE9PEL](http://www.ne.jp/asahi/hamradio/je9pel/satslist.htm)

As well as Wikipedia in general and Green Bank's own database. The current list only covers L-band, though I want to include more tabs for other bands as well.

{{< figure src="/images/catalog.png"
caption="A collection of satellite transmissions and information about them." >}}

Eventually, I want to match up sources in this table with sources I see in observed data and mark down if they can be flagged automatically by various RFI mitigation techniques (Spectral Kurtosis, Cyclostationary, etc). This will hopefully increase my understanding of RFI environments and statistical mitigation. If you have any insights into this side project, or know of any other places where I can collect info, I'd love to hear from you!
