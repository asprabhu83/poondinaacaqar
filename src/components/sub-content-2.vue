<template>
  <div>
      <div class="list">
          <div class="item" v-for="item in datas.data" :key="item.id" >
              <div v-for="category in item.category" :key="category.id">
                  <div  v-for="cat in category.category" :key="cat.id">
                      <div  v-if="$route.params.id == item.route_name && $route.params.subid == category.path && $route.params.cntid == cat.path" >
                            <div class="heading description"  >
                                <div class="breadcrumbs"><span><router-link :to="item.link"> Home</router-link> <i class="fas fa-chevron-right" ></i> <router-link :to="item.link">{{item.name}}</router-link>  <i class="fas fa-chevron-right" ></i><router-link :to="category.link">{{category.name}}</router-link>  <i class="fas fa-chevron-right" ></i><router-link class="crnt_page" :to="cat.link">{{cat.name}}</router-link> </span></div>
                                <span class="alter_heading" >{{cat.alter_name}}</span> <button type="button" class="back_btn" @click="this.$router.go(-1)"><i class="fas fa-chevron-left" ></i> Back</button>
                            </div> 
                            <div class="sub_items">
                                <div v-for="cnt in cat.sub" :key="cnt.id" >
                                    <a class="i_list" v-if="cnt.pdf == 'yes'" :href="cnt.id == 4 ? cnt.link : $store.state.siteUrl + cnt.link" target="_blank" >
                                        <img class="send_icon" src="@/assets/send.svg" alt=""> {{cnt.name}}
                                    </a>
                                    <router-link v-if="cnt.pdf == 'no'" class="i_list" :to="cnt.link" >
                                        <img class="send_icon" src="@/assets/send.svg" alt="">{{cnt.name}} 
                                    </router-link>
                                </div>
                                <div class="table_contents courses" style="overflow-x:auto;" v-if="cat.path == '1.3.4'">
                                    <table>
                                        <thead>
                                            <tr>
                                                <th></th>
                                                <th>I UG</th>
                                                <th>II UG</th>
                                                <th>III UG</th>
                                                <th>I PG</th>
                                                <th>II PG</th>
                                           
                                            </tr>
                                        </thead>
                                        <tbody>
                                            <tr v-for="item in tables.t_1_3_4" :key="item.id">
                                                <td style="width:20%;">{{item.name}}</td>
                                                <td class="pdf_items" ><a :href="$store.state.siteUrl + item.Iug" v-if="item.Iug !== ''"  target="_blank" ><img src="../assets/pdf_icon2.png" style="width:20px;" /></a> <span v-else> - </span> </td>
                                                <td class="pdf_items"> <a :href="$store.state.siteUrl + item.IIug" v-if="item.IIug !== ''"  target="_blank" ><img src="../assets/pdf_icon2.png" style="width:20px;" /></a> <span v-else> - </span> </td>
                                                <td class="pdf_items"> <a :href="$store.state.siteUrl + item.IIIug" v-if="item.IIIug !== ''"  target="_blank" ><img src="../assets/pdf_icon2.png" style="width:20px;" /></a> <span v-else> - </span> </td>
                                                <td class="pdf_items"> <a :href="$store.state.siteUrl + item.Ipg" v-if="item.Ipg !== ''"  target="_blank" ><img src="../assets/pdf_icon2.png" style="width:20px;" /></a> <span v-else> - </span> </td>
                                                <td class="pdf_items"> <a :href="$store.state.siteUrl + item.IIpg" v-if="item.IIpg !== ''"  target="_blank" ><img src="../assets/pdf_icon2.png" style="width:20px;" /></a> <span v-else> - </span> </td>
                                            </tr>
                                        </tbody>
                                    </table>
                                </div>
                                <div class="year_category" v-if="cat.path == '3.4.4'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">Books and chapters Published</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.t_3_4_4" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '6.3.4'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">Teachers Attended Professional Development Programmes</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.t_6_3_4" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '3.2.1'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">Project Grants Recieved</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.t_3_2_1" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '5.2.1'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">Placement of outgoing students</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.t_5_2_1" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category ssd" v-if="cat.path == '5.1.3'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt=""> Soft Skill Development</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.i_5_1_3" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category ssd" v-if="cat.path == '5.1.3'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt=""> Language and Communication Skills (UG course)</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.iiug_5_1_3" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category ssd" v-if="cat.path == '5.1.3'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt=""> Language and Communication Skills (PG course)</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.iipg_5_1_3" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '5.1.3'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt=""> Awareness of Trends and Technology</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.iii_5_1_3" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '6.3.3'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt=""> Professional Development Programmes</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.t_6_3_3" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category ssd" v-if="cat.path == '7.1.6'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt=""> Energy Audit</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.tI_7_1_6" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category ssd" v-if="cat.path == '7.1.6'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt=""> Environment Audit</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.tII_7_1_6" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category ssd" v-if="cat.path == '7.1.6'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt=""> Green Audit</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.tIII_7_1_6" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category2" v-if="cat.path == '5.1.4'">
                                    <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">2015-2016</div>
                                    <div class="year_items2">
                                        <a v-for="item in tables.one_5_1_4" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                    </div>
                                </div>
                                <div class="year_category2" v-if="cat.path == '4.1.3'">
                                    <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">ICT Class Rooms</div>
                                    <div class="year_items2">
                                        <a v-for="item in tables.t_4_1_3" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                    </div>
                                </div>
                                <div class="year_category2" v-if="cat.path == '4.1.3'">
                                    <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">ICT Seminar Halls</div>
                                    <div class="year_items2">
                                        <a v-for="item in tables.t2_4_1_3" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                    </div>
                                </div>
                                <div class="year_category2" v-if="cat.path == '2.3.4'">
                                    <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">Teaching plan</div>
                                    <div class="year_items2">
                                        <a v-for="item in tables.t_2_3_4" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                    </div>
                                </div>
                                <div class="year_category2" v-if="cat.path == '5.1.4'">
                                    <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">2016-2017</div>
                                    <div class="year_items2">
                                        <a v-for="item in tables.two_5_1_4" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                    </div>
                                </div>
                                <div class="year_category2" v-if="cat.path == '5.1.4'">
                                    <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">2017-2018</div>
                                    <div class="year_items2">
                                        <a v-for="item in tables.three_5_1_4" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                    </div>
                                </div>
                                <div class="year_category2" v-if="cat.path == '5.1.4'">
                                    <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">2018-2019</div>
                                    <div class="year_items2">
                                        <a v-for="item in tables.four_5_1_4" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                    </div>
                                </div>
                                <div class="year_category2" v-if="cat.path == '5.1.4'">
                                    <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">2019-2020</div>
                                    <div class="year_items2">
                                        <a v-for="item in tables.five_5_1_4" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                    </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '1.3.3'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt=""> List of Students Enrolled in Value Added Courses</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.t_1_3_3" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '1.3.3'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">Value Added Courses attendance and results</div>
                                        <div class="year_items">
                                            <router-link v-for="item in tables.main_1_3_3" :key="item.id" :to="item.link">{{item.name}}</router-link>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '7.1.11'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt=""> National/international commemorative days/events and festivals</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.t_7_1_11" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '3.1.2'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">Policy documents for Sanction of seed money</div>
                                        <div class="year_items">
                                            <router-link v-for="item in tables.main_3_1_2" :key="item.id" :to="item.link">{{item.name}}</router-link>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '3.7.1'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">Collaborative activities</div>
                                        <div class="year_items">
                                            <router-link v-for="item in tables.main_3_7_1" :key="item.id" :to="item.link">{{item.name}}</router-link>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '3.7.2'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">Functional MoUs</div>
                                        <div class="year_items">
                                            <router-link v-for="item in tables.main_3_7_2" :key="item.id" :to="item.link">{{item.name}}</router-link>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '3.3.2'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">Workshop/seminars on RM,IPR and etc.</div>
                                        <div class="year_items">
                                            <router-link v-for="item in tables.main_3_3_2" :key="item.id" :to="item.link">{{item.name}}</router-link>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '5.1.1'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">Scholarship and freeship-govt.</div>
                                        <div class="year_items">
                                            <router-link v-for="item in tables.main_5_1_1" :key="item.id" :to="item.link">{{item.name}}</router-link>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '1.1.3'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">Courses focus on employability</div>
                                        <div class="year_items">
                                            <router-link v-for="item in tables.main_1_1_3" :key="item.id" :to="item.link">{{item.name}}</router-link>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '3.6.2'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt=""> Awards and Recognition recieved for extension activities</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.t_3_6_2" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category2" v-if="cat.path == '5.3.3'">
                                    <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">2015-2016</div>
                                    <div class="year_items2">
                                        <a v-for="item in tables.one_5_3_3" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                    </div>
                                </div>
                                <div class="year_category2" v-if="cat.path == '5.3.3'">
                                    <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">2016-2017</div>
                                    <div class="year_items2">
                                        <a v-for="item in tables.two_5_3_3" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                    </div>
                                </div>
                                <div class="year_category2" v-if="cat.path == '5.3.3'">
                                    <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">2017-2018</div>
                                    <div class="year_items2">
                                        <a v-for="item in tables.three_5_3_3" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                    </div>
                                </div>
                                <div class="year_category2" v-if="cat.path == '5.3.3'">
                                    <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">2018-2019</div>
                                    <div class="year_items2">
                                        <a v-for="item in tables.four_5_3_3" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                    </div>
                                </div>
                                <div class="year_category2" v-if="cat.path == '5.3.3'">
                                    <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">2019-2020</div>
                                    <div class="year_items2">
                                        <a v-for="item in tables.five_5_3_3" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                    </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '4.2.2'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">Membership of e-journals</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.t_4_2_2" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
                                        </div>
                                </div>
                                <div class="year_category" v-if="cat.path == '4.2.3'" >
                                        <div class="year_head"><img class="send_icon" src="@/assets/send.svg" alt="">Expenditure for purchase of books and journals</div>
                                        <div class="year_items">
                                            <a v-for="item in tables.t_4_2_3" :key="item.id" :href="$store.state.siteUrl + item.link" target="_blank">{{item.name}}</a>
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
import axios from 'axios'
export default {
    data(){
        return{
            datas:[],
            tables:[]
        }
    },
    mounted(){
        this.GetData()
        this.GetTables()
    },
    methods:{
        GetData(){
            axios.get(this.$store.state.baseUrl + 'datas.json').then((r)=>{
                this.datas=r.data
            }).catch((e)=>{
                console.log(e)
            })
        },
        GetTables(){
            axios.get(this.$store.state.baseUrl + 'tables.json').then((r)=>{
                this.tables=r.data
            }).catch((e)=>{
                console.log(e)
            })
        }
    }
}
</script>

