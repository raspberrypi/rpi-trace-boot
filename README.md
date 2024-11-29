# Raspberry Pi Boot Trace Service

Raspberry Pi Boot Trace Service

The Raspberry Pi Boot Trace Service automatically collects highly detailed
[trace](https://perfetto.dev/docs/tracing-101#tracing) information during
system boot. [Perfetto's](https://perfetto.dev) tracebox tool is started during
boot to capture scheduling and syscall information; tracebox is stopped
following `boot-complete`.

- To install on Raspberry Pi OS, use `sudo apt update && sudo apt install
  rpi-trace-boot`.
- Reboot the device to capture a boot trace.

## How to use Raspberry Pi Boot Trace Service

Once installed, you simply need to restart your device to capture a boot trace.
The trace is available at `/run/rpi-trace-boot.service/trace` and can be
inspected using the [Perfetto UI Tool](https://ui.perfetto.dev). Alternatively,
the boot trace can be accessed via the boot analysis report if
[`rpi-analyse-boot`](https://github.com/raspberrypi/rpi-analyse-boot) has been
installed.

## Configuration

Whilst rpi-trace-boot captures scheduling and syscall information by default,
additional events may also be captured; a full list of these can be found in
`/sys/kernel/debug/tracing/available_events`. For example, to capture console
printk and all rcu events, ensure the configuration file
`/etc/rpi-trace-boot/rpi-trace-boot.conf` contains the following:
```
ADDITIONAL_FTRACE_EVENTS=printk:console rcu/*
```

## Building

On Raspberry Pi OS:
```
gbp buildpackage --git-debian-branch=main -uc -us
sudo dpkg -i ../rpi-trace-boot_<version>_all.deb
```
