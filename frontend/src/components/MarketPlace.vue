<template>
<div>
    <div>
      <div style="left:13.15%">
        <el-image style="width: 73.7%; ; margin-top:2%; " :src="title" ></el-image>
      </div>
      <div v-for="item in nft" :key="item.id">
        <el-row style="margin-top:1.4%" >
            <el-col :span="4" style="margin-left:15.55%;height:15.19%;width:16.21%">
                <router-link :to="{path:'/detail',query: {id: item.id[0], uri: item.uri[0]}}">
                  <el-card style="border-radius:20px;">
                    <el-image style=" border-radius:30px;" 
                    :style="'height:'+myHeight+'px;width:'+myWidth+'px;'"
                    :src="item.url[0]"
                    :fit='cover'
                     >
                    </el-image>
                    <div style="text-align:left;margin-top:10px">
                        <b style="font-size:16px">{{ item.name[0] }}</b>
                        <el-row>
                          <el-col :span="12">
                            <p style="font-size:14px"><b>{{ item.sale_price[0] }} </b> CFX <b style="font-size:10px">Sale Price</b></p>
                          </el-col>
                          <el-col :span="12">
                            <p style="font-size:14px"><b>{{ item.pawn_price[0] }} </b> CFX <b style="font-size:10px">Pawn Price</b></p>
                          </el-col>
                        </el-row>
                    </div>
                  </el-card>
                </router-link>
            </el-col>
            <el-col :span="4" style="margin-left:1.39%;width:16.21%"  v-if="item.id[1] !== undefined">
                <router-link :to="{path:'/detail',query: {id: item.id[1], uri: item.uri[1]}}">
                  <el-card style="border-radius:20px;">
                  <el-image style=" border-radius:30px;" 
                    :style="'height:'+myHeight+'px;width:'+myWidth+'px;'"
                    :src="item.url[1]"
                    :fit='cover'
                    >
                    </el-image>
                    <div style="text-align:left;margin-top:10px">
                        <b style="font-size:16px">{{ item.name[1] }}</b>
                        <el-row>
                          <el-col :span="12">
                            <p style="font-size:14px"><b>{{ item.sale_price[1] }} </b> CFX <b style="font-size:10px">Sale Price</b></p>
                          </el-col>
                          <el-col :span="12">
                            <p style="font-size:14px"><b>{{ item.pawn_price[1] }} </b> CFX <b style="font-size:10px">Pawn Price</b></p>
                          </el-col>
                        </el-row>
                    </div>
                  </el-card>
                </router-link>
            </el-col>
            <el-col :span="4" style="margin-left:1.39%;width:16.21%"  v-if="item.id[2] !== undefined">
                <router-link :to="{path:'/detail',query: {id: item.id[2], uri: item.uri[2]}}">
                  <el-card style="border-radius:20px;">
                  <el-image style=" border-radius:30px;" 
                    :style="'height:'+myHeight+'px;width:'+myWidth+'px;'"
                    :src="item.url[2]"
                    :fit='cover'
                    >
                    </el-image>
                    <div style="text-align:left;margin-top:10px">
                        <b style="font-size:16px">{{ item.name[2] }}</b>
                        <el-row>
                          <el-col :span="12">
                            <p style="font-size:14px"><b>{{ item.sale_price[2] }} </b> CFX <b style="font-size:10px">Sale Price</b></p>
                          </el-col>
                          <el-col :span="12">
                            <p style="font-size:14px"><b>{{ item.pawn_price[2] }} </b> CFX <b style="font-size:10px">Pawn Price</b></p>
                          </el-col>
                        </el-row>
                    </div>
                  </el-card>
                </router-link>
            </el-col>
            <el-col :span="4" style="margin-left:1.39%;width:16.21%"  v-if="item.id[3] !== undefined">
                <router-link :to="{path:'/detail',query: {id: item.id[3], uri: item.uri[3]}}">
                  <el-card style="border-radius:20px;">
                  <el-image style=" border-radius:30px;" 
                    :style="'height:'+myHeight+'px;width:'+myWidth+'px;'"
                    :src="item.url[3]"
                    :fit='cover'
                    >
                    </el-image>
                    <div style="text-align:left;margin-top:10px">
                        <b style="font-size:16px">{{ item.name[3] }}</b>
                        <el-row>
                          <el-col :span="12">
                            <p style="font-size:14px"><b>{{ item.sale_price[3] }} </b> CFX <b style="font-size:10px">Sale Price</b></p>
                          </el-col>
                          <el-col :span="12">
                            <p style="font-size:14px"><b>{{ item.pawn_price[3] }} </b> CFX <b style="font-size:10px">Pawn Price</b></p>
                          </el-col>
                        </el-row>
                    </div>
                  </el-card>
                </router-link>                
            </el-col>

        </el-row>
      </div>
    </div>
</div>
</template>

<script>
import Header from '@/components/Header'
export default {
    
    props: ['account'],
    
    data() {
      return {
        
        myWidth: document.documentElement.clientWidth * 0.14,
        myHeight: document.documentElement.clientHeight * 0.25,

        url:'https://d3vi7ke2kcvale.cloudfront.net/images/bsc/0xe3748766528f93887503dbb527f0965614d72e61/f4b6ceef17ba9360d61d2d1fb40a04c2.png',
        currentDate:'2021-08-12',
        cover: 'cover',
        account: '',
        title: require("../assets/marketplace_bg.png"),
        nft:[],
        json_url: '',
        temp_name: '',

      }

    },
    components:{
        'v-header':Header
    },
    methods: {
      get_bodySize () {//动态获取浏览器高度 宽度
				const _this = this;
				window.onresize = () => {
        return (() => {
          _this.clientHeight = document.documentElement.clientHeight;
          _this.myHeight = _this.clientHeight * 0.25;
          _this.clientWidth = document.documentElement.clientWidth;
          _this.myWidth = this.clientWidth * 0.14;
          console.log("width" + window.screenWidth);
        })();
        };
			},
      init () {
        this.account = this.$refs.account;
        console.log(this.account);
      },
      async getUrl(tokenId){
        let _this = this; 
        await this.getJsonUrl(tokenId);        
      },
      async getJsonUrl(tokenId) {
        const {Conflux, util} = require('js-conflux-sdk');
        const {abi,bytecode} = require('../../sol/MathArt.json');
        // mathArt v2.0合约地址
        const {MathArtAddress} = require('../../sol/config.json');
        let cfx = new Conflux({
            url: 'https://test.confluxrpc.com',
            networkId: 1,
        });
        cfx.provider = conflux;
        let _this = this;
        const contract = cfx.Contract({ abi, address:MathArtAddress,bytecode:bytecode});
        var url = await contract.tokenURI(tokenId);
        _this.json_url = url;
      },
      async getName(itemUrl){
        let _this = this;
        await this.$http.request({
          url:_this.$url + 'download/' + itemUrl,
          method:'get',
        }).then(response => {
          var responseData = response.data;
          _this.temp_name = responseData.nft_name;
        }).catch(function (e) {
          console.log(e);
        });
      }
      
    },
    watch: {
    },
    mounted:function () {      
      this.nft = [];
      this.get_bodySize();

      this.init();

      let _this = this;
      const {Conflux, util, Contract, Drip} = require('js-conflux-sdk');
      const {abi, bytecode} = require('../../sol/NFiTMarket.json');
      const {NFiTMarketAddress} = require('../../sol/config.json');
      async function main() {
        const cfx = new Conflux({
          url: 'https://test.confluxrpc.org',
          defaultGasPrice: 100,
          defaultGas: 1000000,
        });
        cfx.provider = conflux;
        const contract = cfx.Contract(
            {
              abi: abi,
              address: NFiTMarketAddress,
              bytecode: bytecode
            }
        );
        let publishNFT = await contract.getPublishedNFT();
        var nfts = [];
        let item = {
          ID:'', name:'', sell_price:'', loan_price:'', url:'', uri:''
        };

        for(var i = 0; i < publishNFT.length; i++)
        {
          item = {
            ID:'', name:'', sell_price:'', loan_price:'', url:'', uri:''
          };
          if(publishNFT[i][0] == undefined) continue;
          console.log(publishNFT[i]);
          let itemId = publishNFT[i][0];
          let itemInfo = await contract.getItemInfo(itemId);
          let tokenId = itemInfo[2][0];
          console.log(tokenId);
          await _this.getUrl(tokenId);
          let itemUrl = _this.json_url;
          item.uri = itemUrl;
          let url = _this.$url + 'download/' + itemUrl.substr(0, itemUrl.length - 5);

          item.ID = itemId;
          await _this.getName(itemUrl);
          item.name = _this.temp_name;
          item.url = url;

          item.sell_price = new Drip(itemInfo[6].toString()).toCFX();
          item.loan_price = new Drip(itemInfo[7].toString()).toCFX();
          console.log(item);
          nfts.push(item);
        }

        var temp_map = {id:[], name:[], sale_price:[], pawn_price:[], url:[], uri:[]};
        var count = 0;
        
        for(let i = 0; i < nfts.length; i++) {
          temp_map['id'].push(nfts[i].ID);
          temp_map['name'].push(nfts[i].name);
          temp_map['sale_price'].push(nfts[i].sell_price);
          temp_map['pawn_price'].push(nfts[i].loan_price);
          temp_map['url'].push(nfts[i].url);
          temp_map['uri'].push(nfts[i].uri);
          count++;
          if(count == 4){
            _this.nft.push(temp_map);
            temp_map = {id:[], name:[], sale_price:[], pawn_price:[], url:[], uri:[]};
            count = 0;
          }
        }
        if(temp_map['id'].length > 0)
          _this.nft.push(temp_map);

        // let itemId ="6";
        // let itemInfo = await contract.getItemInfo(itemId);
        // console.log(itemInfo);
        // // 具体可以参考智能合约 17到30行
        // // https://github.com/aurorabit/NFiT-core/blob/main/contracts/NFiTMarket.sol
        // console.log("具体的内容");
        // console.log("第一项是itemId");
        // console.log(itemInfo[0][0]);
        // console.log("第二项是nftContract");
        // console.log(itemInfo[1]);
        // console.log("第三项是tokenId");
        // console.log(itemInfo[2][0]);
        // console.log("第四项是creator");
        // console.log(itemInfo[3]);
        // console.log('第五项是pawnor');
        // console.log(itemInfo[4]);
        // console.log('第六项是owner');
        // console.log(itemInfo[5]);
        // console.log('第七项目是sellPrice');
        // console.log(itemInfo[6]);
        // console.log('第八项是loanPrice')
        // console.log(itemInfo[7])
        // console.log('第九项是redeemPrice')
        // console.log(itemInfo[8])
        // console.log('第十项是royality')
        // console.log(itemInfo[9])
        // console.log('第11项是deadline')
        // console.log(itemInfo[10])
        // console.log('第12项是state')
        // console.log(itemInfo[11])

        // let timestamp = itemInfo[10][0];
        // var time = new Date(timestamp * 1000);
        // var year = time.getFullYear(); //getFullYear方法以四位数字返回年份
        // var month = time.getMonth() + 1; // getMonth方法从 Date 对象返回月份 (0 ~ 11)，返回结果需要手动加一
        // var date = time.getDate(); // getDate方法从 Date 对象返回一个月中的某一天 (1 ~ 31)
        // var hours = time.getHours(); // getHours方法返回 Date 对象的小时 (0 ~ 23)
        // var minutes = time.getMinutes(); // getMinutes方法返回 Date 对象的分钟 (0 ~ 59)
        // var seconds = time.getSeconds(); // getSeconds方法返回 Date 对象的秒数 (0 ~ 59)
        // let resStr = year + '-' + month + '-' + date + ' ' + hours + ':' + minutes + ':' + seconds;
        // console.log(resStr);

      }
      main().catch(e => console.error(e));
      }

}
</script>

<style scoped>
a{ text-decoration:none}
a:hover{ text-decoration:none}
.tot{
    height:100%;
}
.main-con{
  /* height:600px; */
  width:80%;
  margin:0 auto;
}
/* Container布局容器 */
  .el-footer {
    background-color: #66CDAA;
    color: #fff;
    text-align: left;
    line-height: 60px;
    /* vertical-align: middle;  */
  }

  .el-aside {
    /* background-color: #D3DCE6; */
    color: #333;
    text-align: center;
    line-height: auto;
    margin-left: 30px;
    margin-right: 30px;
  }

  .el-main {
    /* background-color: #E9EEF3; */
    color: #333;
    text-align: left;
    line-height: auto;
    margin-left: 20px;
  }

  /* .bitmap { */
    /* background: url("../assets/marketplace_bg.png"); */
    /* border-radius: 20px; */
    /* width: 1059.03px; */
    /* height: 400px; */
    
    /* position: relative; */
    /* left: 13.15%; */
    /* right: 13.15%; */
    /* top: 16.36%; */
    /* bottom: 76.1%; */  
  /* } */

  .nft-image {
    width: 100%;
    height: 100%;
  }

  .nft-card {
    /* position: absolute; */
    /* width: 16.21%; */
    /* height: 15.19%; */
  }
</style>
