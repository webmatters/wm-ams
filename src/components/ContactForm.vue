<template>
  <div class="pt-16 mx-auto pb-4 px-4 text-white">
    <h2 class="font-bold mb-6 text-xl text-center">Get a Free 30-minute Strategy Session</h2>
    <div
      class="mb-12 text-center"
    >We'll walk through our discovery process to better understand your needs and recommend a web strategy to achieve your goals.</div>

    <div class="text-lg sm:text-lg mb-16">
      <form
        name="contact"
        method="post"
        v-on:submit.prevent="handleContactSubmit"
        action="/success/"
        data-netlify="true"
        data-netlify-honeypot="bot-field"
        class="mb-12 text-secondary"
      >
        <div class="flex flex-wrap mb-6 -mx-4">
          <div class="w-full md:w-1/2 mb-6 md:mb-0 px-4">
            <input type="hidden" name="form-name" value="contact" />
            <p hidden>
              <label>
                Don’t fill this out:
                <input name="bot-field" />
              </label>
            </p>
            <label class="block mb-2" for="name">Full Name</label>

            <input
              type="text"
              name="name"
              id="name"
              placeholder="Eileen Dover"
              v-model="contactFormData.name"
              class="block w-full bg-background-form border border-border-color-primary shadow rounded outline-none focus:border-primary mb-2 p-4"
              required
            />
          </div>

          <div class="w-full px-4 md:w-1/2">
            <label class="block text-copy-primary mb-2" for="email">Email Address</label>

            <input
              type="email"
              name="email"
              id="email"
              placeholder="email@example.com"
              v-model="contactFormData.email"
              class="block w-full bg-background-form border border-border-color-primary shadow rounded outline-none focus:border-primary mb-2 p-4"
              required
            />
          </div>
        </div>

        <div class="w-full mb-12">
          <label class="block text-copy-primary mb-2" for="message">Message</label>

          <textarea
            id="message"
            rows="5"
            name="message"
            class="block w-full bg-background-form border border-border-color-primary shadow rounded outline-none appearance-none focus:border-primary mb-2 px-4 py-4"
            placeholder="Enter your message here."
            v-model="contactFormData.message"
            required
          ></textarea>
        </div>

        <div class="flex justify-end w-full">
          <button
            type="submit"
            class="block bg-primary hover:primary text-white text-sm font-semibold tracking-wide uppercase shadow rounded cursor-pointer px-6 py-3"
          >Submit</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      contactFormData: {
        name: '',
        email: '',
        message: '',
      },
    }
  },
  methods: {
    encode(data) {
      return Object.keys(data)
        .map(
          key => encodeURIComponent(key) + '=' + encodeURIComponent(data[key])
        )
        .join('&')
    },
    handleContactSubmit(e) {
      fetch('/', {
        method: 'POST',
        headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
        body: this.encode({
          'form-name': e.target.getAttribute('name'),
          ...this.contactFormData,
        }),
      })
        .then(() => this.$router.push('/success'))
        .catch(error => alert(error))
    },
  },
}
</script>
