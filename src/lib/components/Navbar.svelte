<script>
  import { onMount } from 'svelte'

  let scrolled = $state(false)
  let mobileOpen = $state(false)

  const navLinks = [
    { label: 'Home', href: '#home' },
    { label: 'Services', href: '#services' },
    { label: 'Portfolio', href: '#portfolio' },
    { label: 'About', href: '#about' },
    { label: 'Contact', href: '#contact' },
  ]

  onMount(() => {
    const handler = () => { scrolled = window.scrollY > 20 }
    window.addEventListener('scroll', handler, { passive: true })
    return () => window.removeEventListener('scroll', handler)
  })

  function closeMenu() { mobileOpen = false }
</script>

<header
  class="fixed top-0 left-0 right-0 z-50 transition-all duration-500 {scrolled ? 'bg-base-100/90 backdrop-blur-md border-b border-primary/10 shadow-lg' : ''}"
>
  <div class="container mx-auto px-6 py-4">
    <div class="flex items-center justify-between">

      <!-- Brand -->
      <a href="#home" class="flex items-center gap-3 group" onclick={closeMenu}>
        <div class="relative">
          <!-- Logo placeholder — replace src with your actual logo -->
          <div class="w-10 h-10 rounded-lg bg-gradient-to-br from-primary/30 to-accent/20 border border-primary/30 flex items-center justify-center group-hover:border-primary/60 transition-all duration-300 animate-pulse-glow">
            <svg class="w-6 h-6 text-primary" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"/>
            </svg>
          </div>
          <div class="absolute inset-0 rounded-lg bg-primary/20 blur-md group-hover:bg-primary/30 transition-all duration-300"></div>
        </div>

        <div class="flex flex-col leading-tight">
          <span class="font-brand text-sm font-bold tracking-widest text-white uppercase group-hover:text-primary transition-colors duration-300">
            NEW RIDGE DIGITAL SOLUTIONS
          </span>
          <span class="font-inconsolata text-[9px] tracking-[0.25em] text-primary/60 uppercase">
            CUSTOMIZED SOLUTIONS, ENDLESS POSSIBILITIES
          </span>
        </div>
      </a>

      <!-- Desktop Nav -->
      <nav class="hidden lg:flex items-center gap-1">
        {#each navLinks as link}
          <a
            href={link.href}
            class="relative px-4 py-2 text-sm font-inconsolata tracking-wider text-slate-400 hover:text-primary transition-colors duration-200 group"
          >
            {link.label}
            <span class="absolute bottom-0 left-1/2 -translate-x-1/2 w-0 h-px bg-primary group-hover:w-full transition-all duration-300"></span>
          </a>
        {/each}

        <a href="#contact" class="ml-4 btn btn-primary btn-sm font-inconsolata tracking-wider">
          Get Started
          <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"/></svg>
        </a>
      </nav>

      <!-- Mobile Toggle -->
      <button
        class="lg:hidden btn btn-ghost btn-sm text-primary"
        onclick={() => mobileOpen = !mobileOpen}
        aria-label="Toggle menu"
      >
        {#if mobileOpen}
          <svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/></svg>
        {:else}
          <svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/></svg>
        {/if}
      </button>
    </div>

    <!-- Mobile Menu -->
    {#if mobileOpen}
      <nav class="lg:hidden mt-4 pb-4 border-t border-primary/10 pt-4 space-y-1">
        {#each navLinks as link}
          <a
            href={link.href}
            onclick={closeMenu}
            class="block px-4 py-3 font-inconsolata tracking-wider text-slate-400 hover:text-primary hover:bg-primary/5 rounded-lg transition-all duration-200"
          >
            {link.label}
          </a>
        {/each}
        <a href="#contact" onclick={closeMenu} class="block mt-3 btn btn-primary w-full font-inconsolata tracking-wider">
          Get Started
        </a>
      </nav>
    {/if}
  </div>
</header>
