---
title: "RFI Mitigation"
date: 2022-01-30T11:21:36-05:00
draft: false
---


Modern radio telescopes are *incredibly* sensitive - they have to be in order to detect the weakest astronomical signals out there! Between the huge collecting area of their dishes and the amplifiers boosting the incoming signals by a factor of millions, these telescopes can collect incredibly dim radio emissions from a plethora of celestial objects. Humans, on the other hand, are incredibly loud. Our day-to-day lives are filled with all sorts of wireless transmissions, both intentional and unintentional. I've listed many objects below that emit electromagnetic energy, though the list is in no way exhaustive.

 - Satellite internet/phone service
 - Bluetooth
 - Wi-Fi
 - Wireless phone charging pads
 - Spark plugs (!)
 - Airport/Weather radar
 - Powerline transformers
 - Any unshielded electrical device

All of these human-made signals, known as Radio Frequency Interference (RFI) are massively more powerful than the typical celestial signals we try to capture, and block us from gathering useful scientific data. It is imperative, therefore, that we develop techniques to reduce or eliminate this RFI all together. Usually, you just build your telescope away from most sources of RFI as is the case of the Green Bank Observatory, which uses the natural mountainous terrain of West Virginia to hide themselves from most wireless communications. But, some RFI can always leak in.

{{< figure src="/images/iridium.png"
caption="Iridium satellite communications at 1620 MHz" >}}


{{< figure src="/images/bedfordradar.png"
caption="One sweep of the Bedford, NC FAA radar at 1235 MHz" >}}

There are lots of different techniques to remove RFI from data, with varying degrees of complexity and success - some of the RFI mitigation methods I've explored include:

 - Median absolute deviation
 - Subspace Cancellation
 - Sigma Thresholding
 - Reference Antenna Cancellation
 - Cyclostationary Detection

My main focus recently has been on Spectral Kurtosis, developed by Gelu Nita and Dale Gary. For each spectral channel, we collect some statistically significant number of *M* squared power values, and use an estimator to calculate the gaussianity of the underlying distribution. If the data is clean, it should only contain data generated from a perfect normal gaussian distribution. If RFI is present, however, it can cause that distribution to become more 'flat-topped' or 'spiky', which our estimator can pick up on. Thus, we can flag contaminated data. Some more reading can be found at:

[Nita et. al 2010a](https://academic.oup.com/mnrasl/article/406/1/L60/1041152?login=false)
[Nita et. al 2010b](https://iopscience.iop.org/article/10.1086/652409)


I'm currently working on a paper testing the effectiveness of Spectral Kurtosis mitigation against a collection of realistic simulated RFI signals, as well as testing the technique on high-resolution pulsar data taken with the Green Bank Telescope.


<!-- {{< figure src="/post/images/sample_image.jpg"
caption="Photo by Tim Mossholder on Unsplash" >}} -->
