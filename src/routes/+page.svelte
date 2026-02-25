<script>
  import { Timeline, TimelineItem } from "flowbite-svelte";
  import TextSlot from "$lib/components/TextSlot.svelte";
</script>

<TextSlot
  heading="About Me - Vincent Walura | Junior Software Developer | Berlin"
  content="I am a Computer Science graduate with a focus on building robust, scalable applications. During my dual-study program (2022-2025), I have had a really good balance between academic theory at the 'Hochschule für Wirtschaft und Recht Berlin' (HWR) and proper industry practice by working within a large embedded systems company. This experience alowed me to contribute across the full development lifecycle from low-level logic to high.level system integration. I am passionate about efficient problem solving and the tech that is being developed in Berlin."
/>
<TextSlot
  heading="Technical Expertise"
  content="Throughout my degree and work I have developed a versatile foundation in Python, solid basics with C, C++ and complemented by modern web technologies with various frameworks. I thrive in environments where hardware meets software."
/>
<TextSlot heading="What I am learning now" content="" />

<div
  class="my-4 p-4 border-2 border-gray-300 bg-gray-500 bg-opacity-75 rounded-md"
>
  <span style="font-weight: 600; font-size: 2rem; color: #7dd3fc;"
    >Education</span
  >
  <Timeline>
    <TimelineItem title="" date="October 2022 - September 2025">
      <h3 class="font-semibold">
        Hochschule für Wirtschaft und Recht Berlin & <br />MSA Technologies and
        Enterprise Services GmbH
      </h3>
      <p>Dual study program</p>
      <p>Degree: B.Sc. Computer Science</p>
    </TimelineItem>
    <TimelineItem title="" date="August 2019 - July 2022">
      <h3 class="font-semibold">Carlo-Schmid Oberschule</h3>
      <p>High School Diploma (Abitur)</p>
    </TimelineItem>
  </Timeline>
</div>
