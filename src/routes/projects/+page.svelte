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

  const images_ptb_1 = [
    { id: "0", src: ptb_1_io4, alt: "The MSA Altair iO4.", loading: "lazy" },
    {
      id: "1",
      src: ptb_1_draft,
      alt: "Draft of system architecture and workflow.",
      loading: "lazy",
    },
    {
      id: "2",
      src: ptb_1_rawlogs,
      alt: "The raw logs read from the Altair io4.",
      loading: "lazy",
    },
    {
      id: "3",
      src: ptb_1_cloud,
      alt: "The logs after streaming to CloudWatch.",
      loading: "lazy",
    },
    {
      id: "4",
      src: ptb_1_datadog,
      alt: "The logs after forwarding to DataDog.",
      loading: "lazy",
    },
    {
      id: "5",
      src: ptb_1_datadog2,
      alt: "Visualization of log entry in DataDog.",
      loading: "lazy",
    },
    {
      id: "6",
      src: ptb_1_uart,
      alt: "UART protocol interaction.",
      loading: "lazy",
    },
  ];

  const images_ptb_2 = [
    {
      id: "0",
      src: ptb_2_construction,
      alt: "Test setup with battery simulator & DUT.",
      loading: "lazy",
    },
    {
      id: "1",
      src: ptb_2_block,
      alt: "Block diagram of system architecture.",
      loading: "lazy",
    },
    {
      id: "2",
      src: ptb_2_construction2,
      alt: "Another view of test setup construction.",
      loading: "lazy",
    },
    {
      id: "3",
      src: ptb_2_sequence,
      alt: "Sequence diagram of fuel gauge simulator.",
      loading: "lazy",
    },
    {
      id: "4",
      src: ptb_2_block2,
      alt: "Block diagram of I2C HITL support.",
      loading: "lazy",
    },
  ];

  const images_ptb_3 = [
    {
      id: "0",
      src: ptb_3_rack_strom,
      alt: "Back view of testing rack.",
      loading: "lazy",
    },
    {
      id: "1",
      src: ptb_3_rack,
      alt: "Front view of testing rack with 64 Raspberry Pis.",
      loading: "lazy",
    },
    {
      id: "2",
      src: ptb_3_raspi_mount,
      alt: "Rack slot with 4 Raspberry Pis on custom 3D mount.",
      loading: "lazy",
    },
    {
      id: "3",
      src: ptb_3_raspi_close,
      alt: "Close-up of Raspberry Pi with expansion board.",
      loading: "lazy",
    },
    {
      id: "4",
      src: ptb_3_dhcp,
      alt: "Diagram explaining DHCP operation.",
      loading: "lazy",
    },
    {
      id: "5",
      src: ptb_3_aufbau,
      alt: "MSA environment setup.",
      loading: "lazy",
    },
  ];

  const images_stud_1 = [
    {
      id: "0",
      src: stud_1_front,
      alt: "Front view of robot.",
      loading: "lazy",
    },
    {
      id: "1",
      src: stud_1_track,
      alt: "Test track for robot verification.",
      loading: "lazy",
    },
    {
      id: "2",
      src: stud_1_back,
      alt: "Rear view displaying Pi and sensors.",
      loading: "lazy",
    },
    {
      id: "3",
      src: stud_1_build,
      alt: "Schematic build for calculating PID radius.",
      loading: "lazy",
    },
    {
      id: "4",
      src: stud_1_drawing,
      alt: "Control logic loop diagram.",
      loading: "lazy",
    },
    {
      id: "5",
      src: stud_1_corner,
      alt: "Robot approaching sharp corner.",
      loading: "lazy",
    },
  ];

  const images_stud_2 = [
    {
      id: "0",
      src: stud_2_data_assos_2,
      alt: "Top view of robot.",
      loading: "lazy",
    },
    {
      id: "1",
      src: stud_2_data_assos_2_ransac,
      alt: "Data association with RANSAC process.",
      loading: "lazy",
    },
    {
      id: "2",
      src: stud_2_aufbau,
      alt: "Close-up of controller and LiDAR.",
      loading: "lazy",
    },
    { id: "3", src: stud_2_lidar, alt: "LiDAR sensor setup.", loading: "lazy" },
    {
      id: "4",
      src: stud_2_teststrecke_empty,
      alt: "Empty test track.",
      loading: "lazy",
    },
    {
      id: "5",
      src: stud_2_teststrecke,
      alt: "Test track with obstacles.",
      loading: "lazy",
    },
    {
      id: "6",
      src: stud_2_ransac_error,
      alt: "RANSAC algorithm behavior under high noise.",
      loading: "lazy",
    },
    {
      id: "7",
      src: stud_2_3dprint,
      alt: "Custom 3D printed mount.",
      loading: "lazy",
    },
    {
      id: "8",
      src: stud_2_clustering_lidar,
      alt: "LiDAR data points clustering.",
      loading: "lazy",
    },
    {
      id: "9",
      src: stud_2_slam_objects,
      alt: "Test objects used for algorithm.",
      loading: "lazy",
    },
  ];

  const images_ba = [
    { id: "0", src: ba_msa_hub, alt: "The MSA Hub hardware.", loading: "lazy" },
    {
      id: "1",
      src: ba_functional_test,
      alt: "GUI draft for functional test.",
      loading: "lazy",
    },
    {
      id: "2",
      src: ba_architektur,
      alt: "System architecture diagram.",
      loading: "lazy",
    },
    {
      id: "3",
      src: ba_architecture,
      alt: "Software architecture diagram.",
      loading: "lazy",
    },
    {
      id: "4",
      src: ba_sequence_diagram,
      alt: "Application workflow sequence.",
      loading: "lazy",
    },
    {
      id: "5",
      src: ba_app_draft_error,
      alt: "GUI validation error state draft.",
      loading: "lazy",
    },
    {
      id: "6",
      src: ba_led,
      alt: "MSA Hub active status indicators.",
      loading: "lazy",
    },
  ];

  let image = $state(images_ptb_1[0]);
  let image2 = $state(images_ptb_2[0]);
  let image3 = $state(images_ptb_3[0]);
  let image4 = $state(images_stud_1[0]);
  let image5 = $state(images_stud_2[0]);
  let image6 = $state(images_ba[0]);

  // Track accordion open states so carousels inside closed accordions are NOT rendered into DOM upfront
  let openAccordions = $state<Record<string, boolean>>({});

  function toggleAccordion(key: string) {
    openAccordions[key] = !openAccordions[key];
  }
</script>

<div class="max-w-5xl mx-auto space-y-8 py-4">
  <!-- Intro Card -->
  <div class="text-center py-6 relative">
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
  </div>

  <!-- Projects Container -->
  <div class="space-y-6">
    <!-- Bachelorthesis -->
    <div
      class="bg-slate-900/60 backdrop-blur-xl border border-white/10 border-t-white/20 rounded-3xl shadow-xl overflow-hidden transition-all duration-300"
    >
      <Accordion flush class="p-6">
        <AccordionItem
          class="text-white border-0"
          onclick={() => toggleAccordion("ba")}
        >
          {#snippet header()}
            <div class="flex flex-col text-left">
              <span
                class="text-xs font-mono uppercase tracking-wider text-cyan-400 font-semibold mb-1"
                >Bachelor Thesis</span
              >
              <span
                class="text-xl sm:text-2xl font-bold text-white hover:text-cyan-300 transition-colors"
              >
                Development of a Functional Test System for Industrial Routers
              </span>
            </div>
          {/snippet}
          {#snippet arrowup()}<ChevronDoubleUpOutline
              class="h-5 w-5 text-cyan-400"
            />{/snippet}
          {#snippet arrowdown()}<ChevronDoubleDownOutline
              class="h-5 w-5 text-slate-400"
            />{/snippet}

          <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 my-4">
            <div
              class="lg:col-span-7 space-y-4 text-slate-300 text-base leading-relaxed"
            >
              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Situation
                </h4>
                <p>
                  With the in-house relocation of the "<a
                    href="https://de.msasafety.com/p/000010001900011600?&locale=en&default=1"
                    target="_blank"
                    class="text-cyan-400 underline underline-offset-4 hover:text-cyan-300"
                    >MSA Hub</a
                  >" production[cite: 1], a specialized test bench was required
                  to verify hardware integrity and automate firmware deployment
                  without risking manufacturing errors[cite: 1].
                </p>
              </div>
              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Task
                </h4>
                <p>
                  Conceive, implement, and evaluate an automated functional test
                  framework with a single-action GUI designed for factory
                  personnel[cite: 1].
                </p>
              </div>
              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Action
                </h4>
                <ul class="list-disc list-inside space-y-1 ml-1 text-slate-300">
                  <li>
                    <strong class="text-slate-100">Debug & Flashing:</strong> Integrated
                    JTAG and SWD for automated SoM and LRR radio programming[cite:
                    1].
                  </li>
                  <li>
                    <strong class="text-slate-100">Network Verification:</strong
                    > Executed ICMP & DHCP management protocols[cite: 1].
                  </li>
                  <li>
                    <strong class="text-slate-100">Framework:</strong> Modular Python
                    application using PyQt/PySide and YAML config management[cite:
                    1].
                  </li>
                </ul>
              </div>
              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Result
                </h4>
                <p class="text-slate-200">
                  Optimized the EOL manufacturing phase, drastically reducing
                  OPEX while eliminating manual operator error[cite: 1].
                </p>
              </div>
            </div>

            <!-- Lazy Rendered Carousel -->
            <div class="lg:col-span-5 flex flex-col justify-start">
              <div
                class="relative w-full rounded-2xl bg-slate-950/80 border border-white/10 p-2 shadow-inner overflow-hidden min-h-[300px]"
              >
                {#if openAccordions["ba"] && images_ba.length > 0}
                  <Carousel
                    images={images_ba}
                    imgClass="object-contain max-h-[360px] w-auto mx-auto rounded-lg"
                    onchange={(detail) => (image6 = detail)}
                  >
                    <Controls>
                      {#snippet children(changeSlide)}
                        <Button
                          pill
                          class="absolute start-3 top-1/2 -translate-y-1/2 p-2 bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30 backdrop-blur-md"
                          onclick={() => changeSlide(false)}
                        >
                          <CaretLeftOutline class="w-4 h-4" />
                        </Button>
                        <Button
                          pill
                          class="absolute end-3 top-1/2 -translate-y-1/2 p-2 bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30 backdrop-blur-md"
                          onclick={() => changeSlide(true)}
                        >
                          <CaretRightOutline class="w-4 h-4" />
                        </Button>
                      {/snippet}
                    </Controls>
                    <CarouselIndicators class="bottom-2">
                      {#snippet children({ selected, index })}
                        <Indicator
                          color={selected ? "blue" : "gray"}
                          class="h-2 w-2 rounded-full transition-all duration-300 {selected
                            ? 'w-5 bg-cyan-400'
                            : 'bg-slate-600'}"
                        />
                      {/snippet}
                    </CarouselIndicators>
                  </Carousel>
                {/if}
              </div>
              <p
                class="mt-3 text-xs text-center text-slate-400 font-mono italic bg-slate-950/40 p-2 rounded-xl border border-white/5"
              >
                {image6?.alt || images_ba[0].alt}
              </p>
            </div>
          </div>
        </AccordionItem>
      </Accordion>
    </div>

    <!-- Study Project 2 -->
    <div
      class="bg-slate-900/60 backdrop-blur-xl border border-white/10 border-t-white/20 rounded-3xl shadow-xl overflow-hidden transition-all duration-300"
    >
      <Accordion flush class="p-6">
        <AccordionItem class="text-white border-0">
          {#snippet header()}
            <div class="flex flex-col text-left">
              <span
                class="text-xs font-mono uppercase tracking-wider text-cyan-400 font-semibold mb-1"
                >Study Project 2</span
              >
              <span
                class="text-xl sm:text-2xl font-bold text-white hover:text-cyan-300 transition-colors"
              >
                SLAM Robotics Optimization & LiDAR Integration
              </span>
            </div>
          {/snippet}
          {#snippet arrowup()}<ChevronDoubleUpOutline
              class="h-5 w-5 text-cyan-400"
            />{/snippet}
          {#snippet arrowdown()}<ChevronDoubleDownOutline
              class="h-5 w-5 text-slate-400"
            />{/snippet}

          <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 my-4">
            <div
              class="lg:col-span-7 space-y-4 text-slate-300 text-base leading-relaxed"
            >
              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Situation
                </h4>
                <p>
                  A legacy SLAM platform suffered from unstructured procedural
                  code and severe mechanical LiDAR sensor vibrations, rendering
                  mapping data unreliable[cite: 1].
                </p>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Task
                </h4>
                <p>
                  Refactor the platform architecture to professional OOP
                  standards and stabilize the hardware array for real-time
                  mapping[cite: 1].
                </p>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Action
                </h4>
                <ul class="list-disc list-inside space-y-1 ml-1 text-slate-300">
                  <li>
                    <strong class="text-slate-100">Architecture:</strong> Designed
                    clean OOP Python classes for sensor feeds and motor control decoupling[cite:
                    1].
                  </li>
                  <li>
                    <strong class="text-slate-100">CAD & 3D Printing:</strong> Modeled
                    and printed a custom anti-vibration LiDAR bracket[cite: 1].
                  </li>
                  <li>
                    <strong class="text-slate-100">Noise Reduction:</strong> Drafted
                    RANSAC algorithms for outlier rejection[cite: 1].
                  </li>
                </ul>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Result
                </h4>
                <p class="text-slate-200">
                  Established a stable research platform that yields clean,
                  repeatable point-cloud environmental data[cite: 1].
                </p>
              </div>
            </div>

            <!-- Slideshow -->
            <div class="lg:col-span-5 flex flex-col justify-start">
              <div
                class="relative w-full rounded-2xl bg-slate-950/80 border border-white/10 p-2 shadow-inner overflow-hidden"
              >
                {#if images_stud_2.length > 0}
                  <Carousel
                    images={images_stud_2}
                    imgClass="object-contain max-h-[360px] w-auto mx-auto rounded-lg"
                    onchange={(detail) => (image5 = detail)}
                  >
                    <Controls>
                      {#snippet children(changeSlide)}
                        <Button
                          pill
                          class="absolute start-3 top-1/2 -translate-y-1/2 p-2 bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30 backdrop-blur-md"
                          onclick={() => changeSlide(false)}
                        >
                          <CaretLeftOutline class="w-4 h-4" />
                        </Button>
                        <Button
                          pill
                          class="absolute end-3 top-1/2 -translate-y-1/2 p-2 bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30 backdrop-blur-md"
                          onclick={() => changeSlide(true)}
                        >
                          <CaretRightOutline class="w-4 h-4" />
                        </Button>
                      {/snippet}
                    </Controls>
                    <CarouselIndicators class="bottom-2">
                      {#snippet children({ selected, index })}
                        <Indicator
                          color={selected ? "blue" : "gray"}
                          class="h-2 w-2 rounded-full transition-all duration-300 {selected
                            ? 'w-5 bg-cyan-400'
                            : 'bg-slate-600'}"
                        />
                      {/snippet}
                    </CarouselIndicators>
                  </Carousel>
                {/if}
              </div>
              <p
                class="mt-3 text-xs text-center text-slate-400 font-mono italic bg-slate-950/40 p-2 rounded-xl border border-white/5"
              >
                {image5?.alt || images_stud_2[0].alt}
              </p>
            </div>
          </div>
        </AccordionItem>
      </Accordion>
    </div>

    <!-- Study Project 1 -->
    <div
      class="bg-slate-900/60 backdrop-blur-xl border border-white/10 border-t-white/20 rounded-3xl shadow-xl overflow-hidden transition-all duration-300"
    >
      <Accordion flush class="p-6">
        <AccordionItem class="text-white border-0">
          {#snippet header()}
            <div class="flex flex-col text-left">
              <span
                class="text-xs font-mono uppercase tracking-wider text-cyan-400 font-semibold mb-1"
                >Study Project 1</span
              >
              <span
                class="text-xl sm:text-2xl font-bold text-white hover:text-cyan-300 transition-colors"
              >
                Autonomous PID Line-Tracking Robot Prototype
              </span>
            </div>
          {/snippet}
          {#snippet arrowup()}<ChevronDoubleUpOutline
              class="h-5 w-5 text-cyan-400"
            />{/snippet}
          {#snippet arrowdown()}<ChevronDoubleDownOutline
              class="h-5 w-5 text-slate-400"
            />{/snippet}

          <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 my-4">
            <div
              class="lg:col-span-7 space-y-4 text-slate-300 text-base leading-relaxed"
            >
              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Situation
                </h4>
                <p>
                  Designing an autonomous vehicle prototype to navigate unknown
                  high-contrast paths smoothly using feedback-control
                  loops[cite: 1].
                </p>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Task
                </h4>
                <p>
                  Build a LEGO Spike and Raspberry Pi vehicle integration to
                  execute closed-loop motor adjustments in real time[cite: 1].
                </p>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Action
                </h4>
                <ul class="list-disc list-inside space-y-1 ml-1 text-slate-300">
                  <li>
                    <strong class="text-slate-100">Prototyping:</strong> Iterated
                    physical weight distribution and sensor distance[cite: 1].
                  </li>
                  <li>
                    <strong class="text-slate-100"
                      >Control Implementation:</strong
                    > Written low-latency Python scripts for motor speed regulation[cite:
                    1].
                  </li>
                </ul>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Result
                </h4>
                <p class="text-slate-200">
                  Demonstrated smooth path tracking along unknown curves, laying
                  the groundwork for PID parameter tuning experiments[cite: 1].
                </p>
              </div>
            </div>

            <!-- Slideshow -->
            <div class="lg:col-span-5 flex flex-col justify-start">
              <div
                class="relative w-full rounded-2xl bg-slate-950/80 border border-white/10 p-2 shadow-inner overflow-hidden"
              >
                {#if images_stud_1.length > 0}
                  <Carousel
                    images={images_stud_1}
                    imgClass="object-contain max-h-[360px] w-auto mx-auto rounded-lg"
                    onchange={(detail) => (image4 = detail)}
                  >
                    <Controls>
                      {#snippet children(changeSlide)}
                        <Button
                          pill
                          class="absolute start-3 top-1/2 -translate-y-1/2 p-2 bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30 backdrop-blur-md"
                          onclick={() => changeSlide(false)}
                        >
                          <CaretLeftOutline class="w-4 h-4" />
                        </Button>
                        <Button
                          pill
                          class="absolute end-3 top-1/2 -translate-y-1/2 p-2 bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30 backdrop-blur-md"
                          onclick={() => changeSlide(true)}
                        >
                          <CaretRightOutline class="w-4 h-4" />
                        </Button>
                      {/snippet}
                    </Controls>
                    <CarouselIndicators class="bottom-2">
                      {#snippet children({ selected, index })}
                        <Indicator
                          color={selected ? "blue" : "gray"}
                          class="h-2 w-2 rounded-full transition-all duration-300 {selected
                            ? 'w-5 bg-cyan-400'
                            : 'bg-slate-600'}"
                        />
                      {/snippet}
                    </CarouselIndicators>
                  </Carousel>
                {/if}
              </div>
              <p
                class="mt-3 text-xs text-center text-slate-400 font-mono italic bg-slate-950/40 p-2 rounded-xl border border-white/5"
              >
                {image4?.alt || images_stud_1[0].alt}
              </p>
            </div>
          </div>
        </AccordionItem>
      </Accordion>
    </div>

    <!-- PTB 3 -->
    <div
      class="bg-slate-900/60 backdrop-blur-xl border border-white/10 border-t-white/20 rounded-3xl shadow-xl overflow-hidden transition-all duration-300"
    >
      <Accordion flush class="p-6">
        <AccordionItem class="text-white border-0">
          {#snippet header()}
            <div class="flex flex-col text-left">
              <span
                class="text-xs font-mono uppercase tracking-wider text-cyan-400 font-semibold mb-1"
                >Practice Transfer Report 3</span
              >
              <span
                class="text-xl sm:text-2xl font-bold text-white hover:text-cyan-300 transition-colors"
              >
                64-Node Raspberry Pi Cluster for HITL Testing
              </span>
            </div>
          {/snippet}
          {#snippet arrowup()}<ChevronDoubleUpOutline
              class="h-5 w-5 text-cyan-400"
            />{/snippet}
          {#snippet arrowdown()}<ChevronDoubleDownOutline
              class="h-5 w-5 text-slate-400"
            />{/snippet}

          <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 my-4">
            <div
              class="lg:col-span-7 space-y-4 text-slate-300 text-base leading-relaxed"
            >
              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Situation
                </h4>
                <p>
                  Simulating stress tests on firefighting communication
                  equipment required managing 64 independent
                  Hardware-in-the-Loop test nodes[cite: 1].
                </p>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Task
                </h4>
                <p>
                  Design a hardware rack cluster, automate node deployment, and
                  implement rapid system recovery protocols[cite: 1].
                </p>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Action
                </h4>
                <ul class="list-disc list-inside space-y-1 ml-1 text-slate-300">
                  <li>
                    <strong class="text-slate-100">Networking:</strong> Configured
                    SSH orchestration and DHCP servers across 64 nodes[cite: 1].
                  </li>
                  <li>
                    <strong class="text-slate-100">Ansible:</strong> Automated software
                    deployment and test state synchronization[cite: 1].
                  </li>
                  <li>
                    <strong class="text-slate-100">Bare Metal Recovery:</strong>
                    Built a custom Linux OS image for rapid flashing upon failure[cite:
                    1].
                  </li>
                </ul>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Result
                </h4>
                <p class="text-slate-200">
                  Reduced recovery times from hours to minutes, creating a
                  high-availability test bed for mission-critical hardware[cite:
                  1].
                </p>
              </div>
            </div>

            <!-- Slideshow -->
            <div class="lg:col-span-5 flex flex-col justify-start">
              <div
                class="relative w-full rounded-2xl bg-slate-950/80 border border-white/10 p-2 shadow-inner overflow-hidden"
              >
                {#if images_ptb_3.length > 0}
                  <Carousel
                    images={images_ptb_3}
                    imgClass="object-contain max-h-[360px] w-auto mx-auto rounded-lg"
                    onchange={(detail) => (image3 = detail)}
                  >
                    <Controls>
                      {#snippet children(changeSlide)}
                        <Button
                          pill
                          class="absolute start-3 top-1/2 -translate-y-1/2 p-2 bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30 backdrop-blur-md"
                          onclick={() => changeSlide(false)}
                        >
                          <CaretLeftOutline class="w-4 h-4" />
                        </Button>
                        <Button
                          pill
                          class="absolute end-3 top-1/2 -translate-y-1/2 p-2 bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30 backdrop-blur-md"
                          onclick={() => changeSlide(true)}
                        >
                          <CaretRightOutline class="w-4 h-4" />
                        </Button>
                      {/snippet}
                    </Controls>
                    <CarouselIndicators class="bottom-2">
                      {#snippet children({ selected, index })}
                        <Indicator
                          color={selected ? "blue" : "gray"}
                          class="h-2 w-2 rounded-full transition-all duration-300 {selected
                            ? 'w-5 bg-cyan-400'
                            : 'bg-slate-600'}"
                        />
                      {/snippet}
                    </CarouselIndicators>
                  </Carousel>
                {/if}
              </div>
              <p
                class="mt-3 text-xs text-center text-slate-400 font-mono italic bg-slate-950/40 p-2 rounded-xl border border-white/5"
              >
                {image3?.alt || images_ptb_3[0].alt}
              </p>
            </div>
          </div>
        </AccordionItem>
      </Accordion>
    </div>

    <!-- PTB 2 -->
    <div
      class="bg-slate-900/60 backdrop-blur-xl border border-white/10 border-t-white/20 rounded-3xl shadow-xl overflow-hidden transition-all duration-300"
    >
      <Accordion flush class="p-6">
        <AccordionItem class="text-white border-0">
          {#snippet header()}
            <div class="flex flex-col text-left">
              <span
                class="text-xs font-mono uppercase tracking-wider text-cyan-400 font-semibold mb-1"
                >Practice Transfer Report 2</span
              >
              <span
                class="text-xl sm:text-2xl font-bold text-white hover:text-cyan-300 transition-colors"
              >
                Smart Battery Simulator for HITL Framework
              </span>
            </div>
          {/snippet}
          {#snippet arrowup()}<ChevronDoubleUpOutline
              class="h-5 w-5 text-cyan-400"
            />{/snippet}
          {#snippet arrowdown()}<ChevronDoubleDownOutline
              class="h-5 w-5 text-slate-400"
            />{/snippet}

          <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 my-4">
            <div
              class="lg:col-span-7 space-y-4 text-slate-300 text-base leading-relaxed"
            >
              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Situation
                </h4>
                <p>
                  Testing physical batteries for edge-case faults (voltage
                  drops, thermal runaways) is dangerous, expensive, and
                  unrepeatable[cite: 1].
                </p>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Task
                </h4>
                <p>
                  Construct an I2C-based battery simulator that injects fault
                  parameters into the device under test (DUT)[cite: 1].
                </p>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Action
                </h4>
                <ul class="list-disc list-inside space-y-1 ml-1 text-slate-300">
                  <li>
                    <strong class="text-slate-100">Hybrid Hardware:</strong> Pi Pico
                    (RP2040) for real-time register emulation + Raspberry Pi 4 high-level
                    control[cite: 1].
                  </li>
                  <li>
                    <strong class="text-slate-100">I2C Protocol:</strong> Emulated
                    smart battery gauge communication[cite: 1].
                  </li>
                </ul>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Result
                </h4>
                <p class="text-slate-200">
                  Replaced manual battery testing with an automated framework
                  plugin reused across multiple product lines[cite: 1].
                </p>
              </div>
            </div>

            <!-- Slideshow -->
            <div class="lg:col-span-5 flex flex-col justify-start">
              <div
                class="relative w-full rounded-2xl bg-slate-950/80 border border-white/10 p-2 shadow-inner overflow-hidden"
              >
                {#if images_ptb_2.length > 0}
                  <Carousel
                    images={images_ptb_2}
                    imgClass="object-contain max-h-[360px] w-auto mx-auto rounded-lg"
                    onchange={(detail) => (image2 = detail)}
                  >
                    <Controls>
                      {#snippet children(changeSlide)}
                        <Button
                          pill
                          class="absolute start-3 top-1/2 -translate-y-1/2 p-2 bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30 backdrop-blur-md"
                          onclick={() => changeSlide(false)}
                        >
                          <CaretLeftOutline class="w-4 h-4" />
                        </Button>
                        <Button
                          pill
                          class="absolute end-3 top-1/2 -translate-y-1/2 p-2 bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30 backdrop-blur-md"
                          onclick={() => changeSlide(true)}
                        >
                          <CaretRightOutline class="w-4 h-4" />
                        </Button>
                      {/snippet}
                    </Controls>
                    <CarouselIndicators class="bottom-2">
                      {#snippet children({ selected, index })}
                        <Indicator
                          color={selected ? "blue" : "gray"}
                          class="h-2 w-2 rounded-full transition-all duration-300 {selected
                            ? 'w-5 bg-cyan-400'
                            : 'bg-slate-600'}"
                        />
                      {/snippet}
                    </CarouselIndicators>
                  </Carousel>
                {/if}
              </div>
              <p
                class="mt-3 text-xs text-center text-slate-400 font-mono italic bg-slate-950/40 p-2 rounded-xl border border-white/5"
              >
                {image2?.alt || images_ptb_2[0].alt}
              </p>
            </div>
          </div>
        </AccordionItem>
      </Accordion>
    </div>

    <!-- PTB 1 -->
    <div
      class="bg-slate-900/60 backdrop-blur-xl border border-white/10 border-t-white/20 rounded-3xl shadow-xl overflow-hidden transition-all duration-300"
    >
      <Accordion flush class="p-6">
        <AccordionItem class="text-white border-0">
          {#snippet header()}
            <div class="flex flex-col text-left">
              <span
                class="text-xs font-mono uppercase tracking-wider text-cyan-400 font-semibold mb-1"
                >Practice Transfer Report 1</span
              >
              <span
                class="text-xl sm:text-2xl font-bold text-white hover:text-cyan-300 transition-colors"
              >
                High-Fidelity Telemetry & Cloud Logging Pipeline
              </span>
            </div>
          {/snippet}
          {#snippet arrowup()}<ChevronDoubleUpOutline
              class="h-5 w-5 text-cyan-400"
            />{/snippet}
          {#snippet arrowdown()}<ChevronDoubleDownOutline
              class="h-5 w-5 text-slate-400"
            />{/snippet}

          <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 my-4">
            <div
              class="lg:col-span-7 space-y-4 text-slate-300 text-base leading-relaxed"
            >
              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Situation
                </h4>
                <p>
                  Granular raw logs on the MSA ALTAIR io4 were only readable via
                  physical serial ports, bottlenecking remote debugging
                  efforts[cite: 1].
                </p>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Task
                </h4>
                <p>
                  Develop a Python service to capture UART/JTAG streams and
                  forward telemetry directly into AWS and Datadog[cite: 1].
                </p>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Action
                </h4>
                <ul class="list-disc list-inside space-y-1 ml-1 text-slate-300">
                  <li>
                    <strong class="text-slate-100">Data Pipeline:</strong> Written
                    Python listeners reading UART output[cite: 1].
                  </li>
                  <li>
                    <strong class="text-slate-100">AWS Integration:</strong> Pushed
                    logs via AWS Boto3 SDK to CloudWatch[cite: 1].
                  </li>
                  <li>
                    <strong class="text-slate-100">Datadog Dashboards:</strong> Designed
                    visualization queries for error tracking[cite: 1].
                  </li>
                </ul>
              </div>

              <div>
                <h4
                  class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                >
                  Result
                </h4>
                <p class="text-slate-200">
                  Provided engineers with instant global visibility into device
                  logs, eliminating manual serial extraction[cite: 1].
                </p>
              </div>
            </div>

            <!-- Slideshow -->
            <div class="lg:col-span-5 flex flex-col justify-start">
              <div
                class="relative w-full rounded-2xl bg-slate-950/80 border border-white/10 p-2 shadow-inner overflow-hidden"
              >
                {#if images_ptb_1.length > 0}
                  <Carousel
                    images={images_ptb_1}
                    imgClass="object-contain max-h-[360px] w-auto mx-auto rounded-lg"
                    onchange={(detail) => (image = detail)}
                  >
                    <Controls>
                      {#snippet children(changeSlide)}
                        <Button
                          pill
                          class="absolute start-3 top-1/2 -translate-y-1/2 p-2 bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30 backdrop-blur-md"
                          onclick={() => changeSlide(false)}
                        >
                          <CaretLeftOutline class="w-4 h-4" />
                        </Button>
                        <Button
                          pill
                          class="absolute end-3 top-1/2 -translate-y-1/2 p-2 bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30 backdrop-blur-md"
                          onclick={() => changeSlide(true)}
                        >
                          <CaretRightOutline class="w-4 h-4" />
                        </Button>
                      {/snippet}
                    </Controls>
                    <CarouselIndicators class="bottom-2">
                      {#snippet children({ selected, index })}
                        <Indicator
                          color={selected ? "blue" : "gray"}
                          class="h-2 w-2 rounded-full transition-all duration-300 {selected
                            ? 'w-5 bg-cyan-400'
                            : 'bg-slate-600'}"
                        />
                      {/snippet}
                    </CarouselIndicators>
                  </Carousel>
                {/if}
              </div>
              <p
                class="mt-3 text-xs text-center text-slate-400 font-mono italic bg-slate-950/40 p-2 rounded-xl border border-white/5"
              >
                {image?.alt || images_ptb_1[0].alt}
              </p>
            </div>
          </div>
        </AccordionItem>
      </Accordion>
    </div>
  </div>
</div>
