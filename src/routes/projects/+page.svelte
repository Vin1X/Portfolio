<script lang="ts">
  import {
    AccordionItem,
    Accordion,
    Carousel,
    Controls,
    CarouselIndicators,
    Indicator,
    Button,
  } from "flowbite-svelte";
  import {
    ChevronDoubleUpOutline,
    ChevronDoubleDownOutline,
    CaretRightOutline,
    CaretLeftOutline,
  } from "flowbite-svelte-icons";
  import ptb_1_io4 from "$lib/assets/project_images/ptb_1/io4_scaled.webp";
  import ptb_1_cloud from "$lib/assets/project_images/ptb_1/cloudwatch_scaled.webp";
  import ptb_1_datadog from "$lib/assets/project_images/ptb_1/datadog_scaled.webp";
  import ptb_1_datadog2 from "$lib/assets/project_images/ptb_1/datadog2_scaled.webp";
  import ptb_1_rawlogs from "$lib/assets/project_images/ptb_1/rawlogs_scaled.webp";
  import ptb_1_uart from "$lib/assets/project_images/ptb_1/uart_scaled.webp";
  import ptb_1_draft from "$lib/assets/project_images/ptb_1/entwurf_scaled.webp";

  import ptb_2_construction from "$lib/assets/project_images/ptb_2/aufbau_scaled.webp";
  import ptb_2_block from "$lib/assets/project_images/ptb_2/blockschalt.webp";
  import ptb_2_construction2 from "$lib/assets/project_images/ptb_2/aufbau2_scaled.webp";
  import ptb_2_sequence from "$lib/assets/project_images/ptb_2/sequence_diagram_scaled.webp";
  import ptb_2_block2 from "$lib/assets/project_images/ptb_2/i2c_hitl_support_scaled.webp";

  import ptb_3_rack_strom from "$lib/assets/project_images/ptb_3/rack_strom_scaled.webp";
  import ptb_3_rack from "$lib/assets/project_images/ptb_3/rack_scaled.webp";
  import ptb_3_raspi_mount from "$lib/assets/project_images/ptb_3/raspi_mount_scaled.webp";
  import ptb_3_raspi_close from "$lib/assets/project_images/ptb_3/raspi_close_scaled.webp";
  import ptb_3_aufbau from "$lib/assets/project_images/ptb_3/aufbau_scaled.webp";
  import ptb_3_dhcp from "$lib/assets/project_images/ptb_3/dhcp_scaled.webp";

  import stud_1_front from "$lib/assets/project_images/stud_1/robot_front.webp";
  import stud_1_track from "$lib/assets/project_images/stud_1/track.webp";
  import stud_1_back from "$lib/assets/project_images/stud_1/robot_back.webp";
  import stud_1_build from "$lib/assets/project_images/stud_1/robot_build.webp";
  import stud_1_drawing from "$lib/assets/project_images/stud_1/drawing.webp";
  import stud_1_corner from "$lib/assets/project_images/stud_1/robot_cornering.webp";

  import stud_2_data_assos_2 from "$lib/assets/project_images/stud_2/data_assos_2.webp";
  import stud_2_data_assos_2_ransac from "$lib/assets/project_images/stud_2/data_assos_2_ransac.webp";
  import stud_2_aufbau from "$lib/assets/project_images/stud_2/aufbau.webp";
  import stud_2_lidar from "$lib/assets/project_images/stud_2/lidar.webp";
  import stud_2_teststrecke_empty from "$lib/assets/project_images/stud_2/teststrecke_empty.webp";
  import stud_2_teststrecke from "$lib/assets/project_images/stud_2/teststrecke.webp";
  import stud_2_ransac_error from "$lib/assets/project_images/stud_2/ransac_error.webp";
  import stud_2_3dprint from "$lib/assets/project_images/stud_2/3dprint.webp";
  import stud_2_clustering_lidar from "$lib/assets/project_images/stud_2/clustering_lidar.webp";
  import stud_2_slam_objects from "$lib/assets/project_images/stud_2/slam_objects.webp";

  import ba_msa_hub from "$lib/assets/project_images/bachelor/msa_hub.webp";
  import ba_functional_test from "$lib/assets/project_images/bachelor/functional_test.webp";
  import ba_architektur from "$lib/assets/project_images/bachelor/architektur.webp";
  import ba_architecture from "$lib/assets/project_images/bachelor/architecture.webp";
  import ba_sequence_diagram from "$lib/assets/project_images/bachelor/sequence_diagram.webp";
  import ba_app_draft_error from "$lib/assets/project_images/bachelor/app_draft_error.webp";
  import ba_led from "$lib/assets/project_images/bachelor/led.webp";

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
  const images_ptb_3: { id: string; src: string; alt: string }[] = [
    {
      id: "0",
      src: ptb_3_rack_strom,
      alt: "Back view of the testing rack.",
    },
    {
      id: "1",
      src: ptb_3_rack,
      alt: "Front view of the testing rack with 64 Raspberry Pi's as devices under test (DUTs).",
    },
    {
      id: "2",
      src: ptb_3_raspi_mount,
      alt: "Picture from a rack slot containing 4 Raspberry Pi's mounted with a custom 3D printed mount.",
    },
    {
      id: "3",
      src: ptb_3_raspi_close,
      alt: "Close up picture of a Raspberry Pi with expansion board mounted in the rack.",
    },
    {
      id: "4",
      src: ptb_3_dhcp,
      alt: "Diagram on how DHCP works.",
    },
    {
      id: "5",
      src: ptb_3_aufbau,
      alt: "MSA environment of the M1.",
    },
  ];
  const images_stud_1: { id: string; src: string; alt: string }[] = [
    {
      id: "0",
      src: stud_1_front,
      alt: "Picture of the robot from the front.",
    },
    {
      id: "1",
      src: stud_1_track,
      alt: "Test track that was used for testing the robot.",
    },
    {
      id: "2",
      src: stud_1_back,
      alt: "Frontal view of the robot. Displaying the RaspberryPi and the Sensors.",
    },
    {
      id: "3",
      src: stud_1_build,
      alt: "Schematic drawing of the robot build for calculating the radiuses for the PID controller.",
    },
    {
      id: "4",
      src: stud_1_drawing,
      alt: "Diagram of the loop of the control logic for the robot.",
    },
    {
      id: "5",
      src: stud_1_corner,
      alt: "Example schematic of the robot approaching a sharp corner.",
    },
  ];
  const images_stud_2: { id: string; src: string; alt: string }[] = [
    {
      id: "0",
      src: stud_2_data_assos_2,
      alt: "Picture of the robot from the top.",
    },
    {
      id: "1",
      src: stud_2_data_assos_2_ransac,
      alt: "Diagram of the data association process with RANSAC for outlier rejection.",
    },
    {
      id: "2",
      src: stud_2_aufbau,
      alt: "Close up picture of the robot with the controller and LIDAR.",
    },
    {
      id: "3",
      src: stud_2_lidar,
      alt: "Picture of the LIDAR sensor.",
    },
    {
      id: "4",
      src: stud_2_teststrecke_empty,
      alt: "Picture of the test track without any objects.",
    },
    {
      id: "5",
      src: stud_2_teststrecke,
      alt: "Picture of the test track with objects and the robot.",
    },
    {
      id: "6",
      src: stud_2_ransac_error,
      alt: "Example of the error of the RANSAC algorithm when there are too many outliers in the data.",
    },
    {
      id: "7",
      src: stud_2_3dprint,
      alt: "Picture of the 3D printed mount.",
    },
    {
      id: "8",
      src: stud_2_clustering_lidar,
      alt: "Example of the clustering of data points",
    },
    {
      id: "9",
      src: stud_2_slam_objects,
      alt: "All objects that were used for programming the algorithm.",
    },
  ];
  const images_ba: { id: string; src: string; alt: string }[] = [
    {
      id: "0",
      src: ba_msa_hub,
      alt: "Picture of MSA Hub.",
    },
    {
      id: "1",
      src: ba_functional_test,
      alt: "Draft of the GUI of the functional test.",
    },
    {
      id: "2",
      src: ba_architektur,
      alt: "Diagram of the system architecture.",
    },
    {
      id: "3",
      src: ba_architecture,
      alt: "Diagram of the software architecture of the application.",
    },
    {
      id: "4",
      src: ba_sequence_diagram,
      alt: "Sequence diagram of the application's workflow.",
    },
    {
      id: "5",
      src: ba_app_draft_error,
      alt: "Draft of the GUI of the application showing an error message when validation fails.",
    },
    {
      id: "6",
      src: ba_led,
      alt: "The MSA Hub with all LEDs active indicating a successful functional test.",
    },
  ];

  let image: HTMLImgAttributes | undefined = $state();
  let image2: HTMLImgAttributes | undefined = $state();
  let image3: HTMLImgAttributes | undefined = $state();
  let image4: HTMLImgAttributes | undefined = $state();
  let image5: HTMLImgAttributes | undefined = $state();
  let image6: HTMLImgAttributes | undefined = $state();
</script>

<!--
S.T.A.R. method:
Situation: What was the problem?
Task: What was your specific goal?
Action: What code/tools did you use? (e.g., "Implemented a multi-threaded buffer in C++").
Result: Did it run 20% faster? Did you get an 'A'?
-->
<div
  class="bg-slate-900/30 backdrop-blur-xl p-6 border-2 border-white/40 rounded-3xl"
>
  <h2 class="font-semibold text-center">
    These are my most interesting projects that I've worked on during either
    work or as a university project.<br />All of them were done for several
    weeks and also have a deep technical documentation aswell as a scientific
    report.
  </h2>
</div>

<!-- Bachelorthesis -->
<div
  class="bg-slate-900/30 backdrop-blur-xl my-8 p-6 border-2 border-white/40 rounded-3xl"
>
  <Accordion flush>
    <span class="text-2xl font-semibold">Bachelorthesis<br /></span>

    <AccordionItem class="text-white flex flex-col justify-between">
      {#snippet header()}<span
          style="font-weight: 600; font-size: 2rem; color: #7dd3fc;"
          >Development of a functional test for an industrial router in
          production</span
        >{/snippet}
      {#snippet arrowup()}<ChevronDoubleUpOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      {#snippet arrowdown()}<ChevronDoubleDownOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      <div
        class="grid grid-cols-1 md:grid-cols-2 gap-6 auto-rows-max my-2 text-xl"
      >
        <div class="md:col-span-1 md:row-span-2">
          <span class="font-semibold text-[#7dd3fc]">Situation</span>
          <div>
            With the in house relocation of the "<a
              href="https://de.msasafety.com/p/000010001900011600?&locale=en&default=1"
              >MSA Hub</a
            >" production, a specialized system was required to verify hardware
            integrity and automate firmware deployment. The existing process was
            fragmented and prone to manual errors, risking the high-quality
            standards of safety-critical equipment. The goal was to align the
            production line with a modern, automated solution.
          </div>
          <br />
          <span class="font-semibold text-[#7dd3fc]">Task</span>
          <div>
            My objective was to conceive, implement, and evaluate a
            comprehensive functional test system with a Graphical User Interface
            (GUI). The system had to handle complex tasks from low-level
            programming to label printing while remaining simple enough for
            factory personnel to operate with minimal training.
          </div>
          <br />
          <span class="font-semibold text-[#7dd3fc]">Action</span><br />
          I engineered a modular automation platform using professional communication
          and debugging standards:
          <ul class="list-disc list-inside ml-4">
            <li>
              Advanced Debugging & Flashing: Integrated JTAG and Serial Wire
              Debug (SWD) interfaces to automate firmware programming for the
              <a
                href="https://www.amd.com/en/products/system-on-modules/what-is-a-som.html#som"
                >System On Module (SoM)</a
              > and the internal Long Range Radio (LRR) components.
            </li>
            <li>
              Network Diagnostics: Utilized ICMP-based routines to verify
              network connectivity and implemented DHCP management to ensure
              reliable communication with the Device Under Test (DUT).
            </li>
            <li>
              Software Orchestration: Developed a modular framework using Python
              for inter-process communication, ensuring a decoupled and
              maintainable architecture.
            </li>
            <li>
              Configuration Management: Leveraged YAML for human-readable system
              configurations, allowing for easy updates to test parameters
              without changing the core codebase.
            </li>
            <li>
              UX/UI Design: Created a "One-Button-App" to simplify the execution
              of complex technical sequences into a single-action user
              experience.
            </li>
            <li>
              Technologies: Python (PyQt/PySide), JTAG, SWD, SoM (System On
              Module), ICMP, DHCP, TCP/IP, REST API, YAML, Linux, Shell
              Scripting.
            </li>
          </ul>
        </div>
        <div class="w-full md:col-span-1 md:row-span-1">
          {#if images_ba.length > 0}
            <Carousel
              images={images_ba}
              onchange={(detail) => (image6 = detail)}
            >
              <Controls>
                {#snippet children(changeSlide)}
                  <Button
                    pill
                    class="absolute start-4 top-1/2 -translate-y-1/2 p-2 font-bold bg-[#7dd3fc]"
                    onclick={() => changeSlide(false)}
                  >
                    <CaretLeftOutline />
                  </Button>
                  <Button
                    pill
                    class="absolute end-4 top-1/2 -translate-y-1/2 p-2 font-bold bg-[#7dd3fc]"
                    onclick={() => changeSlide(true)}
                  >
                    <CaretRightOutline />
                  </Button>
                {/snippet}
              </Controls>
              <CarouselIndicators>
                {#snippet children({ selected, index })}
                  <Indicator
                    color={selected ? "blue" : "gray"}
                    class="h-5 w-5 border border-white text-white {selected
                      ? 'opacity-100'
                      : 'opacity-90'}"
                  >
                    {index}
                  </Indicator>
                {/snippet}
              </CarouselIndicators>
            </Carousel>
          {/if}
          <div
            class="mt-2 rounded-sm bg-transparent p-2 text-center border-2 align-middle border-gray-300"
          >
            {image6?.alt}
          </div>
        </div>
        <div class="md:col-span-1 md:row-span-1">
          <span class="font-semibold text-[#7dd3fc]">Result</span>
          <div>
            The production ready system successfully optimized the EOL phase,
            ensuring every MSA Hub meets strict requirements before shipment. By
            automating the quality gate and integrating hardware level
            verification, I significantly reduced Operational Expenditures
            (OPEX) and eliminated most manual errors in the production process.
          </div>
        </div>
      </div>
    </AccordionItem>
  </Accordion>
</div>

<!-- Studienprojekt 2 -->
<div
  class="bg-slate-900/30 backdrop-blur-xl my-8 p-6 border-2 border-white/40 rounded-3xl"
>
  <Accordion flush>
    <span class="text-2xl font-semibold">Study project 2<br /></span>

    <AccordionItem class="text-white flex flex-col justify-between">
      {#snippet header()}<span
          style="font-weight: 600; font-size: 2rem; color: #7dd3fc;"
          >Simultaneous Localization and Mapping (SLAM) with Fischertechnik -
          Analysis and optimization of previous work</span
        >{/snippet}
      {#snippet arrowup()}<ChevronDoubleUpOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      {#snippet arrowdown()}<ChevronDoubleDownOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      <div
        class="grid grid-cols-1 md:grid-cols-2 gap-6 auto-rows-max my-2 text-xl"
      >
        <div class="md:col-span-1 md:row-span-2">
          <span class="font-semibold text-[#7dd3fc]">Situation</span>
          <div>
            A legacy study project demonstrated the feasibility of SLAM
            (Simultaneous Localization and Mapping) using a Fischertechnik
            robotics kit, but the implementation was prone to failure. The
            system suffered from unstructured code and unstable sensor mounting,
            resulting in inconsistent environmental data and poor mapping
            performance.
          </div>
          <br />
          <span class="font-semibold text-[#7dd3fc]">Task</span>
          <div>
            The group that worked on consisted of 5 people and the objective was
            to overhaul the system to professional engineering standards. This
            involved a complete architectural refactor to improve
            maintainability, as well as hardware modifications to ensure
            reliable data acquisition for real-time autonomous navigation.
          </div>
          <br />
          <span class="font-semibold text-[#7dd3fc]">Action</span><br />
          I implemented modern software and hardware engineering practices to stabilize
          the platform:
          <ul class="list-disc list-inside ml-4">
            <li>
              Architectural Refactoring: Replaced procedural logic with a robust
              Object-Oriented Programming (OOP) structure. I designed modular
              classes to decouple sensor input, mapping logic, and motor
              control, significantly reducing technical debt.
            </li>
            <li>
              Hardware Integration: Designed and 3D-printed a custom mounting
              bracket for the LiDAR sensor. This eliminated mechanical vibration
              and ensured stable, precise data acquisition during robot
              movement.
            </li>
            <li>
              Performance Optimization: Streamlined the data processing pipeline
              to allow for real-time mapping. We drafted technical strategies
              for implementing RANSAC (Random Sample Consensus) to improve noise
              reduction and data association.
            </li>
            <li>
              Technologies: Python, OOP, LiDAR, SLAM Algorithms, 3D Printing
              (CAD), Robotics.
            </li>
          </ul>
        </div>
        <div class="w-full md:col-span-1 md:row-span-1">
          {#if images_stud_2.length > 0}
            <Carousel
              images={images_stud_2}
              onchange={(detail) => (image5 = detail)}
            >
              <Controls>
                {#snippet children(changeSlide)}
                  <Button
                    pill
                    class="absolute start-4 top-1/2 -translate-y-1/2 p-2 font-bold bg-[#7dd3fc]"
                    onclick={() => changeSlide(false)}
                  >
                    <CaretLeftOutline />
                  </Button>
                  <Button
                    pill
                    class="absolute end-4 top-1/2 -translate-y-1/2 p-2 font-bold bg-[#7dd3fc]"
                    onclick={() => changeSlide(true)}
                  >
                    <CaretRightOutline />
                  </Button>
                {/snippet}
              </Controls>
              <CarouselIndicators>
                {#snippet children({ selected, index })}
                  <Indicator
                    color={selected ? "blue" : "gray"}
                    class="h-5 w-5 border border-white text-white {selected
                      ? 'opacity-100'
                      : 'opacity-90'}"
                  >
                    {index}
                  </Indicator>
                {/snippet}
              </CarouselIndicators>
            </Carousel>
          {/if}
          <div
            class="mt-2 rounded-sm bg-transparent p-2 text-center border-2 align-middle border-gray-300"
          >
            {image5?.alt}
          </div>
        </div>
        <div class="md:col-span-1 md:row-span-1">
          <span class="font-semibold text-[#7dd3fc]">Result</span>
          <div>
            The project resulted in a maintainable framework for robotic
            mapping. The new OOP architecture improved system stability and
            simplified the integration of future autonomous features. By
            providing clean, consistent environmental data, the system now
            serves as a reliable research platform for advanced autonomous
            navigation.
          </div>
        </div>
      </div>
    </AccordionItem>
  </Accordion>
</div>

<!-- Studienprojekt 1 -->
<div
  class="bg-slate-900/30 backdrop-blur-xl my-8 p-6 border-2 border-white/40 rounded-3xl"
>
  <Accordion flush>
    <span class="text-2xl font-semibold">Study project 1<br /></span>

    <AccordionItem class="text-white flex flex-col justify-between">
      {#snippet header()}<span
          style="font-weight: 600; font-size: 2rem; color: #7dd3fc;"
          >Following Uncharted Paths - Developing a Robot Prototype for Line
          Tracking Using a PID Controller</span
        >{/snippet}
      {#snippet arrowup()}<ChevronDoubleUpOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      {#snippet arrowdown()}<ChevronDoubleDownOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      <div
        class="grid grid-cols-1 md:grid-cols-2 gap-6 auto-rows-max my-2 text-xl"
      >
        <div class="md:col-span-1 md:row-span-2">
          <span class="font-semibold text-[#7dd3fc]">Situation</span>
          <div>
            The goal of an university project was to develop a robotic system
            capable of navigating unknown paths autonomously with a PID
            controller. The paths were defined by high-contrast visual markers
            (black lines on a white background). The challenge lay in control
            logic to ensure the robot could follow curves and lines smoothly
            without losing the track.
          </div>
          <br />
          <span class="font-semibold text-[#7dd3fc]">Task</span>
          <div>
            I was in a group of 4 people and we were tasked with building a car
            out of LEGO components that integrate control and sensor
            functionality. The objective was to create a modular system that
            could drive autonomously with minimal human intervention.
          </div>
          <br />
          <span class="font-semibold text-[#7dd3fc]">Action</span>
          <ul class="list-disc list-inside ml-4">
            <li>
              Prototyping: Constructed the physical robot chassis using LEGO
              components, allowing for rapid iteration of sensor placement and
              weight distribution.
            </li>
            <li>
              Hardware Evaluation: Researched and tested different hardware
              interfaces to motor/sensor actuation aswell as capabilities of the
              LEGO ecosystem.
            </li>
            <li>
              Control Implementation: Developed the logic to process real-time
              sensor data and translate it into precise motor commands.
            </li>
            <li>
              Testing: Ran comparative evaluations of different hardware setups
              to determine which provided the highest reliability and lowest
              latency during path tracking.
            </li>
            <li>
              Technologies: LEGO-Spike, Python, Raspberry Pi & expansionboards
            </li>
          </ul>
        </div>
        <div class="w-full md:col-span-1 md:row-span-1">
          {#if images_stud_1.length > 0}
            <Carousel
              images={images_stud_1}
              onchange={(detail) => (image4 = detail)}
            >
              <Controls>
                {#snippet children(changeSlide)}
                  <Button
                    pill
                    class="absolute start-4 top-1/2 -translate-y-1/2 p-2 font-bold bg-[#7dd3fc]"
                    onclick={() => changeSlide(false)}
                  >
                    <CaretLeftOutline />
                  </Button>
                  <Button
                    pill
                    class="absolute end-4 top-1/2 -translate-y-1/2 p-2 font-bold bg-[#7dd3fc]"
                    onclick={() => changeSlide(true)}
                  >
                    <CaretRightOutline />
                  </Button>
                {/snippet}
              </Controls>
              <CarouselIndicators>
                {#snippet children({ selected, index })}
                  <Indicator
                    color={selected ? "blue" : "gray"}
                    class="h-5 w-5 border border-white text-white {selected
                      ? 'opacity-100'
                      : 'opacity-90'}"
                  >
                    {index}
                  </Indicator>
                {/snippet}
              </CarouselIndicators>
            </Carousel>
          {/if}
          <div
            class="mt-2 rounded-sm bg-transparent p-2 text-center border-2 align-middle border-gray-300"
          >
            {image4?.alt}
          </div>
        </div>
        <div class="md:col-span-1 md:row-span-1">
          <span class="font-semibold text-[#7dd3fc]">Result</span>
          <div>
            We successfully developed a working prototype that follows unknown
            paths. This project established a robust hardware and software
            foundation, proving the feasibility of the chosen components. The
            final design serves as a scalable platform for future developments
            in advanced control theory, such as PID
            (Proportional-Integral-Derivative) tuning.
          </div>
        </div>
      </div>
    </AccordionItem>
  </Accordion>
</div>

<!-- PTB 3 -->
<div
  class="bg-slate-900/30 backdrop-blur-xl my-8 p-6 border-2 border-white/40 rounded-3xl"
>
  <Accordion flush>
    <span class="text-2xl font-semibold">Practice transfer report 3<br /></span>

    <AccordionItem class="text-white flex flex-col justify-between">
      {#snippet header()}<span
          style="font-weight: 600; font-size: 2rem; color: #7dd3fc;"
          >Establishing a HITL Testing System with Raspberry Pi’s</span
        >{/snippet}
      {#snippet arrowup()}<ChevronDoubleUpOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      {#snippet arrowdown()}<ChevronDoubleDownOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      <div
        class="grid grid-cols-1 md:grid-cols-2 gap-6 auto-rows-max my-2 text-xl"
      >
        <div class="md:col-span-1 md:row-span-2">
          <span class="font-semibold text-[#7dd3fc]">Situation</span>
          <div>
            To validate critical firefighting communication devices, the team
            required large-scale Hardware-in-the-Loop (HITL) testing to simulate
            real world scenarios. The primary challenge was maintaining a
            stable, reproducible environment while controlling and updating 64
            individual Devices Under Test (DUT) simultaneously.
          </div>
          <br />
          <span class="font-semibold text-[#7dd3fc]">Task</span>
          <div>
            My objective was to design, build, and automate a hardware testing
            rack featuring 64 Raspberry Pi 4 nodes. I needed to establish a
            reliable communication channel between a central Linux controller
            and the cluster, automate test execution, and implement a rapid
            recovery protocol for possbile system failures.
          </div>
          <br />
          <span class="font-semibold text-[#7dd3fc]">Action</span>
          <ul class="list-disc list-inside ml-4">
            <li>
              Network Infrastructure: Configured a dedicated local network
              utilizing SSH for remote orchestration and DHCP for efficient IP
              management across the 64-node cluster.
            </li>
            <li>
              Automation & Orchestration: Leveraged Ansible to automate software
              deployments and test synchronization, ensuring 100% configuration
              consistency across all units.
            </li>
            <li>
              System Imaging & Recovery: Developed a custom Linux Image for the
              Raspberry Pis. This enabled a bare metal recovery, allowing any
              failing node to be reflashed to a stable state within minutes.
            </li>
            <li>
              Technologies: Ansible, Linux (Debian/Raspbian), SSH, DHCP, Shell
              Scripting, Raspberry Pi 4.
            </li>
          </ul>
        </div>
        <div class="w-full md:col-span-1 md:row-span-1">
          {#if images_ptb_3.length > 0}
            <Carousel
              images={images_ptb_3}
              onchange={(detail) => (image3 = detail)}
            >
              <Controls>
                {#snippet children(changeSlide)}
                  <Button
                    pill
                    class="absolute start-4 top-1/2 -translate-y-1/2 p-2 font-bold bg-[#7dd3fc]"
                    onclick={() => changeSlide(false)}
                  >
                    <CaretLeftOutline />
                  </Button>
                  <Button
                    pill
                    class="absolute end-4 top-1/2 -translate-y-1/2 p-2 font-bold bg-[#7dd3fc]"
                    onclick={() => changeSlide(true)}
                  >
                    <CaretRightOutline />
                  </Button>
                {/snippet}
              </Controls>
              <CarouselIndicators>
                {#snippet children({ selected, index })}
                  <Indicator
                    color={selected ? "blue" : "gray"}
                    class="h-5 w-5 border border-white text-white {selected
                      ? 'opacity-100'
                      : 'opacity-90'}"
                  >
                    {index}
                  </Indicator>
                {/snippet}
              </CarouselIndicators>
            </Carousel>
          {/if}
          <div
            class="mt-2 rounded-sm bg-transparent p-2 text-center border-2 align-middle border-gray-300"
          >
            {image3?.alt}
          </div>
        </div>
        <div class="md:col-span-1 md:row-span-1">
          <span class="font-semibold text-[#7dd3fc]">Result</span>
          <div>
            The automated rack significantly increased testing capacity and
            eliminated manual configuration errors. By introducing
            Ansible-driven orchestration and custom imaging, I reduced system
            recovery time from hours to minutes. This infrastructure provided a
            high-availability platform for validating the reliability of safety
            critical hardware at scale.
          </div>
        </div>
      </div>
    </AccordionItem>
  </Accordion>
</div>

<!-- PTB 2 -->
<div
  class="bg-slate-900/30 backdrop-blur-xl my-8 p-6 border-2 border-white/40 rounded-3xl text-xl"
>
  <Accordion flush>
    <span class="text-2xl font-semibold">Practice transfer report 2<br /></span>
    <AccordionItem class="text-white flex flex-col justify-between">
      {#snippet header()}<span
          style="font-weight: 600; font-size: 2rem; color: #7dd3fc;"
          >Design and implementation of a battery simulator</span
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
            <Carousel
              images={images_ptb_2}
              onchange={(detail) => (image2 = detail)}
            >
              <Controls>
                {#snippet children(changeSlide)}
                  <Button
                    pill
                    class="absolute start-4 top-1/2 -translate-y-1/2 p-2 font-bold bg-[#7dd3fc]"
                    onclick={() => changeSlide(false)}
                  >
                    <CaretLeftOutline />
                  </Button>
                  <Button
                    pill
                    class="absolute end-4 top-1/2 -translate-y-1/2 p-2 font-bold bg-[#7dd3fc]"
                    onclick={() => changeSlide(true)}
                  >
                    <CaretRightOutline />
                  </Button>
                {/snippet}
              </Controls>
              <CarouselIndicators>
                {#snippet children({ selected, index })}
                  <Indicator
                    color={selected ? "blue" : "gray"}
                    class="h-5 w-5 border border-white text-white {selected
                      ? 'opacity-100'
                      : 'opacity-90'}"
                  >
                    {index}
                  </Indicator>
                {/snippet}
              </CarouselIndicators>
            </Carousel>
          {/if}
          <div
            class="mt-2 rounded-sm bg-transparent p-2 text-center border-2 align-middle border-gray-300"
          >
            {image2?.alt}
          </div>
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

<!-- PTB 1 -->
<div
  class="bg-slate-900/30 backdrop-blur-xl my-8 p-6 border-2 border-white/40 rounded-3xl"
>
  <Accordion flush>
    <span class="text-2xl font-semibold">Practice transfer report 1<br /></span>
    <AccordionItem class="text-white flex flex-col justify-between">
      {#snippet header()}<span
          style="font-weight: 600; font-size: 2rem; color: #7dd3fc;"
          >Creation of software for data transmission to cloud server</span
        >{/snippet}
      {#snippet arrowup()}<ChevronDoubleUpOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      {#snippet arrowdown()}<ChevronDoubleDownOutline
          class="h-6 w-6 text-[#f0f0f0]"
        />{/snippet}
      <div
        class="grid grid-cols-1 md:grid-cols-2 gap-6 auto-rows-max my-2 text-xl"
      >
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
              dashboards to filter by message type (e.g. error codes) and
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
              <Controls>
                {#snippet children(changeSlide)}
                  <Button
                    pill
                    class="absolute start-4 top-1/2 -translate-y-1/2 p-2 font-bold bg-[#7dd3fc]"
                    onclick={() => changeSlide(false)}
                  >
                    <CaretLeftOutline />
                  </Button>
                  <Button
                    pill
                    class="absolute end-4 top-1/2 -translate-y-1/2 p-2 font-bold bg-[#7dd3fc]"
                    onclick={() => changeSlide(true)}
                  >
                    <CaretRightOutline />
                  </Button>
                {/snippet}
              </Controls>
              <CarouselIndicators>
                {#snippet children({ selected, index })}
                  <Indicator
                    color={selected ? "blue" : "gray"}
                    class="h-5 w-5 border border-white text-white {selected
                      ? 'opacity-100'
                      : 'opacity-90'}"
                  >
                    {index}
                  </Indicator>
                {/snippet}
              </CarouselIndicators>
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
