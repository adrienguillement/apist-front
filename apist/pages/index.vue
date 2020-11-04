
<template>
  <p v-if="$fetchState.pending">Récupération des projets...</p>
  <p v-else-if="$fetchState.error">ptain il y a un bug fréro</p>
  <div v-else>
    <h1>Projets</h1>
    <ul>
      <li v-for="project of projects.data">
        <Card :id="project._id"
              :note="project.note"
              :title="project.libelle"
              :description="project.description" />
      </li>
    </ul>
    <button @click="$fetch">Refresh</button>
  </div>
</template>

<script>
import Card from '~/components/Card'

export default {
  data() {
    return {
      projects: []
    }
  },
  async fetch() {
    this.projects = await fetch(
      'http://localhost:9000/api/projects'
    ).then(res => res.json())
  },
}
</script>
