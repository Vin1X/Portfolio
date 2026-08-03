<script lang="ts">
  // Tech skills organized into categories
  const skills = [
    {
      category: "Languages",
      items: ["Python (Advanced)", "C#", "JavaScript", "HTML / CSS"],
    },
    {
      category: "Embedded & Hardware",
      items: [
        "I2C",
        "SPI",
        "UART",
        "JTAG / SWD",
        "Raspberry Pi",
        "Linux Kernel",
      ],
    },
    {
      category: "Infrastructure & Cloud",
      items: ["Ansible", "AWS", "Linux", "SSH"],
    },
    {
      category: "Networking",
      items: ["DHCP", "TCP/IP", "ICMP", "HTTP"],
    },
  ];
</script>

<div class="max-w-5xl mx-auto space-y-12 py-6">
  <!-- Hero Section -->
  <section class="text-center py-6 relative">
    <h1
      class="text-5xl sm:text-6xl md:text-7xl font-bold tracking-tight mb-6 bg-linear-to-r from-white via-slate-200 to-slate-400 bg-clip-text text-transparent"
    >
      Vincent Walura
    </h1>

    <p
      class="text-lg sm:text-xl md:text-2xl text-slate-400 mb-10 max-w-2xl mx-auto font-light leading-relaxed"
    >
      Software Developer specializing in <span class="text-cyan-300 font-normal"
        >embedded systems</span
      >
      and <span class="text-blue-300 font-normal">cloud infrastructure</span>.
    </p>
  </section>

  <!-- About Me Card -->
  <section class="relative group">
    <div
      class="absolute -inset-0.5 bg-linear-to-r from-blue-500/20 to-cyan-500/20 rounded-3xl blur-xl opacity-50 group-hover:opacity-100 transition duration-500"
    ></div>

    <div
      class="relative bg-slate-900/60 backdrop-blur-xl p-8 sm:p-10 border border-white/10 border-t-white/20 rounded-3xl shadow-2xl"
    >
      <h2
        class="text-2xl font-semibold text-white mb-4 tracking-tight flex items-center gap-3"
      >
        <span class="w-2 h-6 bg-cyan-400 rounded-full"></span>
        About Me
      </h2>

      <p class="text-slate-300 text-base sm:text-lg leading-relaxed font-light">
        I am a Computer Science graduate specialized in embedded logic and
        systems with current interest in cloud infrastructure. Through my
        dual-study program (2022–2025) at
        <a
          href="https://www.hwr-berlin.de/hwr-berlin/fachbereiche-und-bps/fb-2-duales-studium/duales-studium-im-profil/duales-konzept"
          target="_blank"
          rel="noreferrer"
          class="text-cyan-400 underline underline-offset-4 decoration-cyan-400/40 hover:decoration-cyan-400 transition-colors"
          >HWR Berlin</a
        >
        and
        <a
          href="https://de.msasafety.com/about"
          target="_blank"
          rel="noreferrer"
          class="text-cyan-400 underline underline-offset-4 decoration-cyan-400/40 hover:decoration-cyan-400 transition-colors"
          >MSA Technologies</a
        >, I gained three years of hands-on industry experience. I contribute
        across the entire development lifecycle—from engineering hardware-near
        logic to orchestrating complex system integrations. Driven by Berlin’s
        fast-paced tech ecosystem, I am passionate about solving real-world
        problems with efficient, maintainable code.
      </p>
    </div>
  </section>

  <!-- Technical Expertise -->
  <section
    class="bg-slate-900/60 backdrop-blur-xl p-8 sm:p-10 border border-white/10 border-t-white/20 rounded-3xl shadow-2xl"
  >
    <h2
      class="text-2xl font-semibold text-white mb-6 tracking-tight flex items-center gap-3"
    >
      <span class="w-2 h-6 bg-blue-500 rounded-full"></span>
      Technical Expertise
    </h2>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
      {#each skills as group}
        <div
          class="p-5 rounded-2xl bg-slate-950/40 border border-white/5 hover:border-white/10 transition-colors"
        >
          <h3
            class="text-xs font-semibold uppercase tracking-wider text-slate-400 mb-3"
          >
            {group.category}
          </h3>
          <div class="flex flex-wrap gap-2">
            {#each group.items as item}
              <span
                class="px-3 py-1.5 rounded-lg text-sm bg-slate-800/80 border border-white/10 text-slate-200 font-mono"
              >
                {item}
              </span>
            {/each}
          </div>
        </div>
      {/each}
    </div>
  </section>

  <!-- Experience & Education Grid -->
  <div
    id="experience"
    class="grid grid-cols-1 lg:grid-cols-2 gap-8 scroll-mt-24"
  >
    <!-- Experience -->
    <section
      class="bg-slate-900/60 backdrop-blur-xl p-8 border border-white/10 border-t-white/20 rounded-3xl shadow-2xl flex flex-col justify-between"
    >
      <div>
        <h2
          class="text-2xl font-semibold text-white mb-6 tracking-tight flex items-center gap-3"
        >
          <span class="w-2 h-6 bg-cyan-400 rounded-full"></span>
          Experience
        </h2>

        <div class="relative pl-6 border-l border-white/10 space-y-8 my-2">
          <div class="relative">
            <!-- Timeline Glow Node -->
            <span
              class="absolute -left-7.75 top-1.5 w-3 h-3 rounded-full bg-cyan-400 ring-4 ring-slate-900 shadow-[0_0_10px_#22d3ee]"
            ></span>
            <span
              class="text-xs font-mono text-cyan-400 uppercase tracking-wider"
              >October 2025 — Today</span
            >
            <h3 class="text-lg font-semibold text-white mt-1">
              Kosmetik Atelier Laura
            </h3>
            <p class="text-slate-400 text-sm mt-0.5">
              Frontend Developer / IT Specialist
            </p>
          </div>

          <div class="relative">
            <!-- Timeline Glow Node -->
            <span
              class="absolute -left-7.75 top-1.5 w-3 h-3 rounded-full bg-slate-600 ring-4 ring-slate-900 shadow-[0_0_10px_#22d3ee]"
            ></span>
            <span
              class="text-xs font-mono text-slate-500 uppercase tracking-wider"
              >October 2022 — September 2025</span
            >
            <h3 class="text-lg font-semibold text-white mt-1">
              MSA Technologies & Enterprise Services
            </h3>
            <p class="text-slate-400 text-sm mt-0.5">
              Software Developer (Dual Student)
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Education -->
    <section
      class="bg-slate-900/60 backdrop-blur-xl p-8 border border-white/10 border-t-white/20 rounded-3xl shadow-2xl flex flex-col justify-between"
    >
      <div>
        <h2
          class="text-2xl font-semibold text-white mb-6 tracking-tight flex items-center gap-3"
        >
          <span class="w-2 h-6 bg-purple-500 rounded-full"></span>
          Education
        </h2>

        <div class="relative pl-6 border-l border-white/10 space-y-8 my-2">
          <!-- College -->
          <div class="relative">
            <span
              class="absolute -left-7.75 top-1.5 w-3 h-3 rounded-full bg-purple-400 ring-4 ring-slate-900 shadow-[0_0_10px_#c084fc]"
            ></span>
            <span
              class="text-xs font-mono text-purple-400 uppercase tracking-wider"
              >October 2022 — September 2025</span
            >
            <h3 class="text-lg font-semibold text-white mt-1">HWR Berlin</h3>
            <p class="text-slate-400 text-sm mt-0.5">
              B.Sc. Computer Science (Dual Study)
            </p>
          </div>

          <!-- School -->
          <div class="relative">
            <span
              class="absolute -left-7.75 top-1.5 w-3 h-3 rounded-full bg-slate-600 ring-4 ring-slate-900"
            ></span>
            <span
              class="text-xs font-mono text-slate-500 uppercase tracking-wider"
              >August 2019 — July 2022</span
            >
            <h3 class="text-lg font-semibold text-white mt-1">
              Carlo-Schmid Oberschule
            </h3>
            <p class="text-slate-400 text-sm mt-0.5">
              High School Diploma (Abitur)
            </p>
          </div>
        </div>
      </div>
    </section>
  </div>

  <!-- What I currently do -->
  <section
    class="bg-slate-900/60 backdrop-blur-xl p-8 sm:p-10 border border-white/10 border-t-white/20 rounded-3xl shadow-2xl"
  >
    <h2
      class="text-2xl font-semibold text-white mb-4 tracking-tight flex items-center gap-3"
    >
      <span class="w-2 h-6 bg-teal-400 rounded-full"></span>
      What I Currently Do
    </h2>

    <p
      class="text-slate-300 text-base sm:text-lg leading-relaxed font-light mb-6"
    >
      Currently, I am co-developing an unannounced mobile game using C# and
      Unity. I focus on the full stack—building out the gameplay systems on the
      frontend, alongside a dedicated backend and database for player management
      and cloud storage.
    </p>

    <a
      href="https://github.com/Vin1X"
      target="_blank"
      rel="noreferrer"
      class="inline-flex items-center gap-2 text-sm font-medium text-cyan-400 hover:text-cyan-300 transition-colors"
    >
      <span>Explore my open-source work on GitHub</span>
      <svg
        class="w-4 h-4"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M14 5l7 7m0 0l-7 7m7-7H3"
        />
      </svg>
    </a>
  </section>
</div>
