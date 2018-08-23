<template>
    <div class='box'>
       <div class="auto">
           <div class="top">
                <ul class="top_auto">
                    <li></li>
                    <li></li>
                    <li></li>
                    <li></li>
                </ul>
           </div>
           <div class='bottom'>
               <div class="left">
                   <p>公告</p><br/>
                   <a v-for='i in notice' :href="i.href" :key='i.id'>{{i.txt}}</a>
               </div>
               <div class="right">
                   <ul v-for='i in server' :key='i.id'>
                       <p>{{i.title}}</p>
                       <li v-for='k in i.contxt' :key='k.id'><a href="">{{k.txt}}</a></li>
                   </ul>
               </div>
           </div>
       </div>
    </div>
</template>
<script>
export default {
    name:'Qtzz',
    data(){
        return {
            notice:[//关于公告的数组，先做一个假数据，之后要从后台动态获取
                {id:1,txt:'【公告】有关中华古钱通鉴商品价格异常事宜',href:''},
                {id:2,txt:'【公告】 央广购物推“超级服务中心”五大服务全新升级',href:''},
                {id:3,txt:'【公告】有关对购买资中塔罗科血橙商品的用户赠送歉意礼金券事宜',href:''},
                {id:4,txt:'【公告】书籍开启梦想 爱心孕育希望',href:''}
            ],
            server:[//右侧有关服务得数据，这些是死数据，可以直接写死
                {id:1,title:'购物指南',contxt:[
                                                {id:11,txt:'免费注册',href:''},
                                                {id:12,txt:'购物流程',href:''},
                                                {id:13,txt:'用户注册协议',href:''},
                                                {id:14,txt:'电子发票',href:''}
                                            ]},
                {id:2,title:'商家服务',contxt:[
                                                {id:21,txt:'招商标准',href:''},
                                                {id:22,txt:'平台总则',href:''},
                                                {id:23,txt:'入驻注意事项',href:''},
                                                {id:24,txt:'招商资质标准',href:''}
                                            ]},
                {id:3,title:'支付配送',contxt:[
                                                {id:31,txt:'支付方式',href:''},
                                                {id:32,txt:'配送范围',href:''},
                                                {id:33,txt:'配送时间',href:''},
                                                {id:34,txt:'购物卡',href:''}
                                            ]},
                {id:4,title:'会员中心',contxt:[
                                                {id:41,txt:'会员等级',href:''},
                                                {id:42,txt:'会员权益',href:''},
                                                {id:43,txt:'购物金',href:''},
                                                {id:44,txt:'找回密码',href:''}
                                            ]},
                {id:5,title:'售后服务',contxt:[
                                                {id:51,txt:'超级服务中心',href:''},
                                                {id:52,txt:'售后服务政策',href:''},
                                                {id:53,txt:'无忧购物',href:''},
                                                {id:54,txt:'权威监督',href:''}
                                            ]}
            ]
        }
    },
    methods:{
        ceilImg(id){
            if(id === 1){
                alert('第一个li');
            }else if(id===2){
                alert('第二个li');
            }
        }
    }
} 
</script>
<style lang='scss' scoped>
.box{
    width:100%;
    height:271px;
    background:#fff;
    .auto{
        width:1210px;
        height:100%;
        margin:0 auto;
        .top{
            width:1210px;
            height:86px;
            background:#fff;
            border-bottom:1px solid #e3e3e3;
            .top_auto{
                width:1000px;
                height:86px;
                margin:0 auto;
                >li{
                    float:left;
                    width:250px;
                    height:86px;
                    background:#fff url('../../assets/ceil/cti.png');
                }
                >li:nth-child(2){
                    background-position-x: -250px;
                }
                >li:nth-child(3){
                    background-position-x: -500px;
                }
                >li:nth-child(4){
                    background-position-x: -750px;
                }
            }
        }
        .bottom{
            width:100%;
            height:184px;
            div{
                float: left;
                margin-top:25px;
            }
            .left{
                width:329px;
                height:134px;
                border-right:1px solid #eaeaea;
                p{
                    width:35px;
                    height:20px;
                    text-align: center;
                    line-height:20px;
                    font-size:16px;
                    display: inline-block;
                    margin-left:47px;
                    margin-bottom:10px;
                    color:#000;
                    font-family:'宋体'; 
                }
                a{
                    color:#999;
                    font-family:'宋体'; 
                    width:241px;
                    overflow: hidden;
                    margin-top:8px;
                    text-overflow: ellipsis;
                    white-space: nowrap;
                    display: inline-block;
                    margin-left:40px;
                }
            }
            .right{
                width:880px;
                height:134px;
                ul{
                    width:102px;
                    height:134px;
                    float: left;
                    margin-left:63px;
                    p{
                        height:20px;
                        text-align: center;
                        line-height:20px;
                        font-size:16px;
                        display: inline-block;
                        margin-bottom:10px;
                        color:#000;
                        font-family:'宋体'; 
                    }
                    li{
                        width:241px;
                        overflow: hidden;
                        margin-top:8px;
                        text-overflow: ellipsis;
                        white-space: nowrap;
                        a{
                            color:#999;
                            font-family:'宋体'; 
                        }
                    }
                }
            }
        }
    }
}
</style>

