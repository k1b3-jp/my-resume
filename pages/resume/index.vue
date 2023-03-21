<template>
  <div class="container">
    <section class="summary">
      <h2>Summary</h2>
      <p>ダミーテキスト</p>
    </section>

    <section class="skill">
      <h2>Skill</h2>
      <div>
        見せ方要検討
      </div>
    </section>

    <section class="works">
      <h2>Works</h2>
      <div class="work-wrap">
        <div v-for="work in works" :key="work.id" class="activity-item">
          {{ work.title }}
        </div>
      </div>
    </section>

    <section class="certification">
      <h2>Certification</h2>
      <ul>
        <li>
          <a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ" target="_blank" rel="noopener noreferrer">
            Youtube
          </a>
        </li>
      </ul>
    </section>
  </div>
</template>

<script>
import { createClient } from 'microcms-js-sdk'

export default {
  async asyncData ({ env }) {
    const client = createClient({
      serviceDomain: env.SERVICE_DOMAIN,
      apiKey: env.API_KEY
    })

    try {
      const [resumeRes] = await Promise.all([
        client.get({ endpoint: 'resume' })
      ])
      return {
        works: resumeRes.contents
      }
    } catch (error) {
      console.error(error)
      return { works: [] }
    }
  },
  methods: {
    formatDate (date) {
      const d = new Date(date)
      const year = d.getFullYear()
      const month = `0${d.getMonth() + 1}`.slice(-2)
      return `${year}.${month}`
    }
  }
}
</script>

  <style lang="scss" scoped>
  .main-visual {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    align-items: flex-start;
    &__left {
    }
    &__right {
      &__name {
        display: flex;
        flex-wrap: wrap;
        justify-content: flex-start;
        align-items: center;
      }
    }
  }
  </style>
