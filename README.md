# Block-Attacks
IPTABLES commands womit angriffe sehr erschwert werden auf deinem Server/Router.

              -/Blockt Packete in Protokoll formen\-


      - Blockieren von verdächtigem eingehenden Traffic für alle Protokolle: -
- iptables -A INPUT -m conntrack --ctstate NEW -m limit --limit 50/s --limit-burst 20 -j ACCEPT
- iptables -A INPUT -m conntrack --ctstate NEW -j DROP

      - Schützen von spezifischen Ports vor DDoS-Angriffen (zum Beispiel Port 80 für HTTP): -
- iptables -A INPUT -p tcp --dport 80 -m conntrack --ctstate NEW -m limit --limit 50/s --limit-burst 20 -j ACCEPT
- iptables -A INPUT -p tcp --dport 80 -m conntrack --ctstate NEW -j DROP

      - Blockieren von ICMP Flood-Angriffen: -
- iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT
- iptables -A INPUT -p icmp -j DROP

      - Blockieren von SYN Flood-Angriffen: -
- iptables -A INPUT -p tcp --syn -m limit --limit 1/s -j ACCEPT
- iptables -A INPUT -p tcp --syn -j DROP

      - Blockieren von SYN-Flood-Angriffen: - 

- iptables -A INPUT -p tcp ! --syn -m state --state NEW -j DROP

      - Blockieren von Paketen mit den Flags FIN, ACK und SYN gesetzt: -

- iptables -A INPUT -p tcp --tcp-flags ALL FIN,ACK,SYN -j DROP

      - Blockieren von Paketen mit den Flags FIN und ACK gesetzt: -

- iptables -A INPUT -p tcp --tcp-flags ALL FIN,ACK -j DROP

      - Blockieren von Paketen mit dem FIN-Flag gesetzt: -

- iptables -A INPUT -p tcp --tcp-flags ALL FIN -j DROP

      - Blockieren von Paketen mit dem SYN- und RST-Flag gesetzt: -

- iptables -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j DROP

Blockiert einige angriffe und Packete. Sollten fragen sein oder probleme auftreten einfach melden.
