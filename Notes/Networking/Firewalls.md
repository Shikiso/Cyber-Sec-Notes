A firewall is a device within a network responsible for determining what traffic is allowed to enter and exit. There are multiple types of firewalls, such as hardware enterprise ones to simple routers like what you have in your home.
Firewalls operate on the Network and Transport layer of the OSI model.

## Primary Types
| Firewalls                 | Characteristics                                                                                                                                                                                |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Stateless firewalls       | - Basic filtering  <br>- No track of previous connections  <br>- Efficient for high-speed networks                                                                                             |
| Stateful firewalls        | - Recognize traffic by patterns  <br>- Complex rules can be applicable  <br>- Monitor the network connections                                                                                  |
| Proxy firewalls           | - Inspect the data inside the packets as well  <br>- Provides content filtering options  <br>- Provides application control  <br>- Decrypts and inspects SSL/TLS data packets                  |
| Next-generation firewalls | - Provides advanced threat protection  <br>- Comes with an intrusion prevention system  <br>- Identify anomalies based on heuristic analysis  <br>- Decrypts and inspects SSL/TLS data packets |
Use Windows defender to edit firewall rules on windows.
Use netfilter or ufw on linux