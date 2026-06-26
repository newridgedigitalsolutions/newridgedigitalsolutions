<script>
  import Navbar from './lib/components/Navbar.svelte'
  import Hero from './lib/components/Hero.svelte'
  import Services from './lib/components/Services.svelte'
  import Portfolio from './lib/components/Portfolio.svelte'
  import About from './lib/components/About.svelte'
  import Contact from './lib/components/Contact.svelte'
  import Footer from './lib/components/Footer.svelte'
  import { onMount } from 'svelte'

  // Initialize scroll-reveal for .reveal elements
  onMount(() => {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach(e => {
          if (e.isIntersecting) {
            e.target.classList.add('visible')
          }
        })
      },
      { threshold: 0.1 }
    )

    // Observe all .reveal elements
    const observe = () => {
      document.querySelectorAll('.reveal').forEach(el => observer.observe(el))
    }

    // Small delay to let components mount
    setTimeout(observe, 100)

    return () => observer.disconnect()
  })
</script>

<Navbar />
<main>
  <Hero />
  <Services />
  <Portfolio />
  <About />
  <Contact />
</main>
<Footer />
