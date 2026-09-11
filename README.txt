# Multi-AS BGP, OSPF & EIGRP Enterprise Network Topology

An enterprise-grade network simulation built using **GNS3**, demonstrating full inter-domain and intra-domain routing using **eBGP**, **iBGP**,**EIGRP** and **OSPF**.

---

##  Network Architecture

![Network Topology](./BGP.jpg) 
The network is divided into three Autonomous Systems (AS):

* **AS 100:** Uses **EIGRP** as IGP for internal reachability and connects via **eBGP** to AS 200.
* **AS 200 (Core Transit AS):** 
  * Runs **OSPF Area 0** as the Interior Gateway Protocol (IGP) for core connectivity.
  * Implements **iBGP** full mesh / next-hop propagation across core routers (`R1`, `R2`, `R3`, `R4`).
  * Utilizes `next-hop-self` on edge routers to ensure reachability for external prefixes.
* **AS 300:** Hosts loopback prefixes (`50.1.1.0/24` - `50.1.3.0/24`) and peers with AS 200 via **eBGP**.

---

##  Key Technologies & Features

* **Exterior Gateway Protocol:** eBGP (Inter-AS Routing between AS100-AS200 and AS200-AS300).
* **Interior Gateway Protocol:** iBGP (Intra-AS Routing inside AS 200) + OSPF for underlying IGP transport.
* **BGP Next-Hop Processing:** Configured `neighbor next-hop-self` on perimeter routers to resolve iBGP next-hop reachability issues.
* **Prefix Advertisement:** Network statements for loopback interfaces and static summaries.

---

##  Verification & Results

BGP Table Output showing valid and best paths (`*>`) for external and internal routes:

![BGP Table](./BGP-TABLE.png)

##  Configuration & Documentation

* **Topology Diagram:** Refer to `BGP.jpg` for detailed IP scheme and AS distribution.
* **Device Configurations:** Complete Cisco IOS configurations for all routers (AS 100, AS 200, AS 300) are included in `Configration.txt`.
* **Routing Verification:** BGP routing table output is verified in `BGP-TABLE.png`.
*

