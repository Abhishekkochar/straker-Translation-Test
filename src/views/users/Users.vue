<template>
  <CRow>
    <CCol col="12" xl="8">
      <CCard>
        <CCardHeader>
          Users
        </CCardHeader>
        <CCardBody>
          <table class="table">
            <thead>
              <tr>
                <th scope="col">Id</th>
                <th scope="col">Name</th>
                <th scope="col">Email</th>
                <th scope="col">City</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="user in users" :key="user.id" v-on:click="nextPage()">
                <th scope="row">{{user.id }}</th>
                <td>{{user.name }}</td>
                <td>{{user.email }}</td>
                <td>{{user.address.city }}</td>
              </tr>
            </tbody>
          </table>

        </CCardBody>
      </CCard>
    </CCol>
  </CRow>
</template>

<script>
  import axios from 'axios';
  export default{
    name:'Users',
    data(){
      return{
        users: null,
      };
    },
    created: function(){
      axios
      .get('https://jsonplaceholder.typicode.com/users')
      .then(res=>{
        this.users = res.data;
      })
    },
     
  }
</script>
