<template>
    <div class="col-md-4">
        <div class="card mb-3">
            <div class="card-body">
                <div class="row">
                    <div class="d-flex justify-content-between">
                        <div class="py-2">
                            <!-- Call category -->
                            <h6 class="text-info"> {{article.category}} </h6>
                        </div >
                        <div class="d-flex">
                            <div v-if="article.author.id == 1" class="p-1">
                                <NuxtLink :to="'/blog/edit/'+article.id" :article="article">
                                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-pencil text-black-50" viewBox="0 0 16 16">
                                        <path d="M12.146.146a.5.5 0 0 1 .708 0l3 3a.5.5 0 0 1 0 .708l-10 10a.5.5 0 0 1-.168.11l-5 2a.5.5 0 0 1-.65-.65l2-5a.5.5 0 0 1 .11-.168l10-10zM11.207 2.5 13.5 4.793 14.793 3.5 12.5 1.207 11.207 2.5zm1.586 3L10.5 3.207 4 9.707V10h.5a.5.5 0 0 1 .5.5v.5h.5a.5.5 0 0 1 .5.5v.5h.293l6.5-6.5zm-9.761 5.175-.106.106-1.528 3.821 3.821-1.528.106-.106A.5.5 0 0 1 5 12.5V12h-.5a.5.5 0 0 1-.5-.5V11h-.5a.5.5 0 0 1-.468-.325z"/>
                                    </svg>
                                </NuxtLink>
                                
                            </div>

                            <!-- Check Status -->
                            <div class="p-2">
                                <div v-if="article.status == 1" class="circle-status border border-success rounded-circle"></div>
                                <div v-if="article.status == 2" class="circle-status border border-info rounded-circle"></div>
                                <div v-if="article.status == 3" class="circle-status border border-warning rounded-circle"></div>
                            </div>
                        </div>
   
                    </div>
                    <!-- Call name -->
                    <h3>{{article.name}}</h3>
                    <div class="mt-2 text-black-50">
                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-heart-fill" viewBox="0 0 16 16">
                        <path fill-rule="evenodd" d="M8 1.314C12.438-3.248 23.534 4.735 8 15-7.534 4.736 3.562-3.248 8 1.314z"/>
                        </svg>
                        <p class="d-inline p-1"> 78 | 5 comment</p>
                        
                    </div>
                    <div class="mt-5">
                        <div class="row">
                            <div class="col-2">
                                <img src="~/assets/images/user.png" class="img-user w-100" alt="Cinque Terre">
                            </div>
                            <div class="col-10">
                                <div class="d-flex justify-content-between">
                                    <div>
                                        <!-- Call author -->
                                        <p class="m-0 p-0">{{article.author.name}} </p>
                                        <small class="text-black-50">{{$moment(article.created_at).fromNow()}}</small>
                                    </div>
                                    <div v-if="article.author.id == 1" class="d-flex align-items-end flex-column">
                                            <svg @click="deleteArticle" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-trash mt-auto text-black-50" viewBox="0 0 16 16">
                                                <path d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6z"/>
                                                <path fill-rule="evenodd" d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1zM4.118 4 4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118zM2.5 3V2h11v1h-11z"/>
                                            </svg>
                                    </div>
                                </div>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
 export default {
    props: {
        article: Object
    },
    data() {
      return {
        boxOne: '',
        boxTwo: ''
      }
    },
    methods: {
      deleteArticle() {
        this.boxTwo = ''
        this.$bvModal.msgBoxConfirm('Please confirm that you want to delete this aticle.', {
          title: 'Please Confirm',
          size: 'sm',
          buttonSize: 'sm',
          okVariant: 'danger',
          okTitle: 'YES',
          cancelTitle: 'NO',
          footerClass: 'p-2',
          hideHeaderClose: false,
          centered: true
        })
        .then(value => {
            this.boxTwo = value
        })
        // eslint-disable-next-line node/handle-callback-err
        .catch(err => {
            // An error occurred
        })
      }
    },
  }
</script>
<style scoped>
.img-user{
  border-radius: 50%;
}
.circle-status{
    width: 1rem;
    height: 1rem;
    border-width: 0.2rem !important;
}
</style>