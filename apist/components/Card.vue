<template>
<div class="column is-half is-offset-one-quarter">
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">
        {{ note }}
      </p>
      <p class="card-header-title">
        {{ title }}
      </p>
      <a href="#" class="card-header-icon" aria-label="more options">
        <span class="icon">
          <i class="fas fa-angle-down" aria-hidden="true"></i>
        </span>
      </a>
    </header>
    <div class="card-content">
      <div class="content">
        {{ description }}
      </div>
    </div>
    <footer class="card-footer">
      <a @click.prevent="addNote" class="card-footer-item">+</a>
      <a @click.prevent="removeNote" class="card-footer-item">-</a>
    </footer>
  </div>
</div>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      required: true
    },
    note: {
      type: Number,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    description: {
      type: String,
      required: true
    }
  },
  methods: {
    addNote() {
      let note = this.note;
      note++
      this.$axios.put('http://localhost:9000/api/projects/' + this.id, {
        libelle: this.libelle,
        description: this.description,
        note: note
      }).then(res => {
        this.note = note
      });
    },
    removeNote() {
      let note = this.note;
      note--
      this.$axios.put('http://localhost:9000/api/projects/' + this.id, {
        libelle: this.libelle,
        description: this.description,
        note: note
      }).then(res => {
        this.note = note
      });
    },
  },
}
</script>