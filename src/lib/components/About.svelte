<script>
  import { onMount } from 'svelte'

  let section
  let visible = $state(false)

  const values = [
    { label: 'No fluff.', detail: 'We tell you what your site needs and why — not what sounds impressive.' },
    { label: 'Long-term.', detail: 'We aim to be your web partner for years, not just the one-time build.' },
    { label: 'Hands-on.', detail: 'Direct communication, real people. No ticket queues, no offshore handoffs.' },
  ]

  onMount(() => {
    const observer = new IntersectionObserver(
      ([e]) => { if (e.isIntersecting) visible = true },
      { threshold: 0.2 }
    )
    observer.observe(section)
    return () => observer.disconnect()
  })
</script>

<section id="about" class="relative py-28 bg-base-200/50" bind:this={section}>
  <div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-accent/20 to-transparent"></div>

  <!-- Background glow -->
  <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[400px] bg-accent/4 rounded-full blur-[120px] pointer-events-none"></div>

  <div class="container mx-auto px-6">
    <div class="grid lg:grid-cols-2 gap-16 items-center">

      <!-- Left: Text -->
      <div class:animate-slide-up={visible}>
        <div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full border border-accent/20 bg-accent/8 mb-6">
          <span class="font-inconsolata text-xs tracking-[0.2em] text-accent/80 uppercase">Who We Are</span>
        </div>

        <h2 class="text-4xl lg:text-5xl font-bold text-white mb-6 leading-tight">
          Digital Strategy<br/>
          <span class="shimmer-text">Built for the Real World</span>
        </h2>

        <p class="text-slate-400 leading-relaxed mb-5">
          New Ridge Digital Solutions was founded with one idea: hands-on businesses deserve the same quality of web presence as the big guys — without the agency runaround.
        </p>
        <p class="text-slate-400 leading-relaxed mb-10">
          We work primarily with contractors, fabricators, service companies, and specialty trades. We understand your customers, your timelines, and what "professional" actually means in your industry.
        </p>

        <!-- Values -->
        <div class="space-y-4">
          {#each values as v, i}
            <div class="flex items-start gap-4 p-4 rounded-lg bg-base-300/50 border border-slate-700/50 hover:border-accent/30 transition-colors duration-300"
              style="transition-delay: {i * 80}ms">
              <div class="w-2 h-2 rounded-full bg-accent shrink-0 mt-2"></div>
              <div>
                <span class="font-bold text-white">{v.label}</span>
                <span class="text-slate-400 ml-2">{v.detail}</span>
              </div>
            </div>
          {/each}
        </div>
      </div>

      <!-- Right: Visual card -->
      <div class:animate-fade-in={visible} class="opacity-0" class:opacity-100={visible}>
        <div class="gradient-border animate-float">
          <div class="relative p-8 rounded-xl bg-base-200 overflow-hidden">
            <!-- Decorative grid -->
            <div class="absolute inset-0 bg-grid opacity-50"></div>

            <div class="relative z-10 space-y-6">
              <!-- Terminal-style block -->
              <div class="font-inconsolata text-sm space-y-1">
                <div class="text-slate-600 text-xs mb-3 tracking-widest">// about.nrds</div>
                <div><span class="text-secondary">const</span> <span class="text-primary">team</span> <span class="text-slate-500">=</span> <span class="text-accent">'humans, not chatbots'</span></div>
                <div><span class="text-secondary">const</span> <span class="text-primary">specialty</span> <span class="text-slate-500">=</span> <span class="text-accent">'trade &amp; industrial'</span></div>
                <div><span class="text-secondary">const</span> <span class="text-primary">approach</span> <span class="text-slate-500">=</span> <span class="text-accent">'direct + honest'</span></div>
                <div class="pt-2"><span class="text-primary">nrds</span><span class="text-slate-500">.</span><span class="text-secondary">getStarted</span><span class="text-slate-500">()</span></div>
              </div>

              <div class="h-px bg-gradient-to-r from-primary/20 via-secondary/20 to-accent/20"></div>

              <!-- Quick facts -->
              <div class="grid grid-cols-2 gap-4">
                {#each [
                  { n: '50+', l: 'Projects' },
                  { n: '5+', l: 'Years' },
                  { n: '98%', l: 'Retention' },
                  { n: '24h', l: 'Response' },
                ] as s}
                  <div class="text-center p-3 rounded-lg bg-base-300/60">
                    <div class="text-xl font-bold text-primary">{s.n}</div>
                    <div class="font-inconsolata text-xs text-slate-500 tracking-widest uppercase">{s.l}</div>
                  </div>
                {/each}
              </div>
            </div>
          </div>
        </div>
      </div>

    </div>
  </div>

  <div class="absolute bottom-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-slate-700/50 to-transparent"></div>
</section>
