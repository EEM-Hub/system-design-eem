---
source: sources/wiki-Hotel_reservation_system.md
source_url: https://en.wikipedia.org/wiki/Hotel_reservation_system
---

## Computer Reservation Systems (CRS) and Global Distribution Systems (GDS)

Computer reservation systems (CRS), also called central reservation systems, are computerized platforms for storing, retrieving, and transacting travel-related bookings — originally built for airlines, then extended to hotels, car rentals, rail, and other travel services. Airlines originally operated their own CRSs, but most have since outsourced to Global Distribution Systems (GDSs), which aggregate multiple providers and serve travel agencies and consumers via internet gateways.

## Key Concepts

- **CRS vs GDS**: A CRS is an airline's own reservation system; a GDS aggregates multiple airlines (and other travel products) into a single distribution platform accessible to travel agents and consumers.
- **Passenger Service System (PSS)**: Airline reservation systems may be part of a larger PSS, which also includes airline inventory and departure control systems.
- **Single point of failure**: Centralized CRS/GDS architectures are vulnerable to network-wide system disruptions (documented outages at American Airlines/Sabre, Southwest, Virgin/Rex).
- **Neutrality**: US regulations (by 1987) required CRSs to display flights neutrally rather than favoring the owning airline. European systems lagged but trended the same direction.
- **Disintermediation**: Airlines increasingly sell directly through their own websites or via direct connections to travel agencies to bypass GDS fees.

## Historical Timeline

- **1958**: MARS-1 (Japan) — world's first computerized seat reservation system for trains, built by Hitachi for Japanese National Railways. Used transistor computer with 400,000-bit magnetic drum memory.
- **1962**: ReserVec (Trans-Canada Airlines / Ferranti Canada) — first airline system with remote terminals in all ticketing offices, ~1 second response time.
- **1960**: SABRE launched (American Airlines + IBM) — became the world's first online transaction processing (OLTP) system when fully completed in December 1964.
- **1965**: PANAMAC (Pan Am), DELTAMATIC (Delta) launched — both developed by IBM alongside SABRE as part of the SABER joint project.
- **1965**: IBM generalized SABRE work into PARS (Programmed Airline Reservation System) — became industry standard by 1971.
- **1976**: United Airlines opened Apollo to travel agents; Travicom launched in UK as the world's first multi-access reservations system (49 airlines, 97% of UK airline bookings by 1987).
- **1978**: US Airline Deregulation Act made efficient CRS critical for competitive advantage.
- **1987**: Amadeus consortium formed (Air France, Lufthansa); launched 1992.
- **1990**: Worldspan formed (Delta, Northwest, TWA).
- **1993**: Galileo GDS formed (British Airways, KLM, United Airlines, others) — evolved from Apollo.

## Major Systems Reference

| System | Origin | Key Fact |
|--------|--------|----------|
| **Sabre** | American Airlines (1960) | First OLTP system; now serves 400+ airlines, 88K hotels |
| **Amadeus** | Air France/Lufthansa (1987) | Largest GDS; 144 PSS airline customers, 90K travel agencies in 195 countries |
| **Travelport** | Merger of Apollo (1971), Galileo (1987), Worldspan (1990) | Three legacy GDSs consolidated |
| **TravelSky** | Chinese state system | Serves Air China, China Eastern, China Southern, Hainan |
| **New Skies (Navitaire)** | Low-cost carrier focus | Powers Ryanair, IndiGo, AirAsia, Wizz Air, Spirit, Frontier, etc. |
| **MARS** | JNR/Hitachi (1958) | Japan Railways train reservation; still in use |
| **Crane (Hitit)** | Turkish origin | Niche/regional airlines including PIA, Pegasus |
| **KIU** | Latin American focus | 20+ airlines across Latin America, Africa, Europe |

## Relationships

- **Airline Reservations System**: The airline-specific component within a CRS; may integrate into a broader Passenger Service System (PSS).
- **Passenger Service System (PSS)**: Encompasses reservations, inventory management, and departure control.
- **Departure Control System (DCS)**: Handles check-in, boarding, load control — downstream of the reservation system.
- **Passenger Name Record (PNR)**: The core data record created and managed by the CRS for each booking.
- **Travel Technology**: Broader field encompassing CRS/GDS plus online travel agencies, metasearch, and direct booking channels.
- **ARINC / SITA**: Telecommunications and IT infrastructure providers that underpin CRS/GDS communications networks.
- **Codeshare Agreements**: CRS/GDS systems must handle multi-carrier bookings enabled by codeshares.
- **Overbooking/Overselling**: CRS systems manage inventory that enables (and must control) overbooking practices.

## Exam-Relevant Points

- MARS-1 (1958, Hitachi/JNR) was the world's first computerized seat reservation system (trains, not airlines).
- SABRE (completed December 1964) was the world's first online transaction processing (OLTP) system.
- ReserVec (1962, Trans-Canada Airlines) was the first airline CRS with remote agent terminals.
- Travicom (1976, UK) was the world's first multi-access reservation system connecting multiple airlines to travel agents.
- IBM's PARS became the industry-standard airline reservation platform by 1971; American Airlines migrated SABRE to PARS-based architecture 1971–1973.
- US government mandated CRS display neutrality by 1987.
- The four major GDS families: Sabre, Amadeus, Travelport (Apollo+Galileo+Worldspan), and TravelSky.
- Navitaire's New Skies dominates the low-cost carrier segment.
- CRS systems are part of the larger Passenger Service System (PSS) alongside inventory and departure control.
- Modern trend: airlines bypass GDS fees via direct website sales and direct-connect programs (e.g., American Airlines Direct Connect).
- Centralized CRS architecture creates vulnerability to network-wide outages affecting entire airlines simultaneously.
