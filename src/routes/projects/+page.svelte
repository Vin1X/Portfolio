<script lang="ts">
  import {
    AccordionItem,
    Accordion,
    Carousel,
    Controls,
    CarouselIndicators,
  } from "flowbite-svelte";
  import {
    ChevronDoubleUpOutline,
    ChevronDoubleDownOutline,
  } from "flowbite-svelte-icons";
  import ptb_1_io4 from "$lib/assets/project_images/ptb_1/io4.png";
  import ptb_1_cloud from "$lib/assets/project_images/ptb_1/cloudwatch.png";
  import ptb_1_datadog from "$lib/assets/project_images/ptb_1/datadog.png";
  import ptb_1_datadog2 from "$lib/assets/project_images/ptb_1/datadog2.png";
  import ptb_1_rawlogs from "$lib/assets/project_images/ptb_1/rawlogs.png";
  import ptb_1_uart from "$lib/assets/project_images/ptb_1/uart.png";
  import ptb_1_draft from "$lib/assets/project_images/ptb_1/Entwurf.png";

  import ptb_2_construction from "$lib/assets/project_images/ptb_2/ahud_aufbau_2.jpg";
  import ptb_2_block from "$lib/assets/project_images/ptb_2/blockschalt.drawio.png";
  import ptb_2_construction2 from "$lib/assets/project_images/ptb_2/ahud_aufbau_3.1.png";
  import ptb_2_sequence from "$lib/assets/project_images/ptb_2/Sequence Fuel Gauge Simulator.drawio.png";
  import ptb_2_block2 from "$lib/assets/project_images/ptb_2/i2c_hitl_support.drawio.png";
  const images_ptb_1: { id: string; src: string; alt: string }[] = [
    {
      id: "0",
      src: ptb_1_io4,
      alt: "The MSA Altair iO4.",
    },
    {
      id: "1",
      src: ptb_1_draft,
      alt: "Draft of system architecture and workflow.",
    },
    {
      id: "2",
      src: ptb_1_rawlogs,
      alt: "The raw logs read from the Altair io4.",
    },
    {
      id: "3",
      src: ptb_1_cloud,
      alt: "The logs after streaming to the cloud in CloudWatch.",
    },
    {
      id: "4",
      src: ptb_1_datadog,
      alt: "The logs after forwarding to DataDog.",
    },
    {
      id: "5",
      src: ptb_1_datadog2,
      alt: "Example of DataDog visualization of a log entry.",
    },
    {
      id: "6",
      src: ptb_1_uart,
      alt: "UART protocol.",
    },
  ];
  const images_ptb_2: { id: string; src: string; alt: string }[] = [
    {
      id: "0",
      src: ptb_2_construction,
      alt: "The construction of the test setup with the battery simulator and the device under test (DUT).",
    },
    {
      id: "1",
      src: ptb_2_block,
      alt: "Block diagram of the system architecture.",
    },
    {
      id: "2",
      src: ptb_2_construction2,
      alt: "Another view of the test setup construction.",
    },
    {
      id: "3",
      src: ptb_2_sequence,
      alt: "Sequence diagram of the fuel gauge simulator.",
    },
    {
      id: "4",
      src: ptb_2_block2,
      alt: "Block diagram of the I2C HITL support.",
    },
  ];

  let image: HTMLImgAttributes | undefined = $state();
</script>

<!--
S.T.A.R. method:
Situation: What was the problem?
Task: What was your specific goal?
Action: What code/tools did you use? (e.g., "Implemented a multi-threaded buffer in C++").
Result: Did it run 20% faster? Did you get an 'A'?
-->
<div class="my-6 p-6 border-2 border-gray-300 bg-gray-500/90 rounded-md">
  <h2 class="font-semibold text-center">
    These are my most interesting projects that I've worked on during either
    work or as a university project.<br />All of them were done for several
    weeks and also have a deep technical documentation aswell as a scientific
    report.
  </h2>
</div>

<div class="my-6 p-6 border-2 border-gray-300 bg-gray-500/90 rounded-md">
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
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6 auto-rows-max my-2">
        <div class="md:col-span-1 md:row-span-2">
          <span class="font-semibold text-[#7dd3fc]">Situation</span>
          <p>
            Embedded devices typically transmit only minimal status updates to
            the cloud to minimize bandwidth and costs. High-fidelity
            logs—including precise timestamps, raw message types, and full
            payloads—were previously only accessible locally via serial
            interfaces. This created a significant bottleneck for remote
            debugging and cross-location collaboration, leading to increased
            downtime.
            <br /><br />
            <span class="font-semibold text-[#7dd3fc]">Task</span>
            <br />
            My goal was to bridge this gap for the MSA ALTAIR io4 by developing a
            Python-based application to capture raw log data from the device via
            a serial interface, archive it locally, and stream it to a cloud environment.
            This enables high-fidelity log comparison and error backtracking that
            is impossible with standard telemetry.
          </p>
          <br />
          <span class="font-semibold text-[#7dd3fc]">Action</span><br />
          I implemented a modular Python architecture to automate the entire data
          pipeline:
          <ul class="list-disc list-inside ml-4">
            <li>
              Data Acquisition: Developed a real-time listener using UART and
              JTAG Debug Boards to capture logs and store them locally in a
              structured format.
            </li>
            <li>
              Streaming: Integrated the AWS SDK (Boto3) to stream data in
              real-time to AWS CloudWatch, ensuring persistent cloud storage.
            </li>
            <li>
              Presentation & Analytics: Engineered a custom integration to
              forward logs from CloudWatch to Datadog. I created specialized
              dashboards to filter by message type (e.g., error codes) and
              timestamps, transforming raw strings into actionable telemetry.
            </li>
            <li>Technologies: Python, AWS CloudWatch, Datadog, UART, JTAG.</li>
          </ul>
        </div>
        <div class="w-full md:col-span-1 md:row-span-1">
          {#if images_ptb_1.length > 0}
            <Carousel
              images={images_ptb_1}
              onchange={(detail) => (image = detail)}
            >
              <Controls />
              <CarouselIndicators />
            </Carousel>
          {/if}
          <div
            class="mt-2 rounded-sm bg-transparent p-2 text-center border-2 align-middle border-gray-300"
          >
            {image?.alt}
          </div>
        </div>
        <div class="md:col-span-1 md:row-span-1">
          <span class="font-semibold text-[#7dd3fc]">Result</span>
          <p>
            The project fully automated the debugging workflow, allowing
            developers to perform remote Root Cause Analysis with the same level
            of detail as a local session. This eliminated manual data
            distribution and significantly reduced issue resolution time by
            providing immediate, global visibility into granular device
            behavior.
          </p>
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

<div class="my-6 p-6 border-2 border-gray-300 bg-gray-500/90 rounded-md">
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
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6 auto-rows-max my-2">
        <div class="md:col-span-1 md:row-span-2">
          <span class="font-semibold text-[#7dd3fc]">Situation</span>
          <div>
            Testing firefighting equipment with physical batteries is slow,
            expensive, and difficult to replicate under specific failure
            conditions. To integrate battery testing into MSA’s
            Hardware-in-the-Loop (HITL), a solution was needed to simulate
            consistent and manipulatable battery behavior without physical
            hardware.
          </div>
          <br />
          <span class="font-semibold text-[#7dd3fc]">Task</span>
          <div>
            My objective was to design and implement a Battery Simulator capable
            of mimicking real-world battery states—such as voltage, temperature,
            and discharge curves. The system needed to allow testers to "inject"
            specific edge-case values via a control interface to validate how
            the Device Under Test (DUT) reacts to critical battery failures.
          </div>
          <br />
          <span class="font-semibold text-[#7dd3fc]">Action</span><br />
          I developed a modular, two-tier hardware and software architecture:
          <ul class="list-disc list-inside ml-4">
            <li>
              Hardware Architecture: Engineered a hybrid system using a
              Raspberry Pi Pico for low-level, real-time battery logic (register
              based) and a Raspberry Pi 4 as the high-level controller for data
              manipulation.
            </li>
            <li>
              Protocol Implementation: Developed a communication bridge via I2C,
              enabling the DUT to interact with the simulator as if it were a
              genuine "smart" battery.
            </li>
            <li>
              Software & Integration: Programmed the simulator with safe
              initialization defaults and a manual override interface for
              edge-case testing. Also developed a custom software plugin to
              integrate the simulator directly into the company’s internal
              automated testing framework.
            </li>
            <li>
              Technologies: Python, I2C, Raspberry Pi Pico (RP2040), Raspberry
              Pi 4, HIL Testing.
            </li>
          </ul>
        </div>
        <div class="w-full md:col-span-1 md:row-span-1">
          {#if images_ptb_2.length > 0}
            <Carousel images={images_ptb_2}>
              <Controls />
            </Carousel>
          {/if}
        </div>
        <div class="md:col-span-1 md:row-span-1">
          <span class="font-semibold text-[#7dd3fc]">Result</span>
          <div>
            I successfully delivered a functional Battery Simulator and a
            corresponding test plugin. This system laid the foundation for all
            future battery testing within the internal framework. All components
            were build modular so that the plugin could be reused for different
            battery gauges. It allowed the development team to run automated,
            repeatable tests for firefighting equipment, reducing the reliance
            on physical battery prototypes.
          </div>
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

<div class="my-6 p-6 border-2 border-gray-300 bg-gray-500/90 rounded-md">
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
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6 auto-rows-max my-2">
        <div class="md:col-span-1 md:row-span-2">
          <span class="font-semibold text-[#7dd3fc]">Situation</span>
          <div>
            To validate firefighting communication devices, the team needed a
            way to run large-scale Hardware-in-the-Loop (HIL) tests. Testing
            these devices manually was impossible due to the scale required to
            simulate a real-world emergency scenario. The challenge was to
            create a stable, reproducible environment where 64 "Devices Under
            Test" (DUTs) could be controlled and updated simultaneously.
          </div>
          <span class="font-semibold text-[#7dd3fc]">Task</span>
          <div>
            My objective was to build and automate a testing rack consisting of
            64 Raspberry Pi 4 nodes, each acting as a simulated firefighting
            device. I needed to ensure that the central Linux controller could
            communicate with every node, execute tests, and recover the entire
            system quickly in case of a software failure.
          </div>
          <span class="font-semibold text-[#7dd3fc]">Action</span>
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
        </div>
        <div class="w-full md:col-span-1 md:row-span-1">
          {#if images_ptb_1.length > 0}
            <Carousel images={images_ptb_1}>
              <Controls />
            </Carousel>
          {/if}
        </div>
        <div class="md:col-span-1 md:row-span-1">
          <span class="font-semibold text-[#7dd3fc]">Result</span>
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

<div class="my-6 p-6 border-2 border-gray-300 bg-gray-500/90 rounded-md">
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
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6 auto-rows-max my-2">
        <div class="md:col-span-1 md:row-span-2">
          <span class="font-semibold text-[#7dd3fc]">Situation</span>
          <div>
            The goal was to develop a robotic system capable of navigating
            unknown paths autonomously. The paths were defined by high-contrast
            visual markers (black lines on a white background). The challenge
            lay in selecting the right hardware components and control logic to
            ensure the robot could follow complex curves smoothly without losing
            the track.
          </div>
          <span class="font-semibold text-[#7dd3fc]">Task</span>
          <div>
            I was tasked with evaluating various hardware approaches for motor
            control and sensor integration, and subsequently building a
            functional prototype. The objective was to create a modular system
            that could serve as a reliable baseline for future algorithmic
            optimizations.
          </div>
          <span class="font-semibold text-[#7dd3fc]">Action</span>
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
        </div>
        <div class="w-full md:col-span-1 md:row-span-1">
          {#if images_ptb_1.length > 0}
            <Carousel images={images_ptb_1}>
              <Controls />
            </Carousel>
          {/if}
        </div>
        <div class="md:col-span-1 md:row-span-1">
          <span class="font-semibold text-[#7dd3fc]">Result</span>
          <div>
            I successfully developed a working prototype that accurately follows
            unknown paths. This project established a robust hardware and
            software foundation, proving the feasibility of the chosen
            components. The final design serves as a scalable platform for
            future developments in advanced control theory, such as PID
            (Proportional-Integral-Derivative) tuning.
          </div>
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

<div class="my-6 p-6 border-2 border-gray-300 bg-gray-500/90 rounded-md">
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
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6 auto-rows-max my-2">
        <div class="md:col-span-1 md:row-span-2">
          <span class="font-semibold text-[#7dd3fc]">Situation</span>
          <div>
            A previous study project had demonstrated the feasibility of SLAM
            (Simultaneous Localization and Mapping) using a Fischertechnik
            robotics kit, but the implementation was difficult to maintain. The
            code lacked structure, and the hardware lacked a stable mounting
            solution for the LiDAR sensor, leading to inconsistent data and poor
            system performance.
          </div>
          <span class="font-semibold text-[#7dd3fc]">Task</span>
          <div>
            My objective was to transform this prototype into a
            professional-grade system. This involved two main tracks: Software:
            Improving code quality, stability, and performance through modern
            engineering practices. Hardware: Integrating a LiDAR sensor
            physically and logically into the robot's ecosystem.
          </div>
          <span class="font-semibold text-[#7dd3fc]">Action</span>
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
        </div>
        <div class="w-full md:col-span-1 md:row-span-1">
          {#if images_ptb_1.length > 0}
            <Carousel images={images_ptb_1}>
              <Controls />
            </Carousel>
          {/if}
        </div>
        <div class="md:col-span-1 md:row-span-1">
          <span class="font-semibold text-[#7dd3fc]">Result</span>
          <div>
            I successfully delivered a high-quality, maintainable software
            framework for robotic mapping. The new OOP architecture
            significantly improved system stability and simplified future
            feature integration. The physical LiDAR integration provided clean,
            consistent environmental data, establishing a reliable platform for
            advanced autonomous navigation research.
          </div>
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

<div class="my-6 p-6 border-2 border-gray-300 bg-gray-500/90 rounded-md">
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
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6 auto-rows-max my-2">
        <div class="md:col-span-1 md:row-span-2">
          <span class="font-semibold text-[#7dd3fc]">Situation</span>
          <div>
            As production of the "MSA Hub" was relocated in-house, a new system
            was required to verify the hardware before it left the factory. The
            existing process was fragmented and prone to manual errors. To
            ensure high-quality standards for safety equipment, MSA needed a
            centralized, automated system to handle everything from firmware
            flashing to physical label printing.
          </div>
          <span class="font-semibold text-[#7dd3fc]">Task</span>
          <div>
            My objective was to conceive, implement, and evaluate a
            comprehensive functional test system with a graphical user interface
            (GUI). The system had to be robust enough for a production
            environment and simple enough to be operated by factory personnel
            with minimal training.
          </div>
          <span class="font-semibold text-[#7dd3fc]">Action</span>
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
        </div>
        <div class="w-full md:col-span-1 md:row-span-1">
          {#if images_ptb_1.length > 0}
            <Carousel images={images_ptb_1}>
              <Controls />
            </Carousel>
          {/if}
        </div>
        <div class="md:col-span-1 md:row-span-1">
          <span class="font-semibold text-[#7dd3fc]">Result</span>
          <div>
            I successfully delivered a production-ready test system that
            optimized the End-of-Line (EOL) testing phase. The modular design
            ensures the system is easily maintainable and scalable. By
            automating the quality assurance process, the system minimized
            manual errors and ensured that every MSA Hub leaving the factory
            meets strict functional and firmware requirements.
          </div>
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

<div class="my-6 p-6 border-2 border-gray-300 bg-gray-500/90 rounded-md">
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
        <div class="w-full">
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
