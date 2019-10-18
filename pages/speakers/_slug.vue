<template>
  <div>
    <div class="post-title">
      <h1>Test</h1>
    </div>
    <div class="content">Hello</div>
  </div>
</template>

<script>
  export default {
    async asyncData({ params }) {
      try {
        let post = await import(`~/markdown/speakers/${params.slug}.md`);
        console.debug(post)
        return {
          post
        }
      } catch(err) {
        console.debug(err)
        return false
      }
    }
  }
</script>