<script lang="ts">
  import {
    AccordionItem,
    Accordion,
    Carousel,
    Controls,
  } from "flowbite-svelte";
  import {
    ChevronDoubleUpOutline,
    ChevronDoubleDownOutline,
  } from "flowbite-svelte-icons";
  import ptb_1_img1 from "$lib/assets/project_images/ptb_1/image.png";
  import ptb_1_img2 from "$lib/assets/project_images/ptb_1/image copy.png";
  const images_ptb_1 = [
    {
      id: 0,
      src: ptb_1_img1,
      alt: "PTB 1 - Image 1",
    },
    {
      id: 1,
      src: ptb_1_img2,
      alt: "PTB 1 - Image 2",
    },
  ];
</script>

<!--
S.T.A.R. method:
Situation: What was the problem?
Task: What was your specific goal?
Action: What code/tools did you use? (e.g., "Implemented a multi-threaded buffer in C++").
Result: Did it run 20% faster? Did you get an 'A'?
-->
<div class="my-6 p-4 border-2 border-gray-300 bg-gray-500/90 rounded-md">
  <h2 class="font-semibold text-center">
    These are my most interesting projects that I've worked on during either
    work or as a university project.<br />All of them were done for several
    weeks and also have a deep technical documentation aswell as a scientific
    report.
  </h2>
</div>

<div class="my-6 p-4 border-2 border-gray-300 bg-gray-500/90 rounded-md">
  <Accordion flush>
    <span class="text-2xl font-semibold">Praxistransferbericht 1<br /></span>
    <AccordionItem class="text-white flex flex-col justify-between">
      {#snippet header()}<span
          style="font-weight: 600; font-size: 2rem; color: #7dd3fc;"
          >Creation of software for data transfer to cloud servers</span
        >{/snippet}
      {#snippet arrowup()}<ChevronDoubleUpOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      {#snippet arrowdown()}<ChevronDoubleDownOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      <div
        class="grid grid-cols-1 md:grid-cols-[2fr_1fr] gap-6 items-start mt-6"
      >
        <div>
          <span class="font-semibold text-[#7dd3fc]">Situation</span>
          <p>
            Embedded devices often have a "blind spot" in the cloud. To save
            costs and bandwidth, they only send simplified status updates. When
            a critical error occurs, the high-detail log data (precise
            timestamps, raw message types, and full payloads) is only available
            locally via a serial interface. This makes remote debugging
            difficult and requires manual, on-site intervention to extract
            detailed error reports.
            <br /><br />
            <span class="font-semibold text-[#7dd3fc]">Task</span>
            <br />
            My objective was to bridge this gap by developing a bridge application.
            The goal was to capture raw log data from an embedded device via a serial
            interface (UART/Debug Board), stream it to a cloud environment, and enable
            high-fidelity log comparison and error backtracking that is otherwise
            impossible with standard telemetry.
          </p>
          <br />
          <span class="font-semibold text-[#7dd3fc]">Action</span>
          <ul class="list-disc list-inside ml-4">
            <li>
              Data Acquisition: Implemented a listener to read raw data streams
              from a Debug Board via a serial interface.
            </li>
            <li>
              Pipeline Development: Designed a three-stage cloud integration
              concept:
            </li>
            <li>Ingestion: Streaming raw log data from the local machine.</li>
            <li>
              Processing: Developed filters to parse and structure the "noisy"
              raw logs into meaningful formats.
            </li>
            <li>
              Visualization: Configured cloud-based evaluation tools to display
              detailed message types and timing information.
            </li>
            <li>
              Tools & Technologies: C/C++ (Embedded side), Python or Node.js
              (Bridge/Scripting), Serial Communication Protocols, and Cloud
              Storage/Analytics services.
            </li>
          </ul>
          <br />
          <span class="font-semibold text-[#7dd3fc]">Result</span>
          <p>
            I successfully created a workflow that allows developers to perform
            "Root Cause Analysis" remotely with the same level of detail as a
            local debug session. This eliminates the need for manual device
            checking and significantly reduces debugging time by providing full
            visibility into message contents and timing—data that was previously
            discarded to save on cloud costs.
          </p>
        </div>
        <div class="max-w-md mx-auto md:mx-0">
          {#if images_ptb_1.length > 0}
            <Carousel images={images_ptb_1}>
              <Controls />
            </Carousel>
          {/if}
        </div>
      </div>
    </AccordionItem>
  </Accordion>
</div>
<!--
  Das ist Ziel dieser Arbeit ist es, eine Anwendung für die Entwickler zu konstruieren, welche
    Log Daten aus dem Embedded Device nimmt, die durch eine seriele Schnittstelle am
    Computer verbunden ist und diese in die Cloud sendet.
    Diese Methode bietet den Vorteil, die Log Daten direkt in die Cloud zu schicken und
    zu vergleichen. Dadurch kann man bei entstandenen Fehlern eine leichte Rückführung machen,
    da die direkte Ausgabe viel mehr Informationen über die Zeit, die Art der Nachricht
    und dem Inhalt dieser Nachricht gibt und meistens diese Informationen nicht in der Cloud
    einsehbar sind. Geräte, sofern sie eine Cloud Verbindung haben, senden meist nur runtergebrochene
    Informationen, um kosten für die Cloud Dienste zu sparen. Somit muss
    bei Geräten ohne Cloud Verbindung eine manuelle Überprüfung durchgeführt werden, um
    mehr Einsicht über einen Fehler zu haben.
    Hierfür wird zunächst auf das lesen von Daten über ein Debug Board eingegangen. Danach
    auf das grundlegende Konzept der Cloudsicherung: Das senden der rohen Log Daten, das
    filtern dieser Daten und schließlich das auswerten in der Cloud.
  -->

<div class="my-6 p-4 border-2 border-gray-300 bg-gray-500/90 rounded-md">
  <Accordion flush>
    <span class="text-2xl font-semibold">Praxistransferbericht 2<br /></span>
    <AccordionItem class="text-white flex flex-col justify-between">
      {#snippet header()}<span
          style="font-weight: 600; font-size: 2rem; color: #7dd3fc;"
          >Design und Implementierung eines Batteriesimulators</span
        >{/snippet}
      {#snippet arrowup()}<ChevronDoubleUpOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      {#snippet arrowdown()}<ChevronDoubleDownOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      <div
        class="grid grid-cols-1 md:grid-cols-[2fr_1fr] gap-6 items-start mt-6"
      >
        <div>
          <div>
            At MSA Technologies, a new product for the firefighting sector
            required extensive battery testing. However, testing with physical
            batteries is slow, expensive, and difficult to replicate under
            specific failure conditions. To integrate battery testing into the
            company’s automated internal test system, a way to simulate
            consistent and manipulatable battery behavior was needed.
          </div>
          <div>
            My task was to design and implement a Battery Simulator that could
            mimic real-world battery states (voltage, temperature, discharge
            curves) and communicate these values to the product under test. The
            simulator needed to be adjustable so that testers could "inject"
            specific battery values to see how the firefighting equipment
            reacts.
          </div>
          <div>
            Hardware Architecture: Developed a two-tier system using a Raspberry
            Pi Pico (Microcontroller) for the real-time battery logic and a
            Raspberry Pi 4 (Single Board Computer) as the controller. Protocol
            Implementation: Engineered the communication bridge using the I2C
            interface, allowing the product under test to "read" the simulated
            battery data as if it were a real smart battery. Software
            Development: Programmed the simulator to initialize with safe
            default values. Created a control interface allowing users to
            manually manipulate battery parameters for edge-case testing.
            Integration: Developed a custom Software Plugin to integrate the
            simulator directly into the company’s internal automated testing
            framework.
          </div>
          <div>
            I successfully delivered a functional Battery Simulator and a
            corresponding test plugin. This system laid the foundation for all
            future battery testing within the internal framework. It allowed the
            development team to run automated, repeatable tests for firefighting
            equipment, reducing the reliance on physical battery prototypes and
            enabling the simulation of critical low-battery or error states
            safely.
          </div>
        </div>
        <div class="max-w-md mx-auto md:mx-0">
          {#if images_ptb_1.length > 0}
            <Carousel images={images_ptb_1}>
              <Controls />
            </Carousel>
          {/if}
        </div>
      </div>
    </AccordionItem>
  </Accordion>
</div>

<!--
  Im Unternehmen „MSA Technologies und Enterprise Services GmbH“ wird zur Zeit ein
    neues Produkt entwickelt, welches für den Feuerwehrsektor eingesetzt wird. Hierfür soll
    ein Batteriesimulator erstellt werden, welcher das Verhalten der Batterie für dieses Produkt
    simulieren soll. Das Batterieverhalten wird mit einem Mikrocontroller (Raspberry Pi
    Pico) simuliert und kommuniziert mithilfe eines Einplatinencomputer (Raspberry Pi 4)
    und einer I2C-Schnittstelle mit dem zu testenden Produkt.
    Der Batteriesimulator initialisiert mit Standardwerten und diese Standardwerte sind manipulierbar.
    Der Batteriesimulator wird für das Testen in dem firmeninternen Testsystem
    verwendet. Hierfür wird die Grundlage für das Batterietesten gelegt und wie es später in
    dem firmeninternen Testsystem verwendet wird. Auch wird das Konzept für die Kommunikation
    über die I2C-Schnittstelle des zu testenden Produkts erklärt. Die Implementierung
    des Batteriesimulators, sowie die Erstellung eines Plugins1 für das Batterieverhalten im
    firmeninternen Testsystems werden zusammen mit dem Simulatordesign erläutert.
  -->

<div class="my-6 p-4 border-2 border-gray-300 bg-gray-500/90 rounded-md">
  <Accordion flush>
    <span class="text-2xl font-semibold">Praxistransferbericht 3<br /></span>

    <AccordionItem class="text-white flex flex-col justify-between">
      {#snippet header()}<span
          style="font-weight: 600; font-size: 2rem; color: #7dd3fc;"
          >Einrichtung eines HITL-Testsystems mit RaspberryPi’s</span
        >{/snippet}
      {#snippet arrowup()}<ChevronDoubleUpOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      {#snippet arrowdown()}<ChevronDoubleDownOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      <div
        class="grid grid-cols-1 md:grid-cols-[2fr_1fr] gap-6 items-start mt-6"
      >
        <div>
          <div>
            To validate firefighting communication devices, the team needed a
            way to run large-scale Hardware-in-the-Loop (HIL) tests. Testing
            these devices manually was impossible due to the scale required to
            simulate a real-world emergency scenario. The challenge was to
            create a stable, reproducible environment where 64 "Devices Under
            Test" (DUTs) could be controlled and updated simultaneously.
          </div>
          <div>
            My objective was to build and automate a testing rack consisting of
            64 Raspberry Pi 4 nodes, each acting as a simulated firefighting
            device. I needed to ensure that the central Linux controller could
            communicate with every node, execute tests, and recover the entire
            system quickly in case of a software failure.
          </div>
          <div>
            Network Infrastructure: Configured the network communication using
            SSH for remote command execution and DHCP for dynamic IP management
            across the 64-node cluster. Automation & Orchestration: Utilized
            Ansible to automate software deployments and test execution,
            ensuring configuration consistency across all 64 units. System
            Imaging: Developed a custom Linux Gold Image (Speicherabbild) for
            the Raspberry Pis. This allowed for rapid "bare-metal" recovery,
            ensuring that any failing node could be reflashed to a known working
            state within minutes. Documentation: Authored comprehensive
            technical documentation for the Linux control environment to ensure
            long-term maintainability by the engineering team.
          </div>
          <div>
            I successfully implemented a fully automated HIL test rack that
            significantly increased testing throughput. By moving from manual
            checks to an Ansible-driven SSH orchestration, the team could
            simulate complex network behaviors across 64 devices at once. The
            inclusion of the custom system image reduced downtime from hours to
            minutes, creating a "production-ready" test environment for
            safety-critical firefighting hardware.
          </div>
        </div>
        <div class="max-w-md mx-auto md:mx-0">
          {#if images_ptb_1.length > 0}
            <Carousel images={images_ptb_1}>
              <Controls />
            </Carousel>
          {/if}
        </div>
      </div>
    </AccordionItem>
  </Accordion>
</div>
<!--
  Im Unternehmen „MSA Technologies und Enterprise Services GmbH“ wurde ein automatisiertes
    HITL-Testsystem erstellt. Das Testsystem besteht aus 64 Einplatinencomputern
    (Raspberry Pi 4) und einem Linux-Computer. Die Raspberry Pi’s sind mit einem Funkmodul
    ausgestattet und sind das DUT. Das System simuliert einen Teil eines Geräts für
    Feuerwehrleute. Die Tests werden mit Hilfe eines Linux-Computers ausgeführt, welcher
    über das Netzwerkprotokoll SSH mit den Raspberry Pi’s kommuniziert.
    Es wurde zudem ein Speicherabbild für die Raspberry Pi’s und eine detaillierte Dokumentation
    für den Linux-Computer erstellt. Im Falle eines Ausfalls, ist eine schnelle Wiederherstellung
    möglich. Im Folgenden wird die Grundlage von Hardware In The Loop und den
    Netzwerkprotokollen SSH, als auch DHCP, sowie dem Automatisierungswerkzeug Ansible
    gelegt.
    Anschließend gibt es eine Anforderungsanalyse über die verwendete Hard- sowie Software
    und der Kommunikation über das Netzwerkprotokoll SSH.
    Die Implementierung, einschließlich des Aufbaus des Testgestells und der Erstellung des
    Speicherabbilds sowie des Linux-Computers, wird detailliert beschrieben.
  -->

<div class="my-6 p-4 border-2 border-gray-300 bg-gray-500/90 rounded-md">
  <Accordion flush>
    <span class="text-2xl font-semibold">Studienprojekt 1<br /></span>

    <AccordionItem class="text-white flex flex-col justify-between">
      {#snippet header()}<span
          style="font-weight: 600; font-size: 2rem; color: #7dd3fc;"
          >Unbekannten Wegen folgen - Entwicklung eines Roboter-Prototypen zur
          Verfolgung von Linien mithilfe eines PID-Reglers</span
        >{/snippet}
      {#snippet arrowup()}<ChevronDoubleUpOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      {#snippet arrowdown()}<ChevronDoubleDownOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      <div
        class="grid grid-cols-1 md:grid-cols-[2fr_1fr] gap-6 items-start mt-6"
      >
        <div>
          <div>
            The goal was to develop a robotic system capable of navigating
            unknown paths autonomously. The paths were defined by high-contrast
            visual markers (black lines on a white background). The challenge
            lay in selecting the right hardware components and control logic to
            ensure the robot could follow complex curves smoothly without losing
            the track.
          </div>
          <div>
            I was tasked with evaluating various hardware approaches for motor
            control and sensor integration, and subsequently building a
            functional prototype. The objective was to create a modular system
            that could serve as a reliable baseline for future algorithmic
            optimizations.
          </div>
          <div>
            Prototyping: Constructed the physical robot chassis using LEGO
            components, allowing for rapid iteration of sensor placement and
            weight distribution. Hardware Evaluation: Researched and tested
            different hardware interfaces to bridge the gap between high-level
            logic and motor/sensor actuation. Control Implementation: Developed
            the logic to process real-time sensor data and translate it into
            precise motor commands. Testing: Ran comparative evaluations of
            different hardware setups to determine which provided the highest
            reliability and lowest latency during path tracking.
          </div>
          <div>
            I successfully developed a working prototype that accurately follows
            unknown paths. This project established a robust hardware and
            software foundation, proving the feasibility of the chosen
            components. The final design serves as a scalable platform for
            future developments in advanced control theory, such as PID
            (Proportional-Integral-Derivative) tuning.
          </div>
        </div>
        <div class="max-w-md mx-auto md:mx-0">
          {#if images_ptb_1.length > 0}
            <Carousel images={images_ptb_1}>
              <Controls />
            </Carousel>
          {/if}
        </div>
      </div>
    </AccordionItem>
  </Accordion>
</div>
<!--
  Diese Arbeit beschäftigt sich mit dem Bau und der Implementierung eines Roboters
    zur Verfolgung unbekannter Wege. Diese Wege sind durch eine schwarze Linie
    auf weißem Grund definiert. Für den Aufbau werden überwiegend LEGO-Bausteine
    verwendet.
    Das Ziel dieser Arbeit ist die Evaluation verschiedener Ansätze mit unterschiedlichen
    Hardwarekomponenten zur Ansteuerung der Motoren und Sensoren sowie die
    Implementierung eines Prototyps.
    Ein funktionierender Prototyp konnte erfolgreich entwickelt werden, wodurch eine
    grundlegende Basis geschaffen wurde, die in Zukunft für weitere Optimierungen genutzt
    werden kann.
  -->

<div class="my-6 p-4 border-2 border-gray-300 bg-gray-500/90 rounded-md">
  <Accordion flush>
    <span class="text-2xl font-semibold">Studienprojekt 2<br /></span>

    <AccordionItem class="text-white flex flex-col justify-between">
      {#snippet header()}<span
          style="font-weight: 600; font-size: 2rem; color: #7dd3fc;"
          >Simultaneous Localization and Mapping (SLAM) mit Fischertechnik -
          Analyse und Optimierung der Vorgängerarbeit</span
        >{/snippet}
      {#snippet arrowup()}<ChevronDoubleUpOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      {#snippet arrowdown()}<ChevronDoubleDownOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      <div
        class="grid grid-cols-1 md:grid-cols-[2fr_1fr] gap-6 items-start mt-6"
      >
        <div>
          <div>
            A previous study project had demonstrated the feasibility of SLAM
            (Simultaneous Localization and Mapping) using a Fischertechnik
            robotics kit, but the implementation was difficult to maintain. The
            code lacked structure, and the hardware lacked a stable mounting
            solution for the LiDAR sensor, leading to inconsistent data and poor
            system performance.
          </div>
          <div>
            My objective was to transform this prototype into a
            professional-grade system. This involved two main tracks: Software:
            Improving code quality, stability, and performance through modern
            engineering practices. Hardware: Integrating a LiDAR sensor
            physically and logically into the robot's ecosystem.
          </div>
          <div>
            Architectural Refactoring: Extracted existing procedural logic and
            restructured the entire codebase using Object-Oriented Programming
            (OOP). I designed modular classes to handle sensor input, mapping
            logic, and motor control independently. Hardware Integration:
            Designed and 3D-printed a custom mounting bracket to secure the
            LiDAR sensor, ensuring stable data acquisition during movement.
            Performance Optimization: Analyzed and optimized the data processing
            pipeline to ensure the robot could map its environment in real-time
            with higher stability. Future-Proofing: Drafted technical strategies
            for implementing advanced algorithms like RANSAC (Random Sample
            Consensus) for noise reduction and improved data association.
          </div>
          <div>
            I successfully delivered a high-quality, maintainable software
            framework for robotic mapping. The new OOP architecture
            significantly improved system stability and simplified future
            feature integration. The physical LiDAR integration provided clean,
            consistent environmental data, establishing a reliable platform for
            advanced autonomous navigation research.
          </div>
        </div>
        <div class="max-w-md mx-auto md:mx-0">
          {#if images_ptb_1.length > 0}
            <Carousel images={images_ptb_1}>
              <Controls />
            </Carousel>
          {/if}
        </div>
      </div>
    </AccordionItem>
  </Accordion>
</div>

<!--
  Das Ziel dieser Arbeit ist die Analyse und Optimierung des vorangegangenen Studienprojekts
    „Simultaneous Localization and Mapping (SLAM) mit Fischertechnik -
    Analyse und praktische Umsetzung“, das die Umsetzbarkeit von Simultaneous Localization
    and Mapping (SLAM) unter Verwendung des Fischertechnik STEM Coding
    Competition Sets untersucht.
    Der Fokus liegt auf der Verknüpfung des Roboters mit dem LiDAR Sensor und
    der Verbesserung der Qualität und Wartbarkeit des bestehenden Quellcodes. Dafür
    wurden die bisherigen Funktionalitäten des Quellcodes extrahiert und nach dem
    objektorientierten Ansatz in Klassen umstrukturiert, um eine bessere Wartbarkeit,
    Stabilität und Performanz zu gewährleisten. Außerdem wird die Erstellung einer 3D
    gedruckten Halterung thematisiert und dessen Notwendigkeit evaluiert.
    Die Anforderungen konnten weitestgehend umgesetzt werden. Der Quellcode befindet
    sich in einem qualitativ hochwertigen Zustand und der LiDAR-Sensor kann auf
    dem Roboter befestigt werden. Es werden auch mögliche weitere Verbesserungen
    hinsichtlich RANSAC, LiDAR und Datenassoziation diskutiert, um die Funktionalität
    und Effizienz des Systems weiter zu steigern.
  -->

<div class="my-6 p-4 border-2 border-gray-300 bg-gray-500/90 rounded-md">
  <Accordion flush>
    <span class="text-2xl font-semibold">Bachelorthesis<br /></span>

    <AccordionItem class="text-white flex flex-col justify-between">
      {#snippet header()}<span
          style="font-weight: 600; font-size: 2rem; color: #7dd3fc;"
          >Entwicklung eines Funktionstests für einenIndustrie-Router in der
          Produktion</span
        >{/snippet}
      {#snippet arrowup()}<ChevronDoubleUpOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      {#snippet arrowdown()}<ChevronDoubleDownOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      <div
        class="grid grid-cols-1 md:grid-cols-[2fr_1fr] gap-6 items-start mt-6"
      >
        <div>
          <div>
            As production of the "MSA Hub" was relocated in-house, a new system
            was required to verify the hardware before it left the factory. The
            existing process was fragmented and prone to manual errors. To
            ensure high-quality standards for safety equipment, MSA needed a
            centralized, automated system to handle everything from firmware
            flashing to physical label printing.
          </div>
          <div>
            My objective was to conceive, implement, and evaluate a
            comprehensive functional test system with a graphical user interface
            (GUI). The system had to be robust enough for a production
            environment and simple enough to be operated by factory personnel
            with minimal training.
          </div>
          <div>
            Software Architecture: Developed a modular software framework to
            handle diverse tasks like label scanning, firmware programming (for
            both the LRR module and the Hub), and interface testing. UX/UI
            Design: Implemented a "One-Button-App" concept. This simplified
            complex technical sequences into a single-action user experience,
            significantly reducing the potential for human error on the assembly
            line. System Integration: Engineered the logic to automatically
            generate and print device-specific labels only after a successful
            functional test, ensuring no faulty device could be shipped.
            Automation: Integrated automated flashing routines for the internal
            Long Range Radio (LRR) modules and Hub firmware to streamline the
            deployment process.
          </div>
          <div>
            I successfully delivered a production-ready test system that
            optimized the End-of-Line (EOL) testing phase. The modular design
            ensures the system is easily maintainable and scalable. By
            automating the quality assurance process, the system minimized
            manual errors and ensured that every MSA Hub leaving the factory
            meets strict functional and firmware requirements.
          </div>
        </div>
        <div class="max-w-md mx-auto md:mx-0">
          {#if images_ptb_1.length > 0}
            <Carousel images={images_ptb_1}>
              <Controls />
            </Carousel>
          {/if}
        </div>
      </div>
    </AccordionItem>
  </Accordion>
</div>

<!--
  Im Zuge einer Produktionsverlagerung vom Lieferanten zu MSA wurde ein neues Funktionstestsystem
    für den MSA Hub konzipiert und entwickelt. Die vorliegende Arbeit beschreibt die
    Konzeption, Implementierung und Evaluation des Funktionstestsystems mit grafischer Oberfläche.
    Das entwickelte System ist in der Lage, vorhandene Labels am Gerät auszulesen, das interne LRRModul
    und die Hub-Firmware zu programmieren, einen Funktionstest aller relevanten Schnittstellen
    durchzuführen sowie die benötigten Gerätelabels zu generieren und zu drucken. Ziel war es, eine
    zuverlässige und effiziente Lösung zu schaffen, die den EOL-Test optimiert und manuelle Fehlerquellen
    minimiert.
    Die Umsetzung erfolgte in Form eines modularen Software-Frameworks. Ein intuitives „One-Button-
    App“-Konzept führt das Produktionspersonal mit minimalem Einarbeitungsaufwand durch den
    Prüfprozess. Die Implementierung aller Kernfunktionalitäten sorgt für ein robustes und wartbares
    Testsystem, das die Qualitätssicherung des MSA Hubs sicherstellt.
  -->

<div class="my-6 p-4 border-2 border-gray-300 bg-gray-500/90 rounded-md">
  <Accordion flush>
    <span class="text-2xl font-semibold">University project<br /></span>

    <AccordionItem class="text-white flex flex-col justify-between">
      {#snippet header()}<span
          style="font-weight: 600; font-size: 2rem; color: #7dd3fc;"
          >Erdulator</span
        >{/snippet}
      {#snippet arrowup()}<ChevronDoubleUpOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      {#snippet arrowdown()}<ChevronDoubleDownOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      <div
        class="grid grid-cols-1 md:grid-cols-[2fr_1fr] gap-6 items-start mt-6"
      >
        <div>a</div>
        <div class="max-w-md mx-auto md:mx-0">
          {#if images_ptb_1.length > 0}
            <Carousel images={images_ptb_1}>
              <Controls />
            </Carousel>
          {/if}
        </div>
      </div>
    </AccordionItem>
  </Accordion>
</div>
