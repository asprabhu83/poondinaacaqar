<template>
  <div>

      <div class="list">
          <div class="item" v-for="item in datas.data" :key="item.id" >
              <div v-if="$route.params.id == item.route_name">
                  <div class="heading">
                      <div class="breadcrumbs"><span> <router-link :to="item.link" > Home </router-link><i class="fas fa-chevron-right" ></i> <router-link class="crnt_page" :to="item.link">{{item.name}}</router-link></span></div>
                      {{item.name}}
                  </div>
                  <div class="sub_items">
                      <div  v-for="category in item.category" :key="category.id">
                         <router-link class="i_list" :to="category.link" v-if="category.path !== 'pdf'"> <img class="send_icon" src="@/assets/send.svg" alt=""> {{category.name}}</router-link> 
                         <a class="i_list" v-if="category.path == 'pdf'" :href="$store.state.siteUrl + category.link" target="_blank" > <img class="send_icon" src="@/assets/send.svg" alt=""> {{category.name}}</a> 
                      </div>
                  </div>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return{
            datas:[]
        }
    },
    mounted(){
        this.GetData()
    },
    methods:{
        GetData(){
            axios.get(this.$store.state.baseUrl + 'datas.json').then((r)=>{
                this.datas = r.data
            }).catch((e)=>{
                console.log(e)
            })
        }
    }
}
</script>

