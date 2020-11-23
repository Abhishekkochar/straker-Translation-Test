<template>
  <CRow>
    <CCol col="12" xl="8">
      <CCard>
        <CCardHeader>
          Posts
        </CCardHeader>
        <CCardBody>
          <table class="table">
            <thead>
              <tr>
                <th scope="col">Id</th>
                <th scope="col">Title</th>

              </tr>
            </thead>
            <tbody>
              <tr v-for="post in posts" :key="post.userId">
                <th scope="row">{{post.userId }}</th>
                <span @mouseover="hover = true" @mouseleave="hover = false">
                <td>{{post.title }}</td>
                 </span>
                 <span v-if="hover">
                <td>{{post.body }}</td>
                </span>
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
    name:'User',
    data(){
      return{
        hover:false,
        posts: null,
      };
    },
    created: function(){
      axios
      .get('https://jsonplaceholder.typicode.com/posts')
      .then(res=>{
        this.posts = res.data;
      })
    },
     
  }

</script>
