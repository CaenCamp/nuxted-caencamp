<template>
  <div>
    <h1>Les speakers</h1>
    
    <div class="speakers">
        <div class="speaker" v-for="speaker in speakers" :key="speaker.attributes.slug">
          <div class="speaker-name">
            {{ speaker.attributes.firstName }} {{ speaker.attributes.lastName }}
          </div>
          <div class="speaker-resume">
            {{ speaker.attributes.resume }}
          </div>
          <nuxt-link to="#">Details</nuxt-link>
        </div>
    </div>

  </div>
</template>

<script>
export default {
  async asyncData() {
    const resolve = require.context("~/markdown/speakers/", true, /\.md$/)
    console.log(resolve);
    const imports = resolve.keys().map((key) => {
      const [, name] = key.match(/\/(.+)\.md$/);
      return resolve(key);
    });
    return {
      speakers: imports
    }
  },
}
</script>