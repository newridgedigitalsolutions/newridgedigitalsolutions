<script>
  let name = $state('')
  let email = $state('')
  let business = $state('')
  let message = $state('')
  let submitted = $state(false)
  let submitting = $state(false)

  async function handleSubmit() {
    if (!name || !email || !message) return
    submitting = true
    // TODO: Replace with your actual form endpoint (e.g. Formspree, Netlify Forms, etc.)
    await new Promise(r => setTimeout(r, 1000))
    submitted = true
    submitting = false
  }
</script>

<section id="contact" class="relative py-28 bg-base-100">
  <div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-primary/30 to-transparent"></div>

  <!-- Glows -->
  <div class="absolute top-1/4 right-0 w-96 h-96 bg-primary/5 rounded-full blur-[100px] pointer-events-none"></div>
  <div class="absolute bottom-0 left-0 w-64 h-64 bg-secondary/5 rounded-full blur-[80px] pointer-events-none"></div>

  <div class="container mx-auto px-6">
    <div class="max-w-2xl mx-auto">

      <div class="text-center mb-12">
        <div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full border border-primary/20 bg-primary/8 mb-5">
          <span class="font-inconsolata text-xs tracking-[0.2em] text-primary/80 uppercase">Get In Touch</span>
        </div>
        <h2 class="text-4xl lg:text-5xl font-bold text-white mb-4">
          Let's Build<br/>
          <span class="shimmer-text">Something Together</span>
        </h2>
        <p class="text-slate-400">
          Tell us about your business. We'll get back to you within one business day.
        </p>
      </div>

      {#if submitted}
        <div class="gradient-border">
          <div class="p-12 rounded-xl bg-base-200 text-center space-y-4">
            <div class="inline-flex items-center justify-center w-16 h-16 rounded-full bg-accent/15 border border-accent/30 mx-auto">
              <svg class="w-8 h-8 text-accent" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>
              </svg>
            </div>
            <h3 class="text-2xl font-bold text-white">Message Received</h3>
            <p class="text-slate-400">Thanks, {name}. We'll be in touch within one business day.</p>
          </div>
        </div>
      {:else}
        <div class="gradient-border">
          <div class="p-8 rounded-xl bg-base-200">
            <form onsubmit={(e) => { e.preventDefault(); handleSubmit() }} class="space-y-5">

              <div class="grid sm:grid-cols-2 gap-5">
                <div class="form-control">
                  <label class="label pb-1.5">
                    <span class="font-inconsolata text-xs tracking-widest text-slate-500 uppercase">Name</span>
                  </label>
                  <input
                    type="text"
                    bind:value={name}
                    placeholder="Jane Smith"
                    required
                    class="input input-bordered w-full bg-base-300 border-slate-700 focus:border-primary focus:outline-none font-inconsolata text-sm"
                  />
                </div>
                <div class="form-control">
                  <label class="label pb-1.5">
                    <span class="font-inconsolata text-xs tracking-widest text-slate-500 uppercase">Email</span>
                  </label>
                  <input
                    type="email"
                    bind:value={email}
                    placeholder="jane@yourcompany.com"
                    required
                    class="input input-bordered w-full bg-base-300 border-slate-700 focus:border-primary focus:outline-none font-inconsolata text-sm"
                  />
                </div>
              </div>

              <div class="form-control">
                <label class="label pb-1.5">
                  <span class="font-inconsolata text-xs tracking-widest text-slate-500 uppercase">Business Name</span>
                </label>
                <input
                  type="text"
                  bind:value={business}
                  placeholder="Acme Construction LLC"
                  class="input input-bordered w-full bg-base-300 border-slate-700 focus:border-primary focus:outline-none font-inconsolata text-sm"
                />
              </div>

              <div class="form-control">
                <label class="label pb-1.5">
                  <span class="font-inconsolata text-xs tracking-widest text-slate-500 uppercase">What do you need?</span>
                </label>
                <textarea
                  bind:value={message}
                  placeholder="Tell us about your business and what you're looking for..."
                  required
                  rows="5"
                  class="textarea textarea-bordered w-full bg-base-300 border-slate-700 focus:border-primary focus:outline-none font-inconsolata text-sm resize-none"
                ></textarea>
              </div>

              <button
                type="submit"
                class="btn btn-primary w-full font-inconsolata tracking-wider"
                disabled={submitting}
              >
                {#if submitting}
                  <span class="loading loading-spinner loading-sm"></span>
                  Sending...
                {:else}
                  Send Message
                  <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"/></svg>
                {/if}
              </button>

              <p class="text-center font-inconsolata text-xs text-slate-600 tracking-wider">
                Or email us directly at
                <a href="mailto:hello@newridgedigitalsolutions.com" class="text-primary hover:underline">
                  hello@newridgedigitalsolutions.com
                </a>
              </p>

            </form>
          </div>
        </div>
      {/if}

    </div>
  </div>
</section>
