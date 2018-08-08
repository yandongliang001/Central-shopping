<template>
    <div class="box">
        <div class="top_nav_box">
            <div class="top_nav">
                <ul class="nav_left">
                    <li v-for='i in navArr' :key='i.id' @mouseover="i.show = false" @mouseout="i.show = true" :class='i.id<=(navArr.length-1)?"active":""'>
                        <i v-if='!i.childShow'></i>
                        <a :href='i.href' :class='i.claName'>{{i.content}}</a>
                        <span v-if='i.childShow'></span>
                        <transition name='fade' enter-active-class='animated fadeInDown'>
                            <ul v-if='!i.show' :class='i.claName'  @mouseover="i.show = true">
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
                        <li v-for='i in bomBoxArr' :class='i.className'>
                            <a :href="i.href">{{i.content}}</a>
                        </li>
                    </ul>
                </div>
                <div class="bom_box_center">
                    <div class="search_box">

                    </div>
                </div>
                <div class="bom_box_right">

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
                    show:true,
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
                    show:true,
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
                    show:true,
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
                    show:false,
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
            ]
        }
    },
    methods:{

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
                        border-top:0;
                        background:#fff;
                        animation-duration: 0.3s;       //动画执行时间
                        animation-delay: 0s;            //动画延迟执行时间
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
                background:#ccc;
                .search_box{
                    width:100%;
                    height:40px;
                    float:left;
                    margin-top:24px;
                    background:#0f0;
                }
            }
            >.bom_box_right{
                width:295px;
                height:100%;
                background:#ff5b57;
            }
        }
    }
}
</style>
