bcmstat
=======

Simple Raspberry Pi command line monitoring tool:

* CPU fequencies (ARM, Core, h264)
* Temperature (current and peak)
* IRQ/s
* Network Rx/Tx
* GPU mem usage
* CPU load (including individual cores when available)
* RAM usage (with/without swap)

Tested with Raspbian, OpenELEC and Raspbmc.

Displayed values can be coloured (white, green, amber and red) to highlight excess usage or resource depletion.

View available options with -h.

Specify a default configuration in ~/.bcmstat.conf, eg:
```
xgcd10
```

####Installing on the Pi:

To install the latest version directly from this github repository:
```
curl -Ls https://raw.githubusercontent.com/MilhouseVH/bcmstat/master/bcmstat.sh -o ~/bcmstat.sh
chmod +x ~/bcmstat.sh
```

####Example output:
```
rpi2:~ # ./bcmstat.sh
  Config: v0.1.9, args "Ccgxpd10", priority lowest (+19)
     CPU: 4 x ARMv7 cores available, using ondemand governor
  Memory: 1008MB (split 752MB ARM, 256MB GPU)
HW Block: |   ARM   |  Core  |  H264  |    SDRAM    |
Min Freq: |  600MHz | 250MHz |   0MHz |    450MHz   |
Max Freq: |  900MHz | 250MHz | 250MHz |    450MHz   |
Voltages: |         0, 1.3125V        |  0, 1.2000V |
   Other: temp_limit=85
Firmware: Jan 30 2015 18:25:11, version d6e004c61a7a749897c482c860d0b2c28196437e (clean) (release)
  Codecs: H264 WVC1 MPG2 VP8 VORBIS MJPG
  Booted: Sun Feb  1 14:14:39 2015

Time         ARM    Core    H264 Core Temp (Max)  IRQ/s     RX B/s     TX B/s GPUMem Free  %user  %nice   %sys  %idle  %iowt   %irq %s/irq %total   cpu0   cpu1   cpu2   cpu3 Memory Free/Used
======== ======= ======= ======= =============== ====== ========== ========== =========== ====== ====== ====== ====== ====== ====== ====== ====== ====== ====== ====== ====== ================
14:15:17  600Mhz  250Mhz    0Mhz 39.01C (39.01C)    783        651      8,888 184M ( 77%)   2.22   8.87  19.95  70.95   0.00   0.00   0.00  29.05  29.05  46.79   2.45  37.92 699,268 kB/ 7.3%
14:15:27  600Mhz  250Mhz    0Mhz 37.93C (39.01C)    758         83        104 184M ( 77%)   0.10   0.07   0.15  99.65   0.05   0.00   0.00   0.35   0.15   0.35   0.45   0.45 699,420 kB/ 7.3%
14:15:37  600Mhz  250Mhz    0Mhz 38.47C (39.01C)    758         73        107 184M ( 77%)   0.10   0.10   0.10  99.69   0.00   0.00   0.00   0.31   0.26   0.45   0.06   0.45 699,440 kB/ 7.3%
14:15:48  600Mhz  250Mhz    0Mhz 37.93C (39.01C)    759        110        101 184M ( 77%)   0.10   0.07   0.12  99.72   0.00   0.00   0.00   0.28   0.03   0.43   0.33   0.33 699,484 kB/ 7.3%
14:15:58  600Mhz  250Mhz    0Mhz 37.93C (39.01C)    759        160        106 184M ( 77%)   0.07   0.07   0.15  99.70   0.00   0.00   0.00   0.30   0.23   0.33   0.23   0.42 699,544 kB/ 7.3%
14:16:08  600Mhz  250Mhz    0Mhz 36.86C (39.01C)    760        188        130 184M ( 77%)   0.10   0.07   0.15  99.69   0.00   0.00   0.00   0.31   0.14   0.33   0.43   0.33 699,464 kB/ 7.3%
14:16:18  600Mhz  250Mhz    0Mhz 37.93C (39.01C)    758        119         88 184M ( 77%)   0.07   0.07   0.12  99.71   0.00   0.00   0.00   0.29   0.14   0.43   0.33   0.33 699,424 kB/ 7.3%
14:16:28  600Mhz  250Mhz    0Mhz 37.93C (39.01C)    759        141        107 184M ( 77%)   0.05   0.12   0.10  99.74   0.00   0.00   0.00   0.26   0.02   0.31   0.22   0.31 699,276 kB/ 7.3%
14:16:38  600Mhz  250Mhz    0Mhz 36.86C (39.01C)    759        114        106 184M ( 77%)   0.05   0.07   0.15  99.72   0.00   0.00   0.00   0.28   0.23   0.33   0.23   0.43 699,296 kB/ 7.3%
14:16:48  600Mhz  250Mhz  250Mhz 41.16C (41.16C)  1,306    281,185     41,792 127M ( 53%)   6.17   0.81   2.15  87.96   1.95   0.00   0.96  12.04  27.88   4.00  10.21   6.07 693,980 kB/ 8.0%
14:16:59  600Mhz  250Mhz  250Mhz 39.55C (41.16C)  1,596  1,840,638     59,927 120M ( 50%)   3.77   0.10   1.92  91.66   0.17   0.00   2.37   8.34  22.32   4.97   2.21   3.88 677,884 kB/10.1%
14:17:09  600Mhz  250Mhz  250Mhz 39.55C (41.16C)  1,151    878,442     28,179 120M ( 50%)   0.71   0.05   0.76  97.20   0.00   0.00   1.28   2.80   8.64   0.95   0.76   0.95 677,088 kB/10.2%
14:17:19  600Mhz  250Mhz  250Mhz 39.55C (41.16C)  1,161    887,809     28,799 120M ( 50%)   0.64   0.10   0.59  97.14   0.00   0.00   1.53   2.86   8.65   0.86   0.76   0.96 676,940 kB/10.3%
14:17:29  600Mhz  250Mhz  250Mhz 39.55C (41.16C)  1,172    915,213     29,404 120M ( 50%)   0.84   0.07   0.54  96.99   0.00   0.00   1.55   3.01   9.79   0.72   0.42   1.31 676,848 kB/10.3%
14:17:39  600Mhz  250Mhz  250Mhz 39.55C (41.16C)  1,144    852,960     27,348 120M ( 50%)   0.67   0.12   0.42  97.48   0.00   0.00   1.31   2.52   7.94   0.84   0.75   0.55 676,416 kB/10.3%
14:17:49  600Mhz  250Mhz  250Mhz 39.01C (41.16C)  1,092    735,973     23,735 120M ( 50%)   0.62   0.07   0.49  97.72   0.00   0.00   1.06   2.28   6.77   0.66   0.26   1.25 676,320 kB/10.3%
14:17:59  600Mhz  250Mhz  250Mhz 39.01C (41.16C)  1,028    587,968     19,269 120M ( 50%)   0.64   0.10   0.52  97.87   0.00   0.00   0.91   2.13   6.64   0.73   0.24   1.02 676,204 kB/10.4%
14:18:10  600Mhz  250Mhz  250Mhz 40.08C (41.16C)  1,434    509,176     50,805 177M ( 75%)   5.53   0.57   2.05  90.57   0.02   0.00   1.31   9.43  22.75   3.71   8.64   2.62 677,700 kB/10.2%
14:18:20  600Mhz  250Mhz  250Mhz 39.55C (41.16C)    759        123        107 181M ( 76%)   0.10   0.07   0.12  99.66   0.00   0.00   0.00   0.34   0.26   0.36   0.17   0.66 678,056 kB/10.1%
14:18:30  600Mhz  250Mhz  250Mhz 39.01C (41.16C)    759        127        101 181M ( 76%)   0.07   0.12   0.12  99.68   0.00   0.00   0.00   0.32   0.10   0.29   0.39   0.29 678,336 kB/10.1%
14:18:40  600Mhz  250Mhz  250Mhz 38.47C (41.16C)    758        130        101 181M ( 76%)   0.10   0.07   0.12  99.71   0.00   0.00   0.02   0.29   0.27   0.46   0.17   0.36 677,932 kB/10.1%
14:18:50  600Mhz  250Mhz  250Mhz 37.93C (41.16C)    759        135         93 181M ( 76%)   0.10   0.02   0.20  99.66   0.00   0.00   0.00   0.34   0.24   0.73   0.04   0.24 678,292 kB/10.1%
14:19:00  600Mhz  250Mhz  250Mhz 39.01C (41.16C)    759        119        101 181M ( 76%)   0.15   0.05   0.15  99.65   0.00   0.00   0.00   0.35   0.08   0.57   0.47   0.37 677,964 kB/10.1%
