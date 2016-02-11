# /dev/rfkill

The linux kernel supports a system called rfkill that can disable
wireless transmitters. The userland means of interacting with this
system is via the `/dev/rfkill` character device.

I stumbled upon this while debugging broken wifi on my laptop as I
transitioned from Network Manager to Wicd. `man rfkill` for a nifty
tool for configuring `/dev/rfkill`. Your os (at least mine did) should
recreate `/dev/rfkill` with defaults if you remove it and restart.

### References
 - https://www.kernel.org/doc/Documentation/rfkill.txt
