<script>
  import { onMount } from 'svelte'

  const projects = [
    {
      title: 'Mountain Peak Construction',
      type: 'Web Design + SEO',
      description: 'A high-converting site for a regional general contractor. 3x increase in quote requests within 60 days.',
      tags: ['Construction', 'Local SEO', 'Lead Gen'],
      color: '#38bdf8',
      gradient: 'from-blue-500/20 to-cyan-500/10',
      icon: `<svg xmlns="http://www.w3.org/2000/svg" class="w-12 h-12 opacity-30" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-2 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4"/></svg>`,
    },
    {
      title: 'Ridgeline Fabrication',
      type: 'Brand Identity + Web',
      description: 'Complete brand overhaul for a custom metal fabrication shop. Logo, style guide, and full site redesign.',
      tags: ['Manufacturing', 'Branding', 'Web Design'],
      color: '#818cf8',
      gradient: 'from-indigo-500/20 to-purple-500/10',
      icon: `<svg xmlns="http://www.w3.org/2000/svg" class="w-12 h-12 opacity-30" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z"/><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/></svg>`,
    },
    {
      title: 'Clear Flow Plumbing',
      type: 'Web Design + Maintenance',
      description: 'Fast-loading emergency services site with click-to-call, service area maps, and Google Reviews integration.',
      tags: ['Plumbing', 'Mobile-First', 'Maintenance'],
      color: '#34d399',
      gradient: 'from-emerald-500/20 to-teal-500/10',
      icon: `<svg xmlns="http://www.w3.org/2000/svg" class="w-12 h-12 opacity-30" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z"/></svg>`,
    },
  ]

  let cards = []

  onMount(() => {
    const observer = new IntersectionObserver(
      (entries) => entries.forEach(e => e.isIntersecting && e.target.classList.add('visible')),
      { threshold: 0.1 }
    )
    cards.forEach(c => c && observer.observe(c))
    return () => observer.disconnect()
  })
</script>

<section id="portfolio" class="relative py-28 bg-base-100">
  <div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-secondary/20 to-transparent"></div>

  <div class="container mx-auto px-6">

    <div class="text-center mb-16">
      <div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full border border-secondary/20 bg-secondary/8 mb-5">
        <span class="font-inconsolata text-xs tracking-[0.2em] text-secondary/80 uppercase">Our Work</span>
      </div>
      <h2 class="text-4xl lg:text-5xl font-bold text-white mb-4">
        Built for Businesses<br/>
        <span class="shimmer-text">That Build Things</span>
      </h2>
      <p class="text-slate-400 max-w-xl mx-auto">
        We specialize in trades, construction, manufacturing, and service businesses.
        Real work, real results.
      </p>
    </div>

    <div class="grid lg:grid-cols-3 gap-6">
      {#each projects as project, idx}
        <div
          bind:this={cards[idx]}
          class="reveal group gradient-border"
          style="transition-delay: {idx * 120}ms"
        >
          <div class="relative rounded-xl overflow-hidden bg-base-200 h-full flex flex-col">
            <!-- Visual top area -->
            <div class="relative h-48 bg-gradient-to-br {project.gradient} flex items-center justify-center overflow-hidden border-b border-white/5">
              <div class="absolute inset-0 bg-grid opacity-50"></div>
              <!-- Decorative glow dot -->
              <div class="absolute top-4 right-4 w-2 h-2 rounded-full animate-pulse" style="background: {project.color}; box-shadow: 0 0 8px {project.color}"></div>
              <div class="relative z-10" style="color: {project.color}">
                {@html project.icon}
              </div>
              <!-- Type badge -->
              <div class="absolute bottom-4 left-4">
                <span class="font-inconsolata text-xs tracking-widest px-2.5 py-1 rounded-full border bg-base-300/80 text-slate-400 border-slate-600/50">
                  {project.type}
                </span>
              </div>
            </div>

            <!-- Content -->
            <div class="p-6 flex flex-col flex-1">
              <h3 class="text-lg font-bold text-white mb-2 group-hover:text-primary transition-colors duration-300">
                {project.title}
              </h3>
              <p class="text-slate-400 text-sm leading-relaxed flex-1 mb-5">
                {project.description}
              </p>
              <div class="flex flex-wrap gap-2">
                {#each project.tags as tag}
                  <span class="font-inconsolata text-xs px-2 py-0.5 rounded border border-slate-700 text-slate-500">
                    {tag}
                  </span>
                {/each}
              </div>
            </div>
          </div>
        </div>
      {/each}
    </div>

    <div class="text-center mt-12">
      <a href="#contact" class="btn btn-outline border-slate-600 text-slate-400 hover:border-primary hover:text-primary font-inconsolata tracking-wider">
        Discuss Your Project
        <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"/></svg>
      </a>
    </div>

  </div>

  <div class="absolute bottom-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-slate-700/50 to-transparent"></div>
</section>
