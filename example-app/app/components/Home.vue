<template>
  <Page>
    <ActionBar>
      <Label text="Home"></Label>
    </ActionBar>
    <ScrollView>
      <StackLayout>
        <Button v-if="isModified" text="Enregistrer" @tap="saveData()"></Button>
        <TextField v-model="message" />
        <TextField hint="Placeholder..." v-model="search" />
        <StackLayout v-for="(xyz, i) in employes" :key="i" class="layout">
          <TextField hint="Placeholder..." v-model="employes[i].nom" />
          <Label
            class="layout__label"
            :text="xyz.adresse ? 'Nom: ' + xyz.nom : ''"
            height="70"
          />
          <Label
            class="layout__label"
            :text="xyz.adresse ? 'Age: ' + xyz.age : ''"
            height="70"
          />
          <Label
            class="layout__label"
            :text="xyz.adresse ? 'Ville: ' + xyz.adresse.ville : ''"
            height="70"
          />
          <Button
            v-if="employes[i].isModified"
            text="Enregistrer"
            @tap="showAlert"
          ></Button>
        </StackLayout>
      </StackLayout>
    </ScrollView>
  </Page>
</template>
<script>
//import ItemDetails from "./ItemDetails";
export default {
  watch: {
    message(newVal, oldVal) {
      console.log(`employes modifié de "${oldVal}" à "${newVal}"`);
      this.isModified = true;
    },
  },
  data() {
    return {
      message: "Bienvenue dans Vue avec NativeScript!",
      isModified: false,
      htmlMessage: "<strong>Bonjour !</strong>",
      search: "Valeur de ma variable!",
      element1: "Mon texte!",
      employes: [
        {
          nom: "A",
          age: "25",
          adresse: {
            ville: "Montreal",
            province: "Quebec",
            pays: "Canada",
          },
          isModified: false,
        },
        {
          nom: "B",
          age: "35",
          adresse: {
            ville: "Québec",
            province: "Quebec",
            pays: "Canada",
          },
          isModified: false,
        },
        {
          nom: "C",
          age: "45",
          adresse: {
            ville: "Laval",
            province: "Quebec",
            pays: "Canada",
          },
          isModified: false,
        },
        {
          nom: "D",
          age: "45",
          adresse: {
            ville: "Laval",
            province: "Quebec",
            pays: "Canada",
          },
          isModified: false,
        },
        {
          nom: "E",
          age: "45",
          adresse: {
            ville: "Laval",
            province: "Quebec",
            pays: "Canada",
          },
          isModified: false,
        },
        {
          nom: "F",
          age: "45",
          adresse: {
            ville: "Laval",
            province: "Quebec",
            pays: "Canada",
          },
          isModified: false,
        },
      ],
    };
  },
  methods: {
    saveData() {
      //TODO: PUT data changes
      this.isModified = false;
    },
  },
  mounted() {
    console.log({ employes: this.employes });
  },
};
</script>
<style lang="scss">
$primary-color: rgb(211, 211, 211);
$secondary-color: rgb(152, 152, 152);
.layout {
  background-color: $secondary-color;
  border-width: 1px;
  &__label {
    background-color: $primary-color;
  }
}
</style>
