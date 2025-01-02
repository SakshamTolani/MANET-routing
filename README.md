# Mobile Ad Hoc (MANET) Simulation and Analysis using OMNET++

This project simulates and analyzes Mobile Ad Hoc Networks (MANETs) using OMNeT++, focusing on the AODV and DSDV protocols. The following sections explain these protocols, their behaviour, and their response to changes in communication range, the number of mobile nodes, and mobility speed.

## Dependencies

To run this simulation, you need the open-source tool [OMNeT++](https://omnetpp.org/download/), a component-based C++ simulation library and framework primarily for network simulators. This project was developed using OMNeT++ version 5.4.1 and the corresponding INET version. Compatibility with other versions is not guaranteed.

## AODV - Definition and Behavior

The **Ad Hoc On-Demand Distance Vector (AODV)** is a reactive on-demand routing protocol designed to improve the Destination-Sequenced Distance-Vector (DSDV) protocol. AODV establishes routes only when needed, maintaining them until the destination is unreachable or the route expires. 

Key features:
- Maintains a routing table with time-limited entries.
- Discovers routes by broadcasting route request (RREQ) messages.
- Uses reverse routes and route reply (RREP) messages to establish paths.
- Handles mobility by restarting the route discovery process or sending link failure notifications.

The main objective of AODV is to minimize network-wide broadcast messages, making it more efficient in dynamic environments.

## DSDV - Definition and Behavior

The **Destination-Sequenced Distance-Vector (DSDV)** is a proactive routing protocol based on the Bellman-Ford algorithm. DSDV maintains consistent routing tables with sequence numbers to prevent loops and stale entries.

Key features:
- Uses periodic updates (full dumps or incremental) to maintain routing tables.
- Selects routes based on sequence numbers and cost metrics.
- Optimizes routing for stable networks but introduces overhead due to frequent updates.

## AODV vs DSDV

- **DSDV** performs better in networks with known routes but generates higher overhead due to constant updates.
- **AODV** reduces overhead by discovering routes on demand, making it more suitable for highly dynamic environments.

## Simulation Analysis

The simulations examine how protocol performance is affected by changes in configuration parameters, focusing on packet loss.

### AODV Analysis

**Base Case Configuration:**
- Number of mobile nodes: 7
- Communication range: 400m
- Mobility speed: 1 m/s
- Duration: 240 seconds

No packet loss occurs with the base configuration when sending 940 packets.

**Impact of Changes:**
1. **Number of mobile nodes:**
   - Fewer or more nodes than 7 increase packet loss.
2. **Communication range:**
   - Reducing the range below 400m significantly increases packet loss.
3. **Mobility speed:**
   - Speeds above 1 m/s lead to higher packet loss.

### DSDV Analysis

**Base Case Configuration:**
- Number of mobile nodes: 6
- Communication range: 650m
- Mobility speed: 0.15 m/s
- Duration: 240 seconds

Packet loss is minimal with the base configuration (53 lost packets out of 940).

**Impact of Changes:**
1. **Number of mobile nodes:**
   - Variations have less impact compared to AODV.
2. **Communication range:**
   - Higher ranges reduce packet loss.
3. **Mobility speed:**
   - Lower speeds result in fewer lost packets.

## Conclusion

- **AODV** requires careful parameter tuning to minimize packet loss.
- **DSDV** is more resilient to configuration changes but introduces higher overhead due to periodic updates.

## References

1. Boukerche, Azzedine. *"Algorithms and Protocols for Wireless and Mobile Ad Hoc Networks."* John Wiley & Sons, 2008.
