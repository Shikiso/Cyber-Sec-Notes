## Auxiliary
Any supporting modules such as scanners, crawlers, fuzzers can be found:
`/opt/metasploit-framework/embedded/framework/modules# tree -L 1 auxiliary/

## Encoders
Encoders will allow you to encode the payload in hopes of bypassing a signature-based antivirus. They can be found:
`opt/metasploit-framework/embedded/framework/modules# tree -L 1 encoders/`

## Evaders
Encoders are not a direct attempt at bypassing security features but evaders are. They can be found:
`/opt/metasploit-framework/embedded/framework/modules# tree -L 2 evasion/`

## Exploits
Organized by system. Can be found:
`/opt/metasploit-framework/embedded/framework/modules# tree -L 1 exploits/`

## NOPs
(No Operations) do nothing...They are represented in the Intel x86 CPU family with 0x90, following which the CPU will do nothing for one cycle. They are often used as a buffer to achieve consistent payload sizes. They can be found:
`/opt/metasploit-framework/embedded/framework/modules# tree -L 1 nops/`

## Payloads
Payloads are code used to take advantage of vulnerabilities on the system. They can be found:
`/opt/metasploit-framework/embedded/framework/modules# tree -L 1 payloads/`
You will see four different directories under payloads: adapters, singles, stagers and stages.
- **Adapters:** An adapter wraps single payloads to convert them into different formats. For example, a normal single payload can be wrapped inside a Powershell adapter, which will make a single powershell command that will execute the payload.  

- **Singles:** Self-contained payloads (add user, launch notepad.exe, etc.) that do not need to download an additional component to run.

- **Stagers:** Responsible for setting up a connection channel between Metasploit and the target system. Useful when working with staged payloads. “Staged payloads” will first upload a stager on the target system then download the rest of the payload (stage). This provides some advantages as the initial size of the payload will be relatively small compared to the full payload sent at once.

- **Stages:** Downloaded by the stager. This will allow you to use larger sized payloads.
## Post
Used in the final stage of penetration testing. Can be found:
`/opt/metasploit-framework/embedded/framework/modules# tree -L 1 post/`

# Commands
`msfconsole` to open in terminal. You can use it like a normal terminal but some commands wont work.

To get help on something  - `help <cmd>` For example `help set`

To get information on a module (can use with selected or add path at end) - `info`

To search msfconsole database - `search`
To show information - `show`
- Show options of module - `show options`
- Show payloads - `show payloads`

To select a module - `use <module>`

To go back - `back`

To set a parameter - `set <option> <value>`
Use `setg` to set globally

To unset a parameter (add all to unset all parameters) - `unset`
Use `unsetg` to unset globally

To run a module (add `-z` to background session when successful) - `exploit`
To put a session in background - `background`

List sessions - `sessions`
Select session - `sessions -i <num>`