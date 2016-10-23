---
layout: post
title: The Billboard Chart 2000
date: 23/10/16
---

# The Billboard Chart

### Background

The following analysis looks at the Billboard chart from the year 2000. The Billboard charts tabulate the relative weekly popularity of songs or albums in the United States and elsewhere. The analysis was done using Python along with its extended libraries Numpy, Pandas and Matplotlib for visualisations. Pandas was used for its functionality when dealing with data frames.


### Reading and clensing the data

The following snippet of code was used to read in the data and convert it to a Pandas Data Frame. 

![alt text](https://lh3.googleusercontent.com/0CZa74ArBx-AZdCGL6UvZOTP2wWNOaSOUMfl0UmBp8YR8lPVfgoK69yuJYqHbsgGgFOruZNqlmfzsNgBnPbcey1MeVJ7WWlwbzozfi9jjax8lMK692u7pjeK1mq4WxlkYy3eiVXtZaiN4Y9hqPX0DpSpmooZrin0aIYNkCY92CSoDVSyJfQcxWtXttRsPt6tTcXBTbGAhtMCfjLvi-AHcAAH1nhZfdd8pK29KEa12Qhq8geA8ERyzlSozMP2fs2E6_3mABDnkPpTBmzhpXERIqPIK2LLtp_W61wvnw8IH278hp1KTC167P9oe2cieK7MUusVaScdkHytZ3YjNvQDtQzzDUeqlwMNNzcd7zY27Ufnqwy8eIWPBzqyQXT6BSq5q0UClhQpARnzpMSieCPqXImjW3GFYcd_Jas3wJfUeWb2ivlOH8IBdi2lqhVxYYhlBdwQUwbO4gB-8qS9VfVg20Vp0xcQQb7GOXVq2mCh4uwOrdGMVZ4vrtjp1jVmJa-9YNtPVK4-8olQP1rzlU7iCAsHC8n66p1VUDVfl3b5j9iyf5pMj9IUQy-4ouIXcxPQ21lmYegD=w1280-h699-k)

The data set contained information on songs in the Billboard chart during the year 2000. There was a total of 317 rows of data, corresponding to individual tracks. The following fields were included for each song:

- Track name
- Artist
- Genre
- Track length 
- Date entered
- Date peaked
- Relative weekly chart position 

The data itself was relatively clean but in order to be able to analyse it, a number of fields had to have their data types converted. 

![alt text](https://lh3.googleusercontent.com/5OZkJK4RhYubCjBfWzWjjdWSlXGjBUYD8odtxe0UgQSIxHqSPJFtdKEPFQPWuvqR4Qi_c7Xv7J8iY1q5xFOFAXhXP2RmQK1cXecmYE51UgYlIXZerw_OqnAnRlAzvUx1Tqnnhie6I_-fcLpCIdObVsP-q5vVS6Vcm28jAsdiKjeA8w_LMmeuQ7e3WWIK_-XUsVX-7WlBpnHrffyuX87NODT6AfePe1bZUkTYg44LGbbZI4wIZqcBDVyauPHqp-HdvGAlCt6rG4UiZF8sW8AKbEdhGBQFlD4Kw8G3TYv8mTkFNqqjTNPSsYGUEzgU_kvR93_J3roLcXU3Ep5jK0HiBhpMizSP48ZovzP1qqz79Kuetb4kAMlAx5q8AsfDjFHP3OspZ4sBe7AQPqBworrfYLGHsf9IJ91ze43gFKydgyu4Y8mVQJqPHkcaQgrgoyhRLAZn0mrF-jt9JX2hBglJU_cSkVOfkj0ww4OQb7Q00Y2jPKP80Mvt5BxzCUdjB8gokZS9TOeybQQsRRLadZSoeUunPG26WhJS3uxEvnu0AMTiKMTkWhRza9Oh7ngfFTfUFl2OtMYv=w1280-h699-k)

There was also whole columns which contained NaN values, making them redundent. For this reason they were dropped.

![alt text](https://lh3.googleusercontent.com/ZJ8R3YzBIY2kuXZgtYJ6Yp7dJd-ZdrVtiP0zWjMAy_VXfftJbBOwcagug8gXHeZmMQg1iYltEpO9RGvM4c2urrIll6gRNlOECZCFtvXvxMuu-y1dPrNRSqE6-nCJe9rQ5m2WOCMmrAqHh29GyktWUXeBjwlB44uJtR-aeHZzAGwJPNaVuRfXlm6ySGcdHq8Xwo2ijx1DaLg1kUXxmRv4i3v-o-1beclburoqUDfHMBXhmT6_A43nlkZ-msqAGC5BkpL9yNUUliiGGcQrvG-rcarA9N6O83gcyw5zkFpl9pkRjs1JOh8tjsh9z9yrBNFy51WnEObXgMmrq8eiZWvZL7E-q2agsgbIyq3TJ0X1hnDpzaCuvIdCYyrXTc9-Ryjh42Rft9MjyfSrRiytvPEFTdzmrWUkXct3fAlO3fUjQGo1N-IiDRfBF6Lqb1Kd_wzqVbY-vaSN67V6ha0CFRmqhmhYyZZJsHLcxJAF5x6w3xtpY-WSSO-5TKyaUbnyMwhYfB-rLJxl39G2s6MeIp2M38xZGSE_HASgG6RrGyZN_5Lf3r2FXrk6hqVrpnfKmlUQKItDeA-0=w1280-h699-k)

Extra fields including highest charting position and average chart position, which was easily calculated from the data, was added.

A problem I encountered was trying to convert the time field to a time format. The format it was initially in, Python did not recognise. This was solved by appending '0:' to the beginning of each time before trying to convert it.

![alt text](https://lh3.googleusercontent.com/lNwwYnLQnss_vfiLh5uCVwD8G48W4Yyx2nGXgSShJgxD1lHlShEU9T0SQcWNHGMNe-6_cPy44wwbfxKjvb6hjQ_DmNq6-Dj79oFHO-vjEQ7Q-FMEgeIuJrWseK6TnB9s6HwlRmCZ3auw0nVYJY5QvgCXhRMKLGUSV7z7Iwm6KK9ZKWv344EvVHC0jOdeHAyNH3jm7UEaYcQnZpqw30zugISseLBxHI5g6OV5Bl6gPUBBZv-R4jtyuZa3PO7QddLkayZk-S_EC2iS-47ZZ-Lv_MdrJRGiHrcs0udEL5voUGQLj-FFRJMRES0EA58s2tJ3_RpIHCoqaYX-RAxRIeN03mAmAEHPfCsNojrhFp9XE_mozzguRB_mIsdLqY_KWR9KRJGEDLzLv6c1pXyCIatEpFlEAWM7iK32QzLONCuLDz4qnnGS8qUvmyKzLC0-7zIBu9uesc5hK7R9IXtFe26TVm2XwfKzzJmgASoZS1zS9AtFkK-tWaPASKlKIYj46m_OjjSxsayJDcNWmN-MQ483AURSEaD_khca-i2CdnFfC2J1iy6BsKW8H_UQnWcZek0FCcksufOm=w1280-h699-k)

### Analysis summary

After clensing the data, analysis could then be performed and visualisations made. Visualisations were made using Matplotlib along with Pandas in-built plot function, which in some cases was easier to use. Pivot tables were also used in order to aggregate.

The following is a summary of some of the main findings from the data


** Track length distribution **

![alt text](https://lh4.googleusercontent.com/WIn878TgzJyKYEYb189OaOwmZH3-yoQP5GY_kgmDnGF-rVsK91Z4ejZKqSbMpYmnC1c-6Mps=w1240-h712)

The histogram shows that track lengths are normally distibuted (as expected), with a slight positive skew. The majority of tracks fall between two standard deviations either side of the mean. The average track length was 156 seconds.

** Popular artists and tracks **

There was a total of 317 tracks by 228 artists charting in the year 2000, meaning that many artists had multiple tracks in the chart throughout the year.

The following table gives a list of all artists that reached number one in the chart. There was a total of 17 number ones, corresponding to 15 artists.

![alt text](https://lh3.googleusercontent.com/3rvFq5hoPQDHBa5nzdh_09QO_coUOewQirVIyCHaXKl4I3oXbm65CbUmeYzdHfaMJ08zvpk-w54nVI0-NONGZ5_Y60UOyyPxSfzvuOvUHnWLn7Xum4EVoNIX5n-TY_sRFnY6yuEziovOlzD_i1epjXunCNqcjVkTsXxWc9cUWY-DEiV5qhAanyGPiRv3muSD3H-U1SXKG0p_SUo1tkJosj1P0LT_3qAWe3QlC_EarNqAC3OhfGqHuCooXq8kiecvNDv4I6FV-2Z_D_b3iVIOyJG9CidMUDoBJT-Z55H1fDrPt_Tq2uFADfSeb9Yobv9DrIF8MOcK7FDxwjhuw-9Rcz95Rr533cCu9CAIKSbTvYiRrhCGIQREC59fD9FJ5l7Lwq9_JsgGtd3A1EXylXrak9zHykhkZfu0b67eSJ1PDdUICdKs6NzIrT45t7FF7DL5ILNAYqQSAWB-rO3Au2bq9Osoc4-iv1UIiR2Py8ylffwZJHjjekdOvOxOfPpKv-yaGOYfZA6V7IqRB1YlZUYsvud_fMN9-uzuNyRoViD1vfIb0ZLoxcRyBut1hwdA9fv32usjo7ub=w1280-h699-k)

A tracks averaged chart position, for the time it was in the chart, was also analysed and it was shown that the song and corresponding artist who had the highest average chart position over the time it was in the chart was; Maria, Maria by Santana

![alt text](https://lh3.googleusercontent.com/_Y3Mv-wi1mGiOvvDKHhU27I7S_oSgaT1wkZekyCr-W5bWrqgOUGYBFJgRJJyg1pHJV4S3nlmJ8ATu87VEoB7MyLHocFLOTEZiWRnpD8bDuthJjRrDwVAWu-wpqWxGjbsH8qrzdOVwydXK1uqW0CE2hCxH36Y7vU1vA2k2WLGAzuSCTU0tyH5t6VrKC0_hSRTPNjIJt4TK6FzdmrP3eDFjuxC94oseqQvgyOszBVUnifD60AVUysKua4snA1_K0ELB-nQXoLZ1cII4Ekk9Cm5dFiDCTrht_h6shCp3bNxRytRu_staiZqikE1a2HgVGhALlwvI9_wHDpZ9fsG_x-y0l7EnXmcA-jZ22q8kYqGuQqDQHhMdKDzOjEOk8uYle6d4b4d7LZXF3O1bvX7jusn-xx2RKVpB006bPiP5LjiGe4AxMl_s_cyOve_8bHXctc0w0VEafpowPn-N7U3ETbiDGFXhKLlqKB9aWd7XomkYb3doV8qazTZJxhL6U28tm7XNA-xOLc0DGpYQ9ICM5PlGNn4S0b-4GTq4iPuSWtRI9ICZix_Zoz-NRRMeX9g-hKv8gP-0LE3=w1280-h699-k)

** Genre **

As shown in the following bar chart, the most popular genre of music in the chart was Rock, followed by Country. After closer inspection of the categories, although subjective, the indentification of artist to genre might not be correct. For example Christina Aguilera has been categorised as Rock.

![alt text](https://lh3.googleusercontent.com/pcw3junXL2gTwUcFJXXyEkaqwoMSAeMVOBRR1e61Kt_455Gl_DXLhaSTrPwUv2ZkJWj_-SecaTSa46_y5uJent1bvFrxQwq431N2qwCIE6c1AsUdLUH8CnKTU0HdUtgbl1KV26wxxnc2p0NZY6N943IwBHY02DPg2xX_SG2BsfCeaIxkGk6USiQuHG9dAJyTdQ11WoT4AGbY-Kkn7TRlHz2UpXzOaU91TtFB7dnyHwb1f6ckgkiq4zZYdytgkb0lgOOsXBZg8aYjeX4iGSl5i5h71V6kdXbbnG5xnnv7j97uiMyddYLS0-3QFlvoCnPsONoangP8T5gI9acPhvSSO-BbIWvtQrkjCR4k5iiGOksIRizYcApn8zLdCW9jcA3dcLYO4PsyoVKum-JkihwS1nM6bLF6T15-UU72kBxtMMkfFMuq-rueSK9X8t9t8Yw-3t1HM7Y-wgzmkUspV25hQ8BTuGEUSTSKhOmYwzKiyonQvrIsfjhqhSk6f7CFnIvesnzA8ArtWhp5o9uwRZ-U9DE23X7vUUZgNnDJSgN9laideL2zWRJAA7vmZTjoG7h_wloYTnDb=w1280-h699-k)


** Number of tracks entered per month **

The number of songs entered into the chart each month peaks in April. A total of 33 tracks entered. As shown by the graph, the number of tracks per month, starts to fall off in August.

![alt text](https://lh3.googleusercontent.com/fiZL3EOENUgDcFWCzKRCxQ4KH16N4kN76zeIjcuW2qfdgrnF3jlLLVPHkZze_d65ZGhKZewDwndoqUo4XKh0u9k8CKvQJQi0te4pU96WLrJ6H8C8SNry3Bz1DdND8nm5eenbJVudG9sjcJ7IzSPqambwIRRPY5mAIT4-8O3uZh3AOFckN-tFKS5f4bLtDEtDIIHgvTAHXAZQSblU5G-LF-xmYXyrv0BI9f_LDy_53w5-3Y1_q-x9e40wOzc2sTQuh67ckIkwQ70Sxg1YXEMR8JC3u1bcaoobKCuCgLliCOHLzQffOUETwW-U11phMQQ3zbEMzQd2PYzuuiEwbqf-SGn8729sSQmrkeYa3G-GipcZfEZmoeemFp3MCiDJsho4R9ARQoQoc90MHcVksaVTMs8-9yl-y7IBLhaOp4sJhCN-vhdMIUucS2xp45VrW7tLvkdzaownIvcMsW6IFPpvOFZ9LSGxckH33aT-w4WFEzwQpBZohJWjP80REzyctULqyKIxDUniE6pu65PHesSIYhWiM3h0uS1h346t9eo1gosIdPxLWIg8AG7rBOJJX7wG3Udd62kg=w1280-h699-k)

