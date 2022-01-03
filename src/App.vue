<template>
  <div class="container">
    <Header />
    <AddContact @add-contact="AddContact" />
    <Contacts
      @delete-contact="deleteContact"
      @update-contact="updateContact"
      :contacts="contacts"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import AddContact from "./components/AddContact.vue";
import Contacts from "./components/Contacts.vue";
export default {
  name: "App",
  components: {
    Header,
    AddContact,
    Contacts,
  },
  data() {
    return {
      contacts: [],
    };
  },
  methods: {
    AddContact(contact) {
      this.contacts = [...this.contacts, contact];
    },
    updateContact(contact) {
      const Update = this.contacts.map((con) =>
        con.id === contact.id ? contact : con
      );
      this.contacts = [Update];
    },
    deleteContact(id) {
      this.contacts = this.contacts.filter((contact) => contact.id !== id);
    },
  },
  created() {
    this.contacts = [
      {
        id: 1,
        name: "Doctors Appoitment",
        phone: "March 1st at 2:30pm",
      },
      {
        id: 2,
        name: "Meeting at School",
        phone: "March 3rd at 1:30pm",
      },
      {
        id: 3,
        name: "Food Shopping",
        phone: "March 3rd at 11:30am",
      },
    ];
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: "Roboto Mono";
}

.container {
  max-width: 500px;
  margin: 30px;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

.btn {
  display: inline-block;
  background-color: black;
  color: white;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}

.btn-group {
  display: flex;
  justify-content: space-evenly;
  gap: 20px;
}

.btn-seprate {
  display: flex;
  gap: 25px;
}
.edit-btn {
  color: yellow;
}

.contact {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

.contact.reminder {
  border-left: 5px solid green;
}

.contact h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px 0;
}

.form-control label {
  display: block;
}

.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.form-control-check label {
  flex: 1;
}

.form-control-check input {
  flex: 2;
  height: 20px;
}

footer {
  margin-top: 30px;
  text-align: center;
}
</style>
