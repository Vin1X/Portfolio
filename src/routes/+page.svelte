<script>
  import { Timeline, TimelineItem } from "flowbite-svelte";
</script>

<div
  class=" bg-slate-900/30 backdrop-blur-xl p-6 border-2 border-white/40 rounded-3xl"
>
  <h2 class="font-semibold mb-2">
    About Me - Vincent Walura | Junior Software Developer | Berlin
  </h2>

  <div class="text-xl">
    I am a Computer Science graduate specialized in embedded logic and systems.
    Through my dual-study program (2022–2025) at <a
      href="https://www.hwr-berlin.de/hwr-berlin/fachbereiche-und-bps/fb-2-duales-studium/duales-studium-im-profil/duales-konzept"
      >HWR Berlin</a
    >
    and <a href="https://de.msasafety.com/about">MSA Technologies</a>, I gained
    three years of hands-on industry experience. I contribute across the entire
    development lifecycle—from engineering hardware-near logic to orchestrating
    complex system integrations. I am driven by Berlin’s fast-paced tech
    ecosystem and passionate about solving real-world problems with efficient,
    maintainable code.
  </div>
</div>

<div
  class=" bg-slate-900/30 backdrop-blur-xl my-8 p-6 border-2 border-white/40 rounded-3xl"
>
  <h2 class="font-semibold mb-2">Technical Expertise</h2>
  <ul class="list-disc list-inside ml-4 text-xl">
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

<div class="my-8 flex flex-col gap-6 lg:flex-row">
  <div
    class="bg-slate-900/30 backdrop-blur-xl p-6 border-2 border-white/40 rounded-3xl lg:flex-1"
  >
    <h2 class="font-semibold mb-2">Experience</h2>
    <Timeline>
      <TimelineItem title="" date="October 2022 - September 2025">
        <h3 class="font-semibold">
          MSA Technologies and Enterprise Services GmbH
        </h3>
        <p class="text-xl">Software Developer (Dual student)</p>
      </TimelineItem>
    </Timeline>
  </div>

  <div
    class="bg-slate-900/30 backdrop-blur-xl p-6 border-2 border-white/40 rounded-3xl lg:flex-1"
  >
    <h2 class="font-semibold mb-2">Education</h2>
    <Timeline>
      <TimelineItem title="" date="October 2022 - September 2025">
        <h3 class="font-semibold">
          Hochschule für Wirtschaft und Recht Berlin
        </h3>
        <p class="text-xl">Dual study program</p>
        <p class="text-xl">Degree: B.Sc. Computer Science</p>
      </TimelineItem>
      <TimelineItem title="" date="August 2019 - July 2022">
        <h3 class="font-semibold">Carlo-Schmid Oberschule</h3>
        <p class="text-xl">High School Diploma (Abitur)</p>
      </TimelineItem>
    </Timeline>
  </div>
</div>

<div
  class=" bg-slate-900/30 backdrop-blur-xl my-8 p-6 border-2 border-white/40 rounded-3xl"
>
  <h2 class="font-semibold mb-2">What I currently do</h2>

  <div class="text-xl">
    Right now, I am focused on improving my C and C++ skills by working on
    various mini projects related to embedded systems with a Raspberry Pi.
    <br />Also with that I am establishing a "framework" with an GUI that is
    accessible via web.
    <br /><br />
    All of my private projects are open source and available on my
    <a href="https://github.com/Vin1X">GitHub profile</a>.
  </div>
</div>
