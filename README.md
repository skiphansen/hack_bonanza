# hack_bonanza

After reading this article on [DOOM ON A DESK PHONE IS JUST THE TIP OF THE ICEBERG](https://hackaday.com/2021/08/13/doom-on-a-desk-phone-is-just-the-tip-of-the-iceburg/) of course I had to have one.

[Josh's article](https://joshumax.github.io/general/2021/08/11/running-doom-on-captioncall.html) is great but short on details.

The intent of this repo is to supplement Josh's info.

## Features

1. Large, bright great looking LCD.
2. 2.4 gig WiFi
3. 100 BaseT Ethernet
4. Sound subsystem ... super LOUD (DUH! for the hearing impaired)
5. ... To be continued.

## Serial port connections

````
  1 2 3 4 5 6
+-------------+
| O O O O O O |  J5
+-------------+
|-------------|
````
1. Gnd
2. unknown
3. unknown
4. Rxd (data from serial port to device)
5. Txd (data from device to serial port)
6. unknown

Serial port configuration is 1152008N1

The root password (**thanks ot Josh!!**) is y4u8it

## WiFi scanning

````
[192.168.123.109]/etc# ifconfig eth1 up
dhd_rx_frame: net device is NOT registered yet. drop packet
dhd_rx_frame: net device is NOT registered yet. drop packet
[192.168.123.109]/etc# iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:25:9C:13:80:32
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"SkipNRebecca"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0005c9f3edc2530b
                    Extra: Last beacon: 85ms ago
                    IE: Unknown: 000C536B69704E52656265636361
                    IE: Unknown: 010882848B962C0C1218
         CONSOLE: 22 packets not freed at wlc_down
           IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 3205243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A6D1017FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: Unknown: 7F080400000000000140
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
          Cell 02 - Address: 76:83:C2:C7:CE:CA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"lesswire"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0005c9f3edc25314
                    Extra: Last beacon: 85ms ago
                    IE: Unknown: 00086C65737377697265
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 05050203009803
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 0B05040035127A
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1601080C00000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD1300156D00010100010257E581067483C2C6CECA
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
...

[192.168.123.109]/etc# 
````

## DMESG
````
Starting kernel ...

Linux version 3.0.35-2213-g7e8c89c (bonanza@bonanza) (gcc version 4.6.2 20110630 (prerelease) (Freescale MAD -- Linaro 2011.07 -- Built at 2011/08/10 09:20) ) #3 SMP PREEMPT Tue Jul 31 11:52:30 MDT 2018
CPU: ARMv7 Processor [412fc09a] revision 10 (ARMv7), cr=10c53c7d
CPU: VIPT nonaliasing data cache, VIPT aliasing instruction cache
Machine: CapCall Bonanza Board V1
Ignoring unrecognised tag 0x54410008
Memory policy: ECC disabled, Data cache writealloc
CPU identified as i.MX6DL/SOLO, unknown revision
PERCPU: Embedded 7 pages/cpu @8c008000 s5024 r8192 d15456 u32768
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227328
Kernel command line: console=ttymxc1,115200 video=mxcfb0:dev=ldb,1024x600@60,if=RGB666 fbmem=28M vt.global_cursor_default=0 eth=48:65:EE:24:70:CC bt=48:65:EE:24:70:CD NoReset boot_image=2 hardware_revision=5 ip=off
Setting MAC address to: 48:65:EE:24:70:CC
PID hash table entries: 4096 (order: 2, 16384 bytes)
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 640MB 256MB = 896MB total
Memory: 889720k/889720k available, 158856k reserved, 0K highmem
Virtual kernel memory layout:
    vector  : 0xffff0000 - 0xffff1000   (   4 kB)
    fixmap  : 0xfff00000 - 0xfffe0000   ( 896 kB)
    DMA     : 0xf4600000 - 0xffe00000   ( 184 MB)
    vmalloc : 0xc0800000 - 0xf2000000   ( 792 MB)
    lowmem  : 0x80000000 - 0xc0000000   (1024 MB)
    pkmap   : 0x7fe00000 - 0x80000000   (   2 MB)
    modules : 0x7f800000 - 0x7fe00000   (   6 MB)
      .init : 0x80008000 - 0x80cf1000   (13220 kB)
      .text : 0x80cf1000 - 0x811b72e8   (4889 kB)
      .data : 0x811b8000 - 0x811fab60   ( 267 kB)
       .bss : 0x811fab84 - 0x81244688   ( 295 kB)
SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Preemptible hierarchical RCU implementation.
NR_IRQS:496
MXC GPIO hardware
sched_clock: 32 bits at 3000kHz, resolution 333ns, wraps every 1431655ms
Set periph_clk's parent to pll2_pfd_400M!
MXC_Early serial console at MMIO 0x21e8000 (options '115200')
bootconsole [ttymxc1] enabled
Console: colour dummy device 80x30
Calibrating delay loop... 1570.81 BogoMIPS (lpj=785408)
pid_max: default: 32768 minimum: 301
Mount-cache hash table entries: 512
CPU: Testing write buffer coherency: ok
hw perfevents: enabled with ARMv7 Cortex-A9 PMU driver, 7 counters available
CPU1: Booted secondary processor
Brought up 2 CPUs
SMP: Total of 2 processors activated (3151.87 BogoMIPS).
print_constraints: dummy: 
NET: Registered protocol family 16
print_constraints: vddpu: 725 <--> 1300 mV at 700 mV fast normal 
print_constraints: vddcore: 725 <--> 1300 mV at 1150 mV fast normal 
print_constraints: vddsoc: 725 <--> 1300 mV at 1200 mV fast normal 
print_constraints: vdd2p5: 2000 <--> 2775 mV at 2400 mV fast normal 
print_constraints: vdd1p1: 800 <--> 1400 mV at 1100 mV fast normal 
print_constraints: vdd3p0: 2625 <--> 3400 mV at 3000 mV fast normal 
------------ Board type Bonanza V1
------------ Setting ids
------------ Adding UARTs
------------ Adding HDMI core
------------ Adding ipuv3
------------ Adding vdoa
------------ Adding lcdif
------------ Adding ldb
------------ Adding rtc
------------ Adding caam
------------ Adding gpio leds
------------ Adding i2c1
------------ Adding i2c2
------------ Adding i2c3
------------ Registering i2c1
------------ Registering i2c2
------------ Adding HDMI
------------ Adding thermal
------------ Adding FEC
------------ Adding PM
------------ Adding SD2 (Ampac)
------------ Adding SD3 (EMMC)
------------ Adding VIV
------------ Adding KPP
------------ Adding USB
------------ Adding vpu
------------ Initing audio
bonanza_audio_clock_init:545 PLL4 set to rate 786432000
imx6_init_audio:1024
------------ Adding PWMs
------------ Initing otp, viim, wdt, dma
------------ Adding dvfs core
------------ Adding device buttons
------------ Adding ringer driver
------------ Adding HDMI soc
------------ Enabling clocks
------------ Exporting GPIO
------------ Done with board init
hw-breakpoint: found 6 breakpoint and 1 watchpoint registers.
hw-breakpoint: 1 breakpoint(s) reserved for watchpoint single-step.
hw-breakpoint: maximum watchpoint size is 4 bytes.
L310 cache controller enabled
l2x0: 16 ways, CACHE_ID 0x410000c8, AUX_CTRL 0x02050000, Cache size: 524288 B
IMX usb wakeup probe
bio: create slab <bio-0> at 0
print_constraints: VDDA: 3300 mV 
print_constraints: VDDIO: 3300 mV 
machine_constraints_voltage: VDDD: unsupportable voltage constraints
reg-fixed-voltage reg-fixed-voltage.2: Failed to register regulator: -22
reg-fixed-voltage: probe of reg-fixed-voltage.2 failed with error -22
print_constraints: vmmc: 3300 mV 
vgaarb: loaded
SCSI subsystem initialized
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
pca953x 1-0020: failed reading register
pca953x 1-0020: interrupt support not compiled in
Running pca9535 setup
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0020: failed writing register
pca953x 1-0021: failed reading register
pca953x 1-0021: interrupt support not compiled in
Running pca9535 setup
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0021: failed writing register
pca953x 1-0022: failed reading register
pca953x 1-0022: interrupt support not compiled in
Running pca9535 setup
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
pca953x 1-0022: failed writing register
imx-ipuv3 imx-ipuv3.0: IPU DMFC NORMAL mode: 1(0~1), 5B(4,5), 5F(6,7)
MIPI CSI2 driver module loaded
Advanced Linux Sound Architecture Driver Version 1.0.24.
Bluetooth: Core ver 2.16
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: L2CAP socket layer initialized
Bluetooth: SCO socket layer initialized
cfg80211: Calling CRDA to update world regulatory domain
Switching to clocksource mxc_timer1
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
UDP hash table entries: 512 (order: 2, 16384 bytes)
UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
NET: Registered protocol family 1
Static Power Management for Freescale i.MX6
wait mode is enabled for i.MX6
cpaddr = c0820000 suspend_iram_base=c08b4000
PM driver module loaded
IMX usb wakeup probe
msgmni has been set to 1737
io scheduler noop registered
io scheduler deadline registered
io scheduler cfq registered (default)
xz_dec_test: module loaded
xz_dec_test: Create a device node with 'mknod xz_dec_test c 252 0' and write .xz files to it.
MIPI DSI driver module loaded
mxc_sdc_fb mxc_sdc_fb.0: register mxc display driver ldb
_regulator_get: get() with no identifier
imx-ipuv3 imx-ipuv3.0: IPU DMFC DP HIGH RESOLUTION: 1(0,1), 5B(2~5), 5F(6,7)
Console: switching to colour frame buffer device 128x48
mxc_sdc_fb mxc_sdc_fb.1: register mxc display driver lcd
mxc_sdc_fb mxc_sdc_fb.1: ipu0-di0 already in use
mxc_sdc_fb: probe of mxc_sdc_fb.1 failed with error -16
imx-sdma imx-sdma: loaded firmware 1.1
imx-sdma imx-sdma: initialized
Serial: IMX driver
imx-uart.0: ttymxc0 at MMIO 0x2020000 (irq = 58) is a IMX
imx-uart.1: ttymxc1 at MMIO 0x21e8000 (irq = 59) is a IMX
console [ttymxc1] enabled, bootconsole disabled
console [ttymxc1] enabled, bootconsole disabled
imx-uart.3: ttymxc3 at MMIO 0x21f0000 (irq = 61) is a IMX
loop: module loaded
FEC Ethernet Driver
fec_enet_mii_bus: probed
tun: Universal TUN/TAP device driver, 1.6
tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
add wake up source irq 75
fsl-ehci fsl-ehci.0: Freescale On-Chip EHCI Host Controller
fsl-ehci fsl-ehci.0: new USB bus registered, assigned bus number 1
fsl-ehci fsl-ehci.0: irq 75, io base 0x02184000
fsl-ehci fsl-ehci.0: USB 2.0 started, EHCI 1.00
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 1 port detected
add wake up source irq 72
fsl-ehci fsl-ehci.1: Freescale On-Chip EHCI Host Controller
fsl-ehci fsl-ehci.1: new USB bus registered, assigned bus number 2
fsl-ehci fsl-ehci.1: irq 72, io base 0x02184200
fsl-ehci fsl-ehci.1: USB 2.0 started, EHCI 1.00
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 1 port detected
Initializing USB Mass Storage driver...
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
usbcore: registered new interface driver usbserial
usbserial: USB Serial Driver core
USB Serial support registered for FTDI USB Serial Device
usbcore: registered new interface driver ftdi_sio
ftdi_sio: v1.6.0:USB FTDI Serial Converters Driver
mousedev: PS/2 mouse device common for all mice
input: gpio-keys as /devices/platform/gpio-keys/input/input0
input: imx-keypad as /devices/platform/imx-keypad/input/input1
egalax_ts 0-0004: egalax_ts: failed to read firmware version
egalax_ts: probe of 0-0004 failed with error -5
ft5x06: Running new touchscreen driver
input: ft5x06 as /devices/virtual/input/input2
input: rotary-encoder as /devices/platform/rotary-encoder.0/input/input3
Bonanza_ringer_init
Bonanza_ringer_probe called
input: bonanza-ringer as /devices/virtual/input/input4
i2c-core: driver [isl29023] using legacy suspend method
i2c-core: driver [isl29023] using legacy resume method
snvs_rtc snvs_rtc.0: rtc core: registered snvs_rtc as rtc0
i2c /dev entries driver
imx2-wdt imx2-wdt.0: IMX2+ Watchdog Timer enabled. timeout=60s (nowayout=1)
Bluetooth: HCI UART driver ver 2.2
Bluetooth: HCI H4 protocol initialized
Bluetooth: HCI BCSP protocol initialized
Bluetooth: HCILL protocol initialized
Bluetooth: HCIATH3K protocol initialized
sdhci: Secure Digital Host Controller Interface driver
sdhci: Copyright(c) Pierre Ossman
mmc0: SDHCI controller on platform [sdhci-esdhc-imx.2] using ADMA
mmc1: SDHCI controller on platform [sdhci-esdhc-imx.3] using ADMA
mxc_vdoa mxc_vdoa: i.MX Video Data Order Adapter(VDOA) driver probed
VPU initialized
mxc_asrc registered
Thermal calibration data is 0x5775075f
Anatop Thermal registered as thermal_zone0
anatop_thermal_probe: default cooling device is cpufreq!
mmc0: queuing unknown CIS tuple 0x80 (2 bytes)
mmc0: queuing unknown CIS tuple 0x80 (3 bytes)
mmc0: queuing unknown CIS tuple 0x80 (3 bytes)
mmc0: queuing unknown CIS tuple 0x80 (7 bytes)
mmc0: new high speed SDIO card at address 0001
caam caam.0: device ID = 0x0a16010000000100
caam caam.0: job rings = 2, qi = 0
caam caam.0: authenc-hmac-md5-cbc-aes-caam
caam caam.0: authenc-hmac-sha1-cbc-aes-caam
caam caam.0: authenc-hmac-sha224-cbc-aes-caam
caam caam.0: authenc-hmac-sha256-cbc-aes-caam
caam caam.0: authenc-hmac-md5-cbc-des3_ede-caam
caam caam.0: authenc-hmac-sha1-cbc-des3_ede-caam
caam caam.0: authenc-hmac-sha224-cbc-des3_ede-caam
caam caam.0: authenc-hmac-sha256-cbc-des3_ede-caam
caam caam.0: authenc-hmac-md5-cbc-des-caam
caam caam.0: authenc-hmac-sha1-cbc-des-caam
caam caam.0: authenc-hmac-sha224-cbc-des-caam
caam caam.0: authenc-hmac-sha256-cbc-des-caam
caam caam.0: cbc-aes-caam
caam caam.0: cbc-3des-caam
caam caam.0: cbc-des-caam
platform caam_jr.0: registering rng-caam
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
bt_modinit:134
bt_platform_probe:111 Registered bt codec succesfully
mmc1: new high speed DDR MMC card at address 0001
mmcblk0: mmc1:0001 SEM04G 3.68 GiB 
imx-hdmi-soc-dai: probe of imx-hdmi-soc-dai.0 failed with error -12
sgtl5000 0-000a: Failed to get supply 'VDDD': -19
print_constraints: 0-000a: 850 <--> 1600 mV at 1200 mV normal 
mmcblk0boot0: mmc1:0001 SEM04G partition 1 2.00 MiB
mmcblk0boot1: mmc1:0001 SEM04G partition 2 2.00 MiB
 mmcblk0: p1 p2 p3 p4 < p5 p6 >
sgtl5000 0-000a: sgtl5000 revision 17
 mmcblk0boot1: unknown partition table
 mmcblk0boot0: unknown partition table
asoc: sgtl5000 <-> imx-ssi.1 mapping ok
imx_bt_init:192
imx_bt_probe:159
imx_audmux_config:137 slave 6 master 4
imx_3stack_bt_init:98
asoc: bt-dai <-> imx-ssi.2 mapping ok
imx_bt_init:217
ALSA device list:
  #0: sgtl5000-audio
  #1: bt-audio
NET: Registered protocol family 26
TCP cubic registered
NET: Registered protocol family 17
Bluetooth: RFCOMM TTY layer initialized
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM ver 1.11
Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Bluetooth: BNEP filters: protocol multicast
Bluetooth: HIDP (Human Interface Emulation) ver 1.2
lib80211: common routines for IEEE802.11 drivers
Registering the dns_resolver key type
VFP support v0.3: implementor 41 architecture 3 part 30 variant 9 rev 4
Bus freq driver module loaded
Bus freq driver Enabled
mxc_dvfs_core_probe
DVFS driver module loaded
CONSOLE: 
 HiFi: Not enforcing symmetric_rates due to race
 bt: Not enforcing symmetric_rates due to race
bt_params:62 setting PCM format
bt_params:62 setting PCM format
````

## /proc/cpuinfo
````
Processor	: ARMv7 Processor rev 10 (v7l)
processor	: 0
BogoMIPS	: 1975.42

processor	: 1
BogoMIPS	: 1988.29

Features	: swp half fastmult vfp edsp neon vfpv3 
CPU implementer	: 0x41
CPU architecture: 7
CPU variant	: 0x2
CPU part	: 0xc09
CPU revision	: 10

Hardware	: CapCall Bonanza Board V1
Revision	: 0001
Serial		: 1f2169d4eacb3b7d
````

## df -h

````
[(none)]/etc# df -h
Filesystem                Size      Used Available Use% Mounted on
/dev                    440.9M         0    440.9M   0% /dev
/dev/mmcblk0p6            3.6G    101.3M      3.3G   3% /mnt/data
````

Yup, that's right 3.3 GB of available flash.

## # U-Boot printenv

````
Bonanza U-Boot > printenv
bootdelay=1
baudrate=115200
netmask=255.255.255.0
loadaddr=0x10900000
rd_loadaddr=(0x10900000 + 0x300000)
bootargs=console=ttymxc1,115200 video=mxcfb0:dev=ldb,1024x600@60,if=RGB666 fbmem=28M vt.global_cursor_default=0 eth=${ethaddr} bt=${btaddr} NoReset hardware_revision=5 ip=off
bootargs_mmc=set bootargs console=${console} video=${video} eth=${ethaddr} bt=${btaddr} ${resetbutton} boot_image=${boot_image} hardware_revision=${hardware_revision} ip=off
bootcmd=run bootargs_mmc; run auto_bootcmd
bootfile=bonanza.combo
bootflash1=set boot_image 1; run bootargs_mmc; mmc dev 3; mmc read ${loadaddr} ${kernel1blockstart} ${kernel1blockcount}; bootm; || run bootflash2;
bootflash2=set boot_image 2; run bootargs_mmc; mmc dev 3; mmc read ${loadaddr} ${kernel2blockstart} ${kernel2blockcount}; bootm; || run bootflash1;
clearenv=mmc dev 3; mmc erargs ${bootargs} ${resetbutton}; run auto_bootcmd
console=ttymxc1,115200
envblockcount=200
envblockstart=1000
ethprime=FEC0
fdt_high=0xffffffff
hardware_revision=5
initrd_high=0xffffffff
kernel1blockcount=10000
kernel1blockstart=1200
kernel2blockcount=10000
kernel2blockstart=11400
lvds_num=0
netdev=eth0
netmask=255.255.255.0
reset_bootargs=set bootargs console=${console} video=${video} eth=${ethaddr} bt=${btaddr} hardware_revision=${hardware_revision} ip=off; saveenv
splashimage=10800000
splashpos=0,0
ubootblockcount=1000
ubootblockstart=0
video=mxcfb0:dev=ldb,1024x600@60,if=RGB666 fbmem=28M vt.global_cursor_default=0
ethact=FEC0
ethaddr=48:65:EE:24:70:CC
btaddr=48:65:EE:24:70:CD
serverip=192.168.1.107
ipaddr=192.168.1.88
gatewayip=192.168.1.1
stdin=serial
stdout=serial
stderr=serial
resetbutton=NoReset
auto_bootcmd=set boot_image 2; run bootargs_mmc; mmc dev 3; mmc read ${loadaddr} ${kernel2blockstart} ${kernel2blockcount}; bootm; || run bootflash1;

Environment size: 1808/8188 bytes
Bonanza U-Boot > 
````

## U-Boot help

````
Bonanza U-Boot > help
?       - alias for 'help'
autoscr - DEPRECATED - use "source" command instead
base    - print or set address offset
bdinfo  - print Board Info structure
bmp     - manipulate BMP image data
boot    - boot default, i.e., run 'bootcmd'
bootd   - boot default, i.e., run 'bootcmd'
bootm   - boot application image from memory
bootp   - boot image via network using BOOTP/TFTP protocol
clk     - Clock sub system
cls     - clear screen
cmp     - memory compare
coninfo - print console devices and information
cp      - memory copy
crc32   - checksum calculation
destroyenv- destroy enviroment variables stored in medium
dhcp    - boot image via network using DHCP/TFTP protocol
download_mode- download_mode - enter i.MX serial/usb download mode
echo    - echo args to console
erase   - erase FLASH memory
exit    - exit script
ext2load- load binary file from a Ext2 filesystem
ext2ls  - list files in a directory (default /)
fatinfo - print information about filesystem
fatload - load binary file from a dos filesystem
fatls   - list files in a directory (default /)
flinfo  - print FLASH memory information
go      - start application at address 'addr'
help    - print online help
i2c     - I2C sub-system
iminfo  - print header information for application image
imxotp  - One-Time Programable sub-system
imxtract- extract a part of a multi-image
itest   - return true/false on integer compare
loadb   - load binary file over serial line (kermit mode)
loads   - load S-Record file over serial line
loady   - load binary file over serial line (ymodem mode)
loop    - infinite loop on address range
md      - memory display
mii     - MII utility commands
mm      - memory modify (auto-incrementing address)
mmc     - MMC sub system
mmcinfo - display MMC info
mtest   - simple RAM read/write test
mw      - memory write (fill)
nfs     - boot image via network using NFS protocol
nm      - memory modify (constant address)
ping    - send ICMP ECHO_REQUEST to network host
printenv- print environment variables
protect - enable or disable FLASH write protection
rarpboot- boot image via network using RARP/TFTP protocol
regul   - Regulator sub system
reset   - Perform RESET of the CPU
run     - run commands in an environment variable
saveenv - save environment variables to persistent storage
setenv  - set environment variables
sf      - SPI flash sub-system
showvar - print local hushshell variables
sleep   - delay execution for some time
source  - run script from memory
sspi    - SPI utility commands
test    - minimal test like /bin/sh
tftpboot- boot image via network using TFTP protocol
version - print monitor version
Bonanza U-Boot > 
````


