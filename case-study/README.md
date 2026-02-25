# Modernization and Migration of the Umbrella Network Monitoring System  
### Condensed Case Study (EN + PL)

---

# English Version

## 1. Introduction

This condensed case study presents the transformation of a legacy Umbrella Network Monitoring System used by a major telecom operator in Poland. It outlines the business drivers, the redesigned architecture, the delivery approach, and the main outcomes of the modernization effort. It also highlights the analytical methods and practices applied throughout the project.

All detailed artefacts (diagrams, requirements, use cases, user stories, test cases) are included in the full case study document available here:  
[umbrella-nms-case-study.pdf](./umbrella-nms-case-study.pdf)

---

## 2. Business Context and Drivers

The operator relied on a legacy Umbrella NMS to aggregate alarms from multiple underlying systems across mobile, fixed-line, and transport domains. Over time, the platform became increasingly unstable and difficult to maintain. Key issues included:

- outdated and unsupported components  
- performance problems during high alarm bursts  
- frequent freezes and restarts affecting NOC operations  
- limited usability and lack of modern features  
- recurring integration issues with CORBA and SNMP systems  

These challenges affected SLA compliance and slowed down incident handling. A full redesign was required to ensure stability, scalability, and long-term maintainability.

---

## 3. Project Scope and Objectives

The modernization replaced the monolithic system with a distributed microservices architecture. The scope covered:

- independent connectors for each external NMS (CORBA, SNMP, HTTP, REST)  
- dedicated engines for enrichment, input rules, correlation, and reporting  
- a redesigned Core split into separate front-end and back-end services  
- migration and repeated synchronization of historical alarm data  
- new features such as dark mode, map visualization, notifications, and scheduled reports  
- REST-based APIs with JSON support  
- performance, stress, and disaster recovery testing  

The rollout was incremental, with the new system gradually taking over functionality from the legacy platform.

---

## 4. Stakeholders and Collaboration

The project involved System Owners, NOC Operators, OSS Maintenance Teams, Developers, DevOps Engineers, and External NMS Teams. Workshops, user-journey walkthroughs, and iterative reviews ensured alignment between business needs and technical design.

As the operator reorganized internally, additional NOC Teams and a new OSS unit joined the project, which required structured onboarding and documentation.

---

## 5. Key Challenges and Lessons Learned

### Technical Challenges
- Splitting ELK indices for active and cleared alarms to resolve performance issues  
- Migrating from Hazelcast to Redis due to instability during cluster restarts  
- Hardware failures on the operator’s infrastructure during data migration  
- Repeated synchronization of large alarm datasets during parallel operation  
- Connector discrepancies caused by filter syntax differences and improved deduplication logic  
- Correlation engine issues that required rule optimization and loop detection  

### Delivery and Process Challenges
- Poorly documented legacy scripts required reverse engineering  
- Parallel operation of old and new systems introduced synchronization issues  
- Automated tests became outdated as the system evolved  
- Independent front-end and back-end development caused integration delays  
- Integration scope expanded as new NMS platforms were added mid-project  

### Organizational Challenges
- Operator restructuring increased the number of user groups  

### Personal and Team Lessons
- Interdisciplinary work required strong time management  
- Clear communication and repeated validation were essential  
- Earlier user involvement and continuous test maintenance would have reduced rework  

---

## 6. Outcomes

### Technical Outcomes
- The new system handles alarm volumes in the hundreds of thousands per second  
- Microservices and containerization enable horizontal scaling and faster recovery  
- Redis-based ID generation and improved indexing increased stability  
- The platform supports 1.5 times more connectors than the legacy system  

### Operational Outcomes
- Faster UI performance and dark mode improved NOC Operator comfort  
- New modules such as maps, reporting, and notifications expanded operational capabilities  
- Synchronization processes that previously took an hour now complete in minutes  

### Business Outcomes
- Reduced operational risk and improved resilience during high-volume events  
- Easier onboarding of new NMS platforms through connector replication  
- Stronger observability across ELK, Grafana, and system health modules  

### Organizational Outcomes
- Consolidated documentation and knowledge transfer supported the new OSS Team  
- The project created a foundation for future modernization initiatives  

---

## 7. My Role and Responsibilities

My involvement covered the full lifecycle of the project:

- co-creating the initial offer and effort estimates  
- gathering and documenting requirements using Miro, Enterprise Architect, and JIRA  
- preparing prototypes in Axure RP, Figma, and through quick HTML/CSS adjustments  
- supporting coordination during periods of limited PM availability  
- acting as the primary Manual Tester and verifying fixes  
- triaging incoming requests and estimating new functionalities  
- contributing to Confluence documentation and onboarding the OSS Team  

This summary also reflects my analytical approach and the methods I apply as a Business and Systems Analyst.

---

## 8. Conclusion

The modernization of the Umbrella NMS delivered a scalable and resilient platform that significantly improved operational efficiency and system reliability. Despite numerous technical and organizational challenges, the project succeeded thanks to iterative analysis, collaborative design, and disciplined delivery.

For readers who want to explore the project in more depth, more details are included in the full case study document available here:  
[umbrella-nms-case-study.pdf](./umbrella-nms-case-study.pdf)

---

# Polish Version

## 1. Wprowadzenie

To skrócone case study opisuje modernizację systemu Umbrella NMS używanego przez jednego z największych operatorów telekomunikacyjnych w Polsce. Przedstawia główne potrzeby biznesowe, nową architekturę, sposób realizacji projektu oraz najważniejsze rezultaty. Pokazuje również metody analityczne i praktyki stosowane podczas całego procesu.

Pełny zestaw artefaktów, w tym diagramy, wymagania, przypadki użycia, user stories i przykładowe scenariusze testowe, znajduje się w pełnym dokumencie:  
[umbrella-nms-case-study.pdf](./umbrella-nms-case-study.pdf)

---

## 2. Kontekst biznesowy i potrzeby

Operator korzystał z przestarzałego systemu Umbrella NMS, który agregował alarmy z wielu systemów NMS w obszarach mobilnych, stacjonarnych i transportowych. Z czasem platforma stała się niestabilna i trudna w utrzymaniu. Najważniejsze problemy obejmowały:

- przestarzałe i niewspierane komponenty  
- problemy wydajnościowe przy dużych wolumenach alarmów  
- częste zawieszenia i restarty wpływające na pracę NOC  
- brak nowoczesnych funkcji i ograniczona użyteczność  
- powtarzające się problemy integracyjne z systemami CORBA i SNMP  

Problemy te wpływały na SLA i opóźniały obsługę incydentów. Konieczna była pełna przebudowa systemu.

---

## 3. Zakres i cele projektu

Modernizacja polegała na zastąpieniu monolitu architekturą mikroserwisową. Zakres obejmował:

- niezależne konektory dla każdego NMS (CORBA, SNMP, HTTP, REST)  
- dedykowane silniki: enrichment, input rules, correlation, reporting  
- nowy Core podzielony na front-end i back-end  
- migrację i wielokrotną synchronizację danych historycznych  
- nowe funkcje: dark mode, mapa, powiadomienia, raporty cykliczne  
- API oparte na REST i JSON  
- testy wydajnościowe, obciążeniowe i DR  

Wdrożenie odbywało się stopniowo, równolegle z działaniem starego systemu.

---

## 4. Interesariusze i współpraca

W projekt zaangażowani byli Administratorzy, Operatorzy NOC, Zespół OSS, Deweloperzy, DevOps oraz Zespoły NMS. Warsztaty, analiza ścieżek użytkownika i iteracyjne przeglądy zapewniały zgodność rozwiązania z potrzebami biznesowymi.

W trakcie reorganizacji operatora do projektu dołączyły kolejne Zespoły NOC oraz nowo utworzona jednostka OSS, co wymagało dodatkowego wdrożenia i dokumentacji.

---

## 5. Kluczowe wyzwania i wnioski

### Wyzwania techniczne
- Podział indeksów ELK dla alarmów aktywnych i wyczyszczonych  
- Migracja z Hazelcast na Redis  
- Awaria dysków podczas migracji danych  
- Wielokrotna synchronizacja dużych wolumenów danych  
- Różnice w działaniu konektorów i filtrów  
- Problemy z regułami korelacyjnymi i zapętleniami  

### Wyzwania procesowe
- Słaba dokumentacja starych skryptów  
- Równoległe działanie starego i nowego systemu  
- Zdezaktualizowane testy automatyczne  
- Niezależny rozwój front-endu i back-endu  
- Rosnący zakres integracji  

### Wyzwania organizacyjne
- Zmiany strukturalne po stronie operatora  

### Wnioski osobiste
- Konieczność dobrej organizacji czasu  
- Znaczenie komunikacji i weryfikacji założeń  
- Potrzeba wcześniejszego zaangażowania użytkowników i utrzymania testów  

---

## 6. Rezultaty

### Rezultaty techniczne
- Obsługa setek tysięcy alarmów na sekundę  
- Skalowanie horyzontalne i szybsze odzyskiwanie po awarii  
- Stabilniejsze generowanie ID dzięki Redis  
- Obsługa większej liczby konektorów niż w systemie legacy  

### Rezultaty operacyjne
- Szybszy interfejs i tryb nocny  
- Nowe moduły: mapa, raporty, powiadomienia  
- Znacznie szybsza synchronizacja danych  

### Rezultaty biznesowe
- Mniejsze ryzyko operacyjne  
- Łatwiejsze podłączanie nowych NMS  
- Lepsza obserwowalność systemu  

### Rezultaty organizacyjne
- Uporządkowana dokumentacja  
- Wsparcie dla nowego Zespołu OSS  

---

## 7. Moja rola i odpowiedzialności

Moje zadania obejmowały:

- współtworzenie oferty i estymacji  
- zbieranie i dokumentowanie wymagań (Miro, EA, JIRA)  
- przygotowywanie prototypów (Axure, Figma, HTML/CSS)  
- wsparcie koordynacji przy ograniczonej dostępności PM  
- testy manualne i weryfikacja poprawek  
- triage zgłoszeń i estymacja nowych funkcji  
- tworzenie dokumentacji i wsparcie wdrożenia Zespołu OSS  

Podsumowanie odzwierciedla moje podejście analityczne i sposób pracy jako Analityk Biznesowo-Systemowy.

---

## 8. Podsumowanie

Modernizacja Umbrella NMS dostarczyła skalowalną i odporną platformę, która znacząco poprawiła efektywność operacyjną i stabilność systemu. Pomimo licznych wyzwań technicznych i organizacyjnych projekt zakończył się sukcesem dzięki iteracyjnej analizie, współpracy i konsekwentnej realizacji.

Pełny zestaw diagramów, wymagań, przypadków użycia, user stories i scenariuszy testowych znajduje się w pełnym dokumencie:
[umbrella-nms-case-study.pdf](./umbrella-nms-case-study.pdf)
