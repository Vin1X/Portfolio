<script>
  import { Timeline, TimelineItem } from "flowbite-svelte";
</script>

<div class="my-4 p-4 border-2 border-gray-300 bg-gray-500/90 rounded-md">
  <h3 class="font-semibold mb-2">
    About Me - Vincent Walura | Junior Software Developer | Berlin
  </h3>

  <div>
    I am a Computer Science graduate specialized in embedded logic and systems.
    Through my dual-study program (2022–2025) at HWR Berlin and MSA
    Technologies, I gained three years of hands-on industry experience. I
    contribute across the entire development lifecycle—from engineering
    hardware-near logic to orchestrating complex system integrations. I am
    driven by Berlin’s fast-paced tech ecosystem and passionate about solving
    real-world problems with efficient, maintainable code.
  </div>
</div>

<div class="my-4 p-4 border-2 border-gray-300 bg-gray-500/90 rounded-md">
  <h3 class="font-semibold mb-2">Technical Expertise</h3>
  <ul class="list-disc list-inside ml-4">
    <li>Languages: Python (Advanced), C/C++, JavaScript, HTML/CSS.</li>
    <li>
      Embedded & Hardware: I2C, SPI, UART, JTAG/SWD, Raspberry Pi Ecosystem,
      Linux.
    </li>
    <li>
      Infrastructure & Cloud: Ansible, AWS, Linux System Administration, SSH
      Orchestration.
    </li>
    <li>Networking: DHCP, TCP/IP, ICMP, HTTP.</li>
  </ul>
</div>

<!-- <div class="my-4 p-4 border-2 border-gray-300 bg-gray-500/90 rounded-md">
  <h3 class="font-semibold mb-2">What I am learning now</h3>

  <div></div>
</div> -->

<div
  class="my-4 p-4 border-2 border-gray-300 bg-gray-500 bg-opacity-75 rounded-md"
>
  <h3 class="font-semibold mb-2">Experience</h3>
  <Timeline>
    <TimelineItem title="" date="October 2022 - September 2025">
      <h3 class="font-semibold">
        MSA Technologies and Enterprise Services GmbH
      </h3>
      <p>Software Developer (Dual student)</p>
    </TimelineItem>
  </Timeline>
</div>

<div
  class="my-4 p-4 border-2 border-gray-300 bg-gray-500 bg-opacity-75 rounded-md"
>
  <h3 class="font-semibold mb-2">Education</h3>
  <Timeline>
    <TimelineItem title="" date="October 2022 - September 2025">
      <h3 class="font-semibold">Hochschule für Wirtschaft und Recht Berlin</h3>
      <p>Dual study program</p>
      <p>Degree: B.Sc. Computer Science</p>
    </TimelineItem>
    <TimelineItem title="" date="August 2019 - July 2022">
      <h3 class="font-semibold">Carlo-Schmid Oberschule</h3>
      <p>High School Diploma (Abitur)</p>
    </TimelineItem>
  </Timeline>
</div>
