<template>
  <div class="container">
    <div class="main-visual">
      <div class="main-visual__left">
        <img src="https://placehold.jp/400x400.png" alt="">
      </div>
      <div class="main-visual__right">
        <div class="main-visual__right__name">
          <h2>Kotaro<br>Kibe</h2>
          <h3>Engineer</h3>
        </div>
        <p>自己紹介</p>
      </div>
    </div>

    <section class="experience">
      <h2>Experience</h2>
      <div class="experience-wrap">
        <div v-for="experience in experiences" :key="experience.id" class="experience-item">
          <div>{{ formatDate(experience.start) }}<span>-</span>{{ formatDate(experience.end) }}</div>
          <h4>{{ experience.title }}</h4>
          <h5>{{ experience.job }}</h5>
        </div>
      </div>
    </section>

    <section class="sns">
      <h2>SNS</h2>
    </section>

    <section class="activity">
      <h2>Activity</h2>
      <div class="activity-wrap">
        <div v-for="activity in activities" :key="activity.id" class="activity-item">
          <a :href="activity.url" target="_blank">{{ activity.title }}</a>
        </div>
      </div>
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
      const [activityRes, experienceRes] = await Promise.all([
        client.get({ endpoint: 'activity' }),
        client.get({ endpoint: 'experience' })
      ])
      return {
        activities: activityRes.contents,
        experiences: experienceRes.contents
      }
    } catch (error) {
      console.error(error)
      return { activities: [], experiences: [] }
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
