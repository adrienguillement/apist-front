<template>
<section>
  <div class="column is-half is-offset-one-quarter">
    <div class="box">
      <h1 class="title is-4">Nouveau projet</h1>
      <br>
      <form>
        <fieldset>
          <fieldset class="form-group">

            <b-field label="Name" :label-position="labelPosition">
                <b-input value="" v-model="libelle" ></b-input>
            </b-field>
          </fieldset>
          <br>
          <fieldset class="form-group">
            <b-field label="Description"
                :label-position="labelPosition">
                <b-input maxlength="200" type="textarea" v-model="description"></b-input>
            </b-field>
          </fieldset>
          <button @click.stop.prevent="createProject" class="btn btn-lg btn-primary pull-xs-right" type="submit">Ajouter</button>
        </fieldset>
      </form>
    </div>
  </div>
</section>
</template>

<script>
export default {
  data() {
    return {
      libelle: '',
      description: '',
      labelPosition: 'on-border'
    };
  },
  methods: {
    createProject() {
      this.$axios.post('http://localhost:9000/api/projects', {
        libelle: this.libelle,
        description: this.description,
      }).then(res => {
        console.log(res)
        this.messageTitle = "yo les potes"
        this.isActive = true
        this.$router.push('/')
      });
    },
  },
}
</script>