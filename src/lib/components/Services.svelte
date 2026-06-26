<script>
  import { onMount } from 'svelte'

  const services = [
    {
      icon: `<svg xmlns="http://www.w3.org/2000/svg" class="w-7 h-7" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5"><path stroke-linecap="round" stroke-linejoin="round" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/></svg>`,
      title: 'Web Design & Development',
      tagline: 'Sites that convert.',
      description: 'We craft fast, mobile-first websites built to turn visitors into customers. Clean code, sharp design, built around your business.',
      color: 'primary',
      features: ['Responsive design', 'Performance-first', 'SEO foundations'],
    },
    {
      icon: `<svg xmlns="http://www.w3.org/2000/svg" class="w-7 h-7" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5"><path stroke-linecap="round" stroke-linejoin="round" d="M12 6V4m0 2a2 2 0 100 4m0-4a2 2 0 110 4m-6 8a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4m6 6v10m6-2a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4"/></svg>`,
      title: 'Site Maintenance',
      tagline: 'Always current.',
      description: 'Keep your site secure, up-to-date, and running at peak performance. We handle the technical upkeep so you never have to worry about it.',
      color: 'secondary',
      features: ['Security updates', 'Content changes', 'Uptime monitoring'],
    },
    {
      icon: `<svg xmlns="http://www.w3.org/2000/svg" class="w-7 h-7" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5"><path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/></svg>`,
      title: 'Search Engine Optimization',
      tagline: 'Get found first.',
      description: 'From local SEO to long-tail keyword strategy, we make sure the right customers find your business — before they find your competition.',
      color: 'accent',
      features: ['Local SEO', 'Google Business', 'Monthly reporting'],
    },
    {
      icon: `<svg xmlns="http://www.w3.org/2000/svg" class="w-7 h-7" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5"><path stroke-linecap="round" stroke-linejoin="round" d="M7 21a4 4 0 01-4-4V5a2 2 0 012-2h4a2 2 0 012 2v12a4 4 0 01-4 4zm0 0h12a2 2 0 002-2v-4a2 2 0 00-2-2h-2.343M11 7.343l1.657-1.657a2 2 0 012.828 0l2.829 2.829a2 2 0 010 2.828l-8.486 8.485M7 17h.01"/></svg>`,
      title: 'Brand Identity',
      tagline: 'Look the part.',
      description: 'Logos, color systems, and brand guidelines that make your company instantly recognizable and trusted — whether online or on a job site.',
      color: 'primary',
      features: ['Logo design', 'Style guides', 'Print-ready assets'],
    },
  ]

  let cards = []

  onMount(() => {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach(e => {
          if (e.isIntersecting) e.target.classList.add('visible')
        })
      },
      { threshold: 0.15 }
    )
    cards.forEach(c => c && observer.observe(c))
    return () => observer.disconnect()
  })

  const colorMap = {
    primary: { border: 'border-primary/20', iconBg: 'bg-primary/10', iconText: 'text-primary', tag: 'badge-primary', dot: 'bg-primary' },
    secondary: { border: 'border-secondary/20', iconBg: 'bg-secondary/10', iconText: 'text-secondary', tag: 'badge-secondary', dot: 'bg-secondary' },
    accent: { border: 'border-accent/20', iconBg: 'bg-accent/10', iconText: 'text-accent', tag: 'badge-accent', dot: 'bg-accent' },
  }
</script>

<section id="services" class="relative py-28 bg-base-200/50">
  <!-- Decorative top divider -->
  <div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-primary/30 to-transparent"></div>

  <div class="container mx-auto px-6">

    <!-- Section header -->
    <div class="text-center mb-16">
      <div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full border border-primary/20 bg-primary/8 mb-5">
        <span class="font-inconsolata text-xs tracking-[0.2em] text-primary/80 uppercase">What We Do</span>
      </div>
      <h2 class="text-4xl lg:text-5xl font-bold text-white mb-4">
        Services That Move<br/>
        <span class="shimmer-text">Your Business Forward</span>
      </h2>
      <p class="text-slate-400 max-w-xl mx-auto">
        Everything a hands-on business needs to establish, grow, and maintain a powerful presence online.
      </p>
    </div>

    <!-- Services grid -->
    <div class="grid md:grid-cols-2 gap-6">
      {#each services as service, idx}
        {@const c = colorMap[service.color]}
        <div
          bind:this={cards[idx]}
          class="reveal gradient-border group cursor-default"
          style="transition-delay: {idx * 100}ms"
        >
          <div class="relative p-8 rounded-xl h-full bg-base-200 overflow-hidden">
            <!-- Hover glow -->
            <div class="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-500"
              style="background: radial-gradient(ellipse at 50% 0%, {service.color === 'primary' ? 'rgba(56,189,248,0.06)' : service.color === 'secondary' ? 'rgba(129,140,248,0.06)' : 'rgba(52,211,153,0.06)'} 0%, transparent 70%)">
            </div>

            <div class="relative z-10">
              <!-- Icon -->
              <div class="inline-flex items-center justify-center w-14 h-14 rounded-xl {c.iconBg} {c.iconText} mb-5 border {c.border} group-hover:scale-110 transition-transform duration-300">
                {@html service.icon}
              </div>

              <!-- Title + tagline -->
              <div class="mb-3">
                <h3 class="text-xl font-bold text-white">{service.title}</h3>
                <span class="font-inconsolata text-xs tracking-widest {c.iconText} uppercase opacity-70">{service.tagline}</span>
              </div>

              <!-- Description -->
              <p class="text-slate-400 text-sm leading-relaxed mb-5">{service.description}</p>

              <!-- Feature list -->
              <ul class="space-y-1.5">
                {#each service.features as f}
                  <li class="flex items-center gap-2 text-sm text-slate-400">
                    <span class="w-1.5 h-1.5 rounded-full {c.dot} shrink-0"></span>
                    {f}
                  </li>
                {/each}
              </ul>
            </div>
          </div>
        </div>
      {/each}
    </div>

  </div>

  <div class="absolute bottom-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-slate-700/50 to-transparent"></div>
</section>
