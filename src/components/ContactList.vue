<template>
    <div>
    <h3>Add contact</h3>
    <form @submit.prevent="addContact">
        <label>First Name</label>
        <input v-model="newContact.firstName" placeholder="First Name">
         <label>Last Name</label>
        
        <input v-model="newContact.lastName" placeholder="Last Name">
         <label>Email</label>

        <input v-model="newContact.email" placeholder="Email">

        <button type="submit">ADD CONTACT</button>
    </form>
    
    <h3>Contact List </h3>
    <table border=1>
        <thead>
            <th>Key</th>
            <th>First Name</th>
             <th>Last Name</th>
              <th>Email</th>
        </thead>
        <tbody>
            <tr v-for="(contact, index) in contacts" :key="index">
                <td>{{index + 1}}</td>
                <td>{{contact.firstName}}</td>
                <td>{{contact.lastName}}</td>
                <td>{{contact.email}}</td>
                <td>
                    <button @click="removeContact(contact)">Remove</button>
                </td>
            </tr>
        </tbody>
    </table>
    </div>
</template>
<script>
export default {
  
    data() {
        return {
            newContact: {
                firstName: '',
                lastName: '',
                email: ''
            },
            contacts: [
                {firstName: 'John', lastName: 'Doe', email: 'example@example.com'},
                {firstName: 'Jane', lastName: 'Doe', email: 'example@example.com'},
                {firstName: 'Jack', lastName: 'Doe', email: 'example@example.com'},
                {firstName: 'Susan', lastName: 'Doe', email: 'example@example.com'},
                {firstName: 'Jasmin', lastName: 'Doe', email: 'example@example.com'}
            ]
        }
    },
      methods: {
        addContact() {
            this.contacts.push(this.newContact);
            this.newContact = {};
           
        },

        removeContact(contact) {
            let index = this.contacts.indexOf(contact);
            this.contacts.splice(index, 1);
            console.log(index);
        }
    },
}
</script>