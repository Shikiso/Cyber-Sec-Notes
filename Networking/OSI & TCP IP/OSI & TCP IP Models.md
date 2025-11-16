
| Layer Number | Layer Name   | Description                                                                                                                                                                                      | Data types                 |
| ------------ | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------- |
| 7            | Application  | Provides networking options to programs running on a computer.                                                                                                                                   | Data                       |
| 6            | Presentation | Receives data from the application layer. This layer translate the data into<br>a standardized format, as well as handling any encryption, compression or any other transformations to the data. | Data                       |
| 5            | Session      | Attempts to set up connection with other devices across the network. If it fails it sends a error message.                                                                                       | Data                       |
| 4            | Transport    | Choses protocol to use to transmit data                                                                                                                                                          | TCP, segment/UDP, datagram |
| 3            | Network      | Responsible for locating the destination of your request.                                                                                                                                        | Packets                    |
| 2            | Data link    | Focuses on the physical addressing of the transmission. It also presents<br>data in a suitable format. As well as check if received information is corrupted.                                    | Frames                     |
| 1            | Physical     | The physical hardware of your device.                                                                                                                                                            | Bits                       |

| Layer Number | Layer Name        | OSI Layers |
| ------------ | ----------------- | ---------- |
| 4            | Application       | 5,6,7      |
| 3            | Transport         | 4          |
| 2            | Internet          | 3          |
| 1            | Network Interface | 1,2        |
