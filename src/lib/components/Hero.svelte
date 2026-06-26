<script>
  import { onMount } from 'svelte'

  let typed = $state('')
  let cursorVisible = $state(true)
  const fullText = 'Your Digital Edge.'
  let i = 0

  onMount(() => {
    // Typewriter effect
    const typeInterval = setInterval(() => {
      if (i < fullText.length) {
        typed += fullText[i]
        i++
      } else {
        clearInterval(typeInterval)
      }
    }, 70)

    return () => clearInterval(typeInterval)
  })
</script>

<section id="home" class="relative min-h-screen flex items-center overflow-hidden bg-grid">

  <!-- Ambient light blobs -->
  <div class="absolute top-1/4 left-1/4 w-96 h-96 bg-primary/8 rounded-full blur-[120px] pointer-events-none"></div>
  <div class="absolute bottom-1/3 right-1/4 w-80 h-80 bg-secondary/8 rounded-full blur-[100px] pointer-events-none"></div>
  <div class="absolute top-1/2 right-1/3 w-64 h-64 bg-accent/6 rounded-full blur-[80px] pointer-events-none"></div>

  <!-- Floating orbit rings (decorative) -->
  <div class="absolute top-1/2 right-16 -translate-y-1/2 hidden xl:block pointer-events-none">
    <div class="relative w-72 h-72 opacity-20">
      <div class="absolute inset-0 rounded-full border border-primary/30"
        style="animation: counter-spin 20s linear infinite;"></div>
      <div class="absolute inset-8 rounded-full border border-secondary/20"
        style="animation: counter-spin 14s linear infinite reverse;"></div>
      <div class="absolute inset-16 rounded-full border border-accent/20"
        style="animation: counter-spin 9s linear infinite;"></div>
      <!-- Orbiting dot -->
      <div class="absolute top-1/2 left-1/2 w-2 h-2 -mt-1 -ml-1"
        style="animation: orbit 20s linear infinite;">
        <div class="w-2 h-2 rounded-full bg-primary shadow-[0_0_8px_#38bdf8]"></div>
      </div>
      <div class="absolute top-1/2 left-1/2 w-2 h-2 -mt-1 -ml-1"
        style="animation: orbit-reverse 14s linear infinite;">
        <div class="w-2 h-2 rounded-full bg-secondary shadow-[0_0_8px_#818cf8]"></div>
      </div>
    </div>
  </div>

  <div class="container mx-auto px-6 pt-32 pb-20 relative z-10">
    <div class="max-w-3xl">

      <!-- Eyebrow -->
      <div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full border border-primary/25 bg-primary/8 mb-8 animate-fade-in">
        <span class="w-1.5 h-1.5 rounded-full bg-accent animate-pulse"></span>
        <span class="font-inconsolata text-xs tracking-[0.2em] text-primary/80 uppercase">
          Web Design & Brand Management
        </span>
      </div>

      <!-- Main Headline -->
      <h1 class="text-5xl sm:text-6xl lg:text-7xl font-bold leading-tight mb-6 animate-slide-up">
        <span class="block text-white mb-2">We Build</span>
        <span class="shimmer-text block">{typed}<span class="animate-blink text-primary">|</span></span>
      </h1>

      <!-- Sub -->
      <p class="text-lg text-slate-400 max-w-xl leading-relaxed mb-10 animate-slide-up delay-200">
        Expert web presence and brand management for hands-on businesses.
        We design and maintain websites that reach your modern customer —
        so you can focus on the work you're actually good at.
      </p>

      <!-- CTA row -->
      <div class="flex flex-wrap gap-4 animate-slide-up delay-300">
        <a href="#contact" class="btn btn-primary btn-lg font-inconsolata tracking-wider gap-2">
          Start a Project
          <svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"/></svg>
        </a>
        <a href="#portfolio" class="btn btn-outline btn-lg font-inconsolata tracking-wider border-slate-600 text-slate-400 hover:border-primary hover:text-primary">
          View Our Work
        </a>
      </div>

      <!-- Stats row -->
      <div class="flex flex-wrap gap-10 mt-16 pt-10 border-t border-slate-800 animate-slide-up delay-400">
        {#each [
          { value: '50+', label: 'Sites Launched' },
          { value: '98%', label: 'Client Retention' },
          { value: '5★', label: 'Average Rating' },
        ] as stat}
          <div>
            <div class="text-2xl font-bold text-primary">{stat.value}</div>
            <div class="font-inconsolata text-xs tracking-widest text-slate-500 uppercase mt-0.5">{stat.label}</div>
          </div>
        {/each}
      </div>

    </div>
  </div>

  <!-- Bottom fade to next section -->
  <div class="absolute bottom-0 left-0 right-0 h-32 bg-gradient-to-t from-base-100 to-transparent pointer-events-none"></div>
</section>

<style>
  @keyframes counter-spin {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }
  @keyframes orbit {
    from { transform: rotate(0deg) translateX(132px) rotate(0deg); }
    to { transform: rotate(360deg) translateX(132px) rotate(-360deg); }
  }
  @keyframes orbit-reverse {
    from { transform: rotate(0deg) translateX(100px) rotate(0deg); }
    to { transform: rotate(-360deg) translateX(100px) rotate(360deg); }
  }
</style>
