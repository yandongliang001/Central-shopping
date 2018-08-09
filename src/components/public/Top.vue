<template>
    <div class="box">
        <div class="top_nav_box">
            <div class="top_nav">
                <ul class="nav_left">
                    <li v-for='i in navArr' :key='i.id' @mouseover="i.show = true" @mouseout="i.show = false" :class='i.id<=(navArr.length-1)?"active":""'>
                        <i v-show='!i.childShow'></i>
                        <a :href='i.href' :class='i.claName'>{{i.content}}</a>
                        <span v-show='i.childShow'></span>
                        <transition name='fade' enter-active-class='animated fadeInDown'>
                            <ul v-show='i.show' :class='i.claName'>
                                <li v-for='k in i.son' :key='k.id'>
                                    <a :href="k.href">{{k.content}}</a>
                                </li>
                            </ul>
                        </transition>
                    </li>
                </ul>
                <ul class="nav_right">
                    <li v-for="key in logginArr" :key='key.id' :class='key.classNane'>
                        <a :href="key.href">{{key.content}}</a>
                    </li>
                </ul>
            </div>
        </div>
        <div class="bottom_box">
            <div class="bottom_auto">
                <div class="bom_box_left">
                    <img src="https://pic1.cnrmall.com/image/df/e5/dfe5c0db500c119e8d570142f184ee2d.png" alt="央广购物官方网站" title="央广购物官方网站"/>
                    <ul class='bolt_nav'>
                        <li v-for='i in bomBoxArr' :class='i.className' :key='i.id'>
                            <a :href="i.href">{{i.content}}</a>
                        </li>
                    </ul>
                </div>
                <div class="bom_box_center">
                    <div class="search_box">
                        <ul class='search_slid'>
                            <li><a href="#">宝贝</a><span></span></li>
                            <li><a href="#">店铺</a></li>
                        </ul>
                        <input type="text" class='search_txt search' placeholder="请输入您要搜索的商品关键字"/>
                        <input type="submit" class='search_btn search' value='搜索'/>
                    </div>
                    <ul class="search_nav">
                        <li v-for='k in searchArr' :key='k.id'><a href="">{{k.content}}</a></li>
                    </ul>
                </div>
                <div class="bom_box_right">
                    <div class="my_shop _my">
                        <div class="ctn">
                            <span></span>
                            <a href="#">我的商城</a>
                            <i></i>
                        </div>
                        <div class='content'>
                            <div class="my_box">
                                <img src="../../assets/denglu.png" alt=""/>
                                <a v-show='!myLogin' href="#">您好，请登录</a>
                                <ul v-show='myLogin' class='my_zt'>
                                    <li><span>{{myLoginObj.name}}</span><i>注册会员</i></li>
                                    <li>上次登录：{{myLoginObj.time}}</li>
                                </ul>
                            </div>
                            <ul v-for='i in myNavArr' :class='i.className' :key='i.id'>
                                <li v-for='k in i.txt' :key='k.id'>
                                    <a href="#">{{k.content}}</a>
                                </li> 
                            </ul>
                        </div>
                    </div>
                    <div class="goshop _my">
                        <div class="ctn">
                            <span></span>
                            <a href="#">购物车结算</a>
                            <i></i>
                        </div>
                        <div class="content">
                            <div class="title">最新加入的商品</div>
                            <div v-show='!myShop' class='none_data'>您的购物车中暂无数据，赶快选择心爱的商品吧！</div>
                            <div v-show='myShop' class='data'>
                                <ul class='myShopList'>
                                    <li v-for='key in myShopLis' :key='key.nub'>
                                        <a href='#' class="left">
                                            <img :src="key.url" alt=""/>
                                            <p>{{key.name}}</p>
                                        </a>
                                        <div class="right">
                                            <div class='price'>{{key.price}}×{{key.nub }}</div>
                                            <a href="javascript:;">删除</a>
                                        </div>
                                    </li>
                                </ul>
                                <div class="jiesuan">
                                    <p>共 <span> {{myShopLis.length}} </span> 中商品 总计金额：<i>¥{{shopListNum}}</i></p>
                                    <a href="#">结算购物车中的商品</a>
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
    name:"Top",
    data(){
        return {
            navArr:[
                {
                    id:1,
                    content:'我的订单',
                    claName:'_box',
                    href:'',
                    childShow:true,
                    show:false,
                    son:[
                        {id:11,content:'待付款订单',href:'#'},
                        {id:12,content:'待确认收货',href:'#'},
                        {id:13,content:'待评价交易',href:'#'}
                    ]
                },{
                    id:2,
                    content:'我的收藏',
                    claName:'_box',
                    href:'',
                    childShow:true,
                    show:false,
                    son:[
                        {id:21,content:'商品收藏',href:'#'},
                        {id:22,content:'店铺收藏',href:'#'}
                    ]
                },{
                    id:3,
                    content:'客户服务',
                    claName:'_box',
                    href:'',
                    childShow:true,
                    show:false,
                    son:[
                        {id:31,content:'购物指南',href:'#'},
                        {id:32,content:'售后服务',href:'#'},
                        {id:33,content:'商家服务',href:'#'}
                    ]
                },{
                    id:4,
                    content:'成为供应商',
                    claName:'gys',
                    href:'',
                    show:true,
                    childShow:false,
                }
            ],
            logginArr:[
                {id:1,content:'您好，请登陆',classNane:'',href:'#'},
                {id:2,content:'免费注册',classNane:'login',href:'#'}
            ],
            bomBoxArr:[
                {id:1,content:'所有商品分类',className:'category',href:'#'},
                {id:2,content:'首页',className:'index',href:'#'},
                {id:3,content:'TV直播',className:'live',href:'#'},
            ],
            searchArr:[
                {id:1,content:'中宁头茬红枸杞'},
                {id:2,content:'攀枝花凯特芒'},
                {id:3,content:'海阳网纹瓜'},
                {id:4,content:'绿壳土鸡蛋'},
                {id:5,content:'方太'},
                {id:6,content:'李宁'},
                {id:7,content:'GUCCI'},
                {id:8,content:'韩后'}
            ],
            myNavArr:[
                {
                    id:1,className:'my_nav',txt:[
                                                    {id:11,content:'站内消息'},
                                                    {id:12,content:'我的订单'},
                                                    {id:13,content:'咨询回复'}
                                                ]
                },{
                    id:2,className:'my_nav',txt:[
                                                    {id:24,content:'我的收藏'},
                                                    {id:25,content:'我的足迹'},
                                                    {id:26,content:'我的积分'}
                                                ]
                } 
            ],
            myLogin:false, //代表未有用户登录
            myLoginObj:{name:'某某某',time:"2018-08-08 15:12:28"},//当有用户登陆时，更改此条数据即可
            myShop:false,//代表用户购物车中没有商品
            myShopLis:[ //用户购物车中的商品明细  现在是测试数据，之后要把这个数组清空，动态添加用户的真实数据
                {name:'农品堂营养黄金藜麦健康组 货号122867',price:'¥298.00',nub:1,url:""},
                {name:'农品堂营养黄金藜麦健康组 货号122867',price:'¥298.00',nub:2,url:""}
            ]
        }
    },
    computed:{
        shopListNum(){//用来统计用户所有商品的总价格
            var num = 0;
            for(var i in this.myShopLis){
                num += this.myShopLis[i].price.split('¥')[1]*this.myShopLis[i].nub;
            }
            return num.toFixed(2);
        }
    },
    mounted(){
        this.getImgUrl();
        this.getUserName();
    },
    methods:{
        getImgUrl(){//图片在myShopLis里写路径，图片不能正确添加，引入此方法解决,
            for(var k in this.myShopLis){ 
                this.myShopLis[k].url = require('../../assets/list/011/0'+(k+1)+'.jpg');
            }
        },
        getUserName(){//用来获取登陆用户的用户名
            if(this.myLogin){//有用户登陆
                this.logginArr[0].content = this.myLoginObj.name;
            }
        }
    }
}    
</script>
<style lang="scss" scoped>
.box{
    width:100%;
    height:189px;
    background:#fff;
    border-bottom:1px solid #e5e5e5;
    .top_nav_box{
        width:100%;
        height:39px;
        background:#f7f6f5;
        border-bottom:1px solid #e5e5e5;
        .top_nav{
            width:1210px;
            height:100%;
            margin:0 auto;
            // background:#f7f6f5;
            >.nav_left{
                float:right;
                >li{
                    float: left;
                    z-index: 20;
                    line-height:39px;
                    color:#777777;
                }
            }
            >.nav_left{
                >li{
                    padding-right:12px;
                    position:relative;
                    >a{
                        color:#76756f;
                        padding:0 8px 0 12px;
                        border-left:1px solid #e1e1e1;
                    }
                    >span{
                        width:6px;
                        height:3px;
                        top:18px;
                        right:8px;
                        position:absolute;
                        z-index: 20;
                        transform:rotateZ(0deg);
                        transition:0.5s;
                        background: url('../../assets/top_bg.png') 0px 0px;
                    }
                    >ul._box{
                        left:-1px;
                        top:37px;
                        display: none;
                        position: absolute;
                        background:#fff;
                        >li{
                            width:79px;
                            height:30px;
                            line-height:20px;
                            >a{
                                padding-left:12px;
                            }
                        }
                    }
                }
                >li.active:hover{
                    background:#f8f7f6;
                    border:1px solid #d9d7d3;
                    border-bottom:0;
                    padding-right:11px;
                    line-height:37px;
                    >span{
                        top:17px;
                        transform:rotateZ(180deg);
                        transition:0.5s;
                    }
                    >a{
                        color:#f15c18;
                        border:0;
                        padding:0 8px 0 12px;
                    }
                    >ul{
                        color:#76756f;
                        border:1px solid #d9d7d3;
                        display: block;
                        border-top:0;
                        background:#fff;
                        animation-duration: 0.3s;       //动画执行时间
                        animation-delay: 0;            //动画延迟执行时间
                        animation-iteration-count: 1;   //动画执行次数
                        >li:hover{
                            background:#f8f7f6;
                            >a{
                                color:#f15c18;
                            }
                        }
                    }
                }
                >li:last-child{
                   padding:0 12px 0 0;
                   position:relative;
                    >a{
                       padding:0 0 0 42px;
                    }
                    >i{
                        width:20px;
                        height:20px;
                        top:10px;
                        left:12px;
                        background:url('../../assets/on2.png')0 0;
                        position:absolute;
                    }
                }
                >.gys>span{
                    width:20px;
                    height:20px;
                }
            }
            >.nav_right{
                float: right;
                >li{
                     float: left;
                     line-height: 39px;
                     >a{
                        color:#555;
                        padding-right:12px;
                     }
                }
                >.login{
                    >a{
                        color:#ff5b57;
                        padding-right:10px;
                    }
                }
            }
        }
    }
    .bottom_box{
        width:100%;
        height:149px;
        background:#fff;
        border-bottom:1px solid #f15c18;
        .bottom_auto{
            width:1210px;
            height:100%;
            margin:0 auto;  
            >div{
                float:left;
            }
            >.bom_box_left{
                width:365px;
                height:100%;
                >img{
                    float:left;
                    padding:25px 0 16px 7px;
                }
                >.bolt_nav{
                    width:100%;
                    height:40px;
                    float: left;
                    font-size:14px;
                    font-weight: 700;
                    li{
                        float: left;
                        height:100%;
                        line-height:40px;
                    }
                    .category{
                        width:172px;
                        text-align: center;
                        background:#f15c18;
                        >a{
                            color:#fff; 
                        }
                    }
                    .index{
                        padding:0 24px;
                        >a{
                            color:#f15c18;
                        }
                    }
                    .live{
                        padding-left:25px;
                        font-weight: normal;
                        >a{
                            color:#000;
                        }
                        >a:hover{
                            color:#f15c18;
                        }
                    }
                }
            }
            >.bom_box_center{
                width:550px;
                height:100%;
                .search_box{
                    width:546px;
                    height:36px;
                    float:left;
                    margin-top:24px;
                    border:2px solid #f15c18;
                    .search{
                        float:left;
                        height:36px;
                    }
                    input{
                        border:none;
                    }
                    .search_slid{
                        float: left;
                        width:68px;
                        height:36px;
                        line-height: 36px;
                        background:#f8f8f8;
                        li{
                            width:68px;
                            height:36px;
                            background:#f8f8f8;
                            position: relative;
                            border-right:1px solid #cecece;   
                            a{
                                padding-left:15px;
                            }
                            span{
                                width:7px;
                                height:4px;
                                top:16px;
                                left:48px;
                                transform:rotateZ(0deg);
                                transition: 0.3s;
                                background:url('../../assets/top_bg.png')-20px 0px ;
                                position: absolute;
                            }
                        }
                        li:hover{
                            a{
                                color:#f15c18;
                            }
                            span{
                                transform:rotateZ(180deg);
                                transition: 0.3s;
                            }
                        }
                        li:last-child{
                            width:67px;
                            height:36px;
                            display: none;
                            border-left:1px solid #cecece;   
                            border-bottom:1px solid #cecece;   
                        }
                    }
                    .search_slid:hover{
                        li:last-child{
                            display: block;
                        }
                    } 
                    .search_txt{
                        width:365px;
                        height:36px;
                        color:#a4a4a4;
                        background:#fff;
                        padding-left:14px;
                    }
                    .search_btn{
                        width:99px;
                        height:36px;
                        color:#fff;
                        font-weight: 700;
                        background:#f15c18;
                    }
                }
                .search_nav{
                    width:550px;
                    height:33px;
                    float: left;
                    li{
                        float:left;
                        height:33px;
                        line-height:33px;
                        a{
                            color:#999;
                            padding:0 9px;
                            border-left:1px solid #999;
                        }
                    }
                    li:first-child{
                        a{
                             padding:0 9px 0 0;
                            border:none;    
                        }
                    }
                }
            }
            >.bom_box_right{
                width:295px;
                height:100%;
                background:#fff;
                ._my{
                    float:left;
                    height:42px;
                    margin-top:24px;
                    line-height:16px;
                    position: relative;
                    .ctn{
                        width:100%;
                        height:30px;
                        float: left;
                        z-index: 11;
                        position: relative;
                        background:#fff;
                        padding-top:12px;
                        border:1px solid #f0f0f0;
                        span{
                            float: left;
                            width:18px;
                            height:16px;
                            margin:0 9px 0 12px;
                        }
                        a{
                            float: left;
                        }
                        i{
                            float: left;
                            width:4px;
                            height:7px;
                            margin:4px 0 0 9px;
                            background:url('../../assets/top_bg.png') -150px 0; 
                        }
                    }
                    .content{
                        float:left;
                        top:43px;
                        right:-2px;
                        display: none;
                        background:#fff;
                        position: absolute;
                    }
                }
                ._my:hover{
                    .ctn{
                        z-index: 11;
                        position: relative;
                        height:31px;
                        border-bottom:1px solid #fff;
                    }
                    .content{
                        z-index:10;
                        display: block;
                    }
                }
                .my_shop{
                    width:113px;
                    margin: 24px 11px 0 42px;
                    background:#fff;
                    .ctn{
                        span{
                            background:url('../../assets/yangguang.png') -7px -6px;
                        }
                    }
                    .content{
                        width:270px;
                        height:157px;
                        display: none;
                        border:1px solid #f1f0ee;
                        .my_box{
                            width:100%;
                            height:68px;
                            background:#fff;
                            border-bottom:1px dashed #ebeae7;
                            img{
                                float: left;
                                width:48px;
                                height:48px;
                                border-radius:50%;
                                margin:10px 22px 10px 10px;
                            }
                            a{
                                float:left;
                                width:92px;
                                height:28px;
                                margin-top:20px;
                                text-align: center;
                                line-height:28px;
                                border-radius:4px;
                                background:#fff;
                                border:1px solid #f1f0ee;
                            }
                            .my_zt{
                                float:left;
                                margin-top:15px;
                                span{
                                    font-weight: 600;
                                    color:#000;
                                    display: inline-block;
                                    padding-right:8px;
                                }
                                i{
                                    display: inline-block;
                                    background:#ff4d04;
                                    border-radius:3px;
                                }
                            }
                            a:hover{
                                background:#cac8c5;
                            }
                        }
                        .my_nav{
                            float:left;
                            li{
                                padding:8px 58px 0 10px;
                            }
                            a{
                                color:#000;
                            }
                            li:hover{
                                a{
                                    color:#ff4d04;
                                }
                            }
                        }
                    }
                }
                .goshop{
                    width:125px;
                    background:#fff;
                    .content{
                        display: none;
                        width:350px;
                        min-height:103px;
                        background:#fff;
                        border:1px solid #f0f0f0;
                        .title{
                            width:342px;
                            height:43px;
                            line-height:43px;
                            padding-left:8px;
                            font-weight: 600;
                            color:#000;
                            font-size:12px;
                            border-bottom:1px solid #f0f0f0;
                        }
                        .none_data{
                            width:100%;
                            height:59px;
                            text-align: center;
                            line-height:59px;
                            color:#666560;
                        }
                        .data{
                            width:100%;
                            .myShopList{
                                width:100%;
                                li{
                                    width:100%;
                                    height:66px;
                                    border-bottom:1px dashed #e0dedb;
                                    .left{
                                        float:left;
                                        height:66px;
                                        width:243px;
                                        background:#fff;
                                        img{
                                            width:43px;
                                            height:43px;
                                            float:left;
                                            padding:3px;
                                            margin:7px 7px 0 15px;
                                            background:#fff;
                                            border:1px solid #e0dedb;
                                        }
                                        p{
                                            color:#000;
                                            float:left;
                                            width:170px;
                                            margin-top:7px;
                                        }
                                    }
                                    .right{
                                        width:97px;
                                        height:59px;
                                        float:right;
                                        padding:7px 10px 0 0;
                                        text-align: right;
                                        .price{
                                            color:#76756f;
                                        }
                                        a{
                                            color:#005f9e;
                                        }
                                    }
                                }
                            }
                            .jiesuan{
                                width:100%;
                                height:71px;
                                background:#f1f0ee;
                                p{
                                    width:340px;
                                    height:21px;
                                    text-align: right;
                                    padding-top:13px;
                                    color:#666560;
                                    span{
                                        color:#ff4300;
                                        font-weight:600;
                                    }
                                    i{
                                        font-size:14px;
                                        color:#ff4300;
                                        font-weight:600;
                                    }
                                }
                                a{
                                    float: right;
                                    width:124px;
                                    height:28px;
                                    margin-right:10px;
                                    border-radius:3px;
                                    text-align: center;
                                    line-height:28px;
                                    color:#fff;
                                    background:#ff4300;
                                }
                            }
                        }
                    }
                    .ctn{
                        span{
                            background:url('../../assets/yangguang.png') -32px -6px;
                        }
                    }
                }
            }
        }
    }
}
</style>
