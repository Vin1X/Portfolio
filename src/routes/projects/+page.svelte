<script lang="ts">
  import ProjectItem from "$lib/components/ProjectItem.svelte";

  // --- IMAGES ---
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

  const projects = [
    {
      id: "ba",
      category: "Bachelor Thesis",
      title: "Development of a Functional Test System for Industrial Routers",
      situation:
        'With the in-house relocation of the "<a href="https://de.msasafety.com/p/000010001900011600?&locale=en&default=1" target="_blank" rel="noopener noreferrer" onclick="event.stopPropagation()" class="text-cyan-400 underline underline-offset-4 hover:text-cyan-300">MSA Hub</a>" production, a specialized test bench was required to verify hardware integrity and automate firmware deployment without risking manufacturing errors.',
      task: "Conceive, implement, and evaluate an automated functional test framework with a single-action GUI designed for factory personnel.",
      actions: [
        {
          label: "Debug & Flashing",
          text: "Integrated JTAG and SWD for automated SoM and LRR radio programming.",
        },
        {
          label: "Network Verification",
          text: "Executed ICMP & DHCP management protocols.",
        },
        {
          label: "Framework",
          text: "Modular Python application using PyQt/PySide and YAML config management.",
        },
      ],
      result:
        "Optimized the EOL manufacturing phase, drastically reducing OPEX while eliminating manual operator error.",
      images: [
        { src: ba_msa_hub, alt: "The MSA Hub." },
        {
          src: ba_functional_test,
          alt: "GUI draft for functional test software.",
        },
        { src: ba_architektur, alt: "System architecture diagram." },
        { src: ba_architecture, alt: "Software architecture diagram." },
        { src: ba_sequence_diagram, alt: "Application workflow sequence." },
        { src: ba_app_draft_error, alt: "GUI validation error state draft." },
        { src: ba_led, alt: "MSA Hub active status indicators." },
      ],
    },
    {
      id: "stud_2",
      category: "Study Project 2",
      title: "SLAM Robotics Optimization & LiDAR Integration",
      situation:
        "A legacy SLAM platform suffered from unstructured procedural code and severe mechanical LiDAR sensor vibrations, rendering mapping data unreliable.",
      task: "Refactor the platform architecture to professional OOP standards and stabilize the hardware array for real-time mapping.",
      actions: [
        {
          label: "Architecture",
          text: "Designed clean OOP Python classes for sensor feeds and motor control decoupling.",
        },
        {
          label: "CAD & 3D Printing",
          text: "Modeled and printed a custom anti-vibration LiDAR bracket.",
        },
        {
          label: "Noise Reduction",
          text: "Drafted RANSAC algorithms for outlier rejection.",
        },
      ],
      result:
        "Established a stable research platform that yields clean, repeatable point-cloud environmental data.",
      images: [
        { src: stud_2_data_assos_2, alt: "Top view of robot." },
        {
          src: stud_2_data_assos_2_ransac,
          alt: "Data association with RANSAC process.",
        },
        { src: stud_2_aufbau, alt: "Close-up of controller and LiDAR." },
        { src: stud_2_lidar, alt: "LiDAR sensor setup." },
        { src: stud_2_teststrecke_empty, alt: "Empty test track." },
        { src: stud_2_teststrecke, alt: "Test track with obstacles." },
        {
          src: stud_2_ransac_error,
          alt: "RANSAC algorithm behavior under high noise.",
        },
        { src: stud_2_3dprint, alt: "Custom 3D printed mount." },
        { src: stud_2_clustering_lidar, alt: "LiDAR data points clustering." },
        { src: stud_2_slam_objects, alt: "Test objects used for algorithm." },
      ],
    },
    {
      id: "stud_1",
      category: "Study Project 1",
      title: "Autonomous PID Line-Tracking Robot Prototype",
      situation:
        "Designing an autonomous vehicle prototype to navigate unknown high-contrast paths smoothly using feedback-control loops.",
      task: "Build a LEGO Spike and Raspberry Pi vehicle integration to execute closed-loop motor adjustments in real time.",
      actions: [
        {
          label: "Prototyping",
          text: "Iterated physical weight distribution and sensor distance.",
        },
        {
          label: "Control Implementation",
          text: "Written low-latency Python scripts for motor speed regulation.",
        },
      ],
      result:
        "Demonstrated smooth path tracking along unknown curves, laying the groundwork for PID parameter tuning experiments.",
      images: [
        { src: stud_1_front, alt: "Front view of robot." },
        { src: stud_1_track, alt: "Test track for robot verification." },
        { src: stud_1_back, alt: "Rear view displaying Pi and sensors." },
        {
          src: stud_1_build,
          alt: "Schematic build for calculating PID radius.",
        },
        { src: stud_1_drawing, alt: "Control logic loop diagram." },
        { src: stud_1_corner, alt: "Robot approaching sharp corner." },
      ],
    },
    {
      id: "ptb_3",
      category: "Practice Transfer Report 3",
      title: "64-Node Raspberry Pi Cluster for HITL Testing",
      situation:
        "Simulating stress tests on firefighting communication equipment required managing 64 independent Hardware-in-the-Loop test nodes.",
      task: "Design a hardware rack cluster, automate node deployment, and implement rapid system recovery protocols.",
      actions: [
        {
          label: "Networking",
          text: "Configured SSH orchestration and DHCP servers across 64 nodes.",
        },
        {
          label: "Ansible",
          text: "Automated software deployment and test state synchronization.",
        },
        {
          label: "Bare Metal Recovery",
          text: "Built a custom Linux OS image for rapid flashing upon failure.",
        },
      ],
      result:
        "Reduced recovery times from hours to minutes, creating a high-availability test bed for mission-critical hardware.",
      images: [
        { src: ptb_3_rack_strom, alt: "Back view of testing rack." },
        {
          src: ptb_3_rack,
          alt: "Front view of testing rack with 64 Raspberry Pis.",
        },
        {
          src: ptb_3_raspi_mount,
          alt: "Rack slot with 4 Raspberry Pis on custom 3D mount.",
        },
        {
          src: ptb_3_raspi_close,
          alt: "Close-up of Raspberry Pi with expansion board.",
        },
        { src: ptb_3_dhcp, alt: "Diagram explaining DHCP operation." },
        { src: ptb_3_aufbau, alt: "MSA environment setup." },
      ],
    },
    {
      id: "ptb_2",
      category: "Practice Transfer Report 2",
      title: "Smart Battery Simulator for HITL Framework",
      situation:
        "Testing physical batteries for edge-case faults (voltage drops, thermal runaways) is dangerous, expensive, and unrepeatable.",
      task: "Construct an I2C-based battery simulator that injects fault parameters into the device under test (DUT).",
      actions: [
        {
          label: "Hybrid Hardware",
          text: "Pi Pico (RP2040) for real-time register emulation + Raspberry Pi 4 high-level control.",
        },
        {
          label: "I2C Protocol",
          text: "Emulated smart battery gauge communication.",
        },
      ],
      result:
        "Replaced manual battery testing with an automated framework plugin reused across multiple product lines.",
      images: [
        {
          src: ptb_2_construction,
          alt: "Test setup with battery simulator & DUT.",
        },
        { src: ptb_2_block, alt: "Block diagram of system architecture." },
        {
          src: ptb_2_construction2,
          alt: "Another view of test setup construction.",
        },
        {
          src: ptb_2_sequence,
          alt: "Sequence diagram of fuel gauge simulator.",
        },
        { src: ptb_2_block2, alt: "Block diagram of I2C HITL support." },
      ],
    },
    {
      id: "ptb_1",
      category: "Practice Transfer Report 1",
      title: "High-Fidelity Telemetry & Cloud Logging Pipeline",
      situation:
        "Granular raw logs on the MSA ALTAIR io4 were only readable via physical serial ports, bottlenecking remote debugging efforts.",
      task: "Develop a Python service to capture UART/JTAG streams and forward telemetry directly into AWS and Datadog.",
      actions: [
        {
          label: "Data Pipeline",
          text: "Written Python listeners reading UART output.",
        },
        {
          label: "AWS Integration",
          text: "Pushed logs via AWS Boto3 SDK to CloudWatch.",
        },
        {
          label: "Datadog Dashboards",
          text: "Designed visualization queries for error tracking.",
        },
      ],
      result:
        "Provided engineers with instant global visibility into device logs, eliminating manual serial extraction.",
      images: [
        { src: ptb_1_io4, alt: "The MSA Altair iO4." },
        { src: ptb_1_draft, alt: "Draft of system architecture and workflow." },
        { src: ptb_1_rawlogs, alt: "The raw logs read from the Altair io4." },
        { src: ptb_1_cloud, alt: "The logs after streaming to CloudWatch." },
        { src: ptb_1_datadog, alt: "The logs after forwarding to DataDog." },
        { src: ptb_1_datadog2, alt: "Visualization of log entry in DataDog." },
        { src: ptb_1_uart, alt: "UART protocol interaction." },
      ],
    },
  ];
</script>

<div class="max-w-5xl mx-auto space-y-8 py-4 px-4">
  <header class="text-center py-6 relative">
    <span
      class="inline-block px-3 py-1 mb-3 rounded-full bg-cyan-500/10 border border-cyan-500/20 text-cyan-300 text-xs font-mono uppercase tracking-wider"
    >
      Portfolio Highlights
    </span>
    <h1 class="text-2xl sm:text-3xl font-bold text-white mb-3 tracking-tight">
      Featured Engineering Projects
    </h1>
    <p
      class="text-slate-300 max-w-2xl mx-auto text-base sm:text-lg leading-relaxed font-light"
    >
      A collection of key projects I have had during my dual study program and
      university courses.
    </p>
  </header>

  <div class="space-y-6">
    {#each projects as project}
      <ProjectItem {project} />
    {/each}
  </div>
</div>
