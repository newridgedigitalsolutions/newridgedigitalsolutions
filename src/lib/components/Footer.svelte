<script>
  const year = new Date().getFullYear()
  const links = [
    { label: 'Home', href: '#home' },
    { label: 'Services', href: '#services' },
    { label: 'Portfolio', href: '#portfolio' },
    { label: 'About', href: '#about' },
    { label: 'Contact', href: '#contact' },
  ]
</script>

<footer class="relative bg-base-200 border-t border-slate-800">
  <div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-primary/20 to-transparent"></div>

  <div class="container mx-auto px-6 py-12">
    <div class="flex flex-col md:flex-row items-start justify-between gap-8">

      <!-- Brand -->
      <div class="max-w-xs">
        <div class="font-brand text-sm font-bold tracking-widest text-white mb-1">
          NEW RIDGE DIGITAL SOLUTIONS
        </div>
        <div class="font-inconsolata text-xs tracking-[0.2em] text-primary/50 uppercase mb-4">
          CUSTOMIZED SOLUTIONS, ENDLESS POSSIBILITIES
        </div>
        <p class="text-slate-500 text-sm leading-relaxed">
          Expert web presence & brand management for hands-on businesses.
        </p>
      </div>

      <!-- Nav links -->
      <nav class="flex flex-wrap gap-x-8 gap-y-2">
        {#each links as link}
          <a href={link.href} class="font-inconsolata text-xs tracking-widest uppercase text-slate-500 hover:text-primary transition-colors duration-200">
            {link.label}
          </a>
        {/each}
      </nav>

    </div>

    <div class="mt-10 pt-6 border-t border-slate-800 flex flex-col sm:flex-row items-center justify-between gap-4">
      <p class="font-inconsolata text-xs text-slate-600 tracking-wider">
        © {year} New Ridge Digital Solutions. All rights reserved.
      </p>
      <p class="font-inconsolata text-xs text-slate-700 tracking-wider">
        www.newridgedigitalsolutions.com
      </p>
    </div>
  </div>
</footer>
