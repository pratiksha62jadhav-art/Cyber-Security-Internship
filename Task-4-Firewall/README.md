# Task 4 – Setup and Use a Firewall on Windows

## Objective
Configure and test basic firewall rules to allow or block network traffic.

## Tool Used
- Windows Defender Firewall with Advanced Security

## Work Performed
1. Opened Windows Defender Firewall with Advanced Security.
2. Created an inbound firewall rule for TCP port 23.
3. Configured the rule to block the connection.
4. Applied the rule to Domain, Private, and Public profiles.
5. Tested port 23 using Test-NetConnection.
6. The test returned `TcpTestSucceeded : False`.
7. Verified that the firewall rule was enabled and set to Block.
8. Removed the test rule after testing.

## Result
TCP port 23 was tested and the firewall rule was successfully configured and removed after testing.

## Conclusion
A Windows firewall can filter network traffic based on rules such as protocol, port, direction, and action.
