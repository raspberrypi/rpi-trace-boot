# RPI-TRACE-BOOT.SERVICE(8)

## NAME
rpi-trace-boot.service, rpi-trace-boot-quit.service, rpi-trace-boot - Boot trace service

## SYNOPSIS
rpi-trace-boot.service

rpi-trace-boot-quit.service

/sbin/rpi-trace-boot

## DESCRIPTION
rpi-trace-boot is a system service that runs perfetto/tracebox during boot to
collect detailed trace information. The trace is automatically terminated by
the rpi-trace-boot-quit system service once the default.target (see
`systemd.special`(7)) is reached.

## FILES
__/etc/rpi-trace-boot/rpi-trace-boot.conf__
: Configures `rpi-trace-boot` behaviour; __ADDITIONAL_FTRACE_EVENTS__ may be
  specified (see `perfetto`(1)).

__/run/rpi-trace-boot.service/trace__
: The captured boot trace

## SEE ALSO
`perfetto`(1), `systemd.special`(7)
