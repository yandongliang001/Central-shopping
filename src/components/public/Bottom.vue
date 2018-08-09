<template>
    <div class='bottom'>
        <div class="bottom_auto">
            <ul class='new_nav'>
                <li v-for='i in newArr' :key='i.id'>
                    <a :href="i.href">{{i.content}}</a>
                </li>
            </ul>
            <ul class='wb'>
                <img src="../../assets/gh.png" alt=""/>
                <li v-for='key in wbArr' :key='key.id'>
                    <a :href="key.href">{{key.content}}</a>
                </li>
            </ul>
            <ul class="english">
                <li v-for='k in englishArr' :key='k.id'>{{k.content}}</li>
            </ul>
            <ul class="baimg">
                <li><a href="javascript:;"></a></li>
                <li><a href="javascript:;"></a></li>
                <li><a href="javascript:;"></a></li>
                <li><a href="javascript:;"></a></li>
            </ul>
        </div>
    </div>
</template>
<script>
export default {
    name:"Bottom",
    data(){
        return {
            newArr:[
                {id:1,content:'首页',href:''},
                {id:2,content:'招商合作',href:''},
                {id:3,content:'关于央广购物',href:''},
                {id:4,content:'联系我们',href:''},
                {id:5,content:'成为供应商',href:''},
                {id:6,content:'招贤纳士',href:''}
            ],
            wbArr:[
                {id:1,content:'京公网安备：11011502002190',href:'javascript:;'},
                {id:2,content:'京ICP备10038858号',href:'javascript:;'},
                {id:3,content:'食品流通许可证编号：SP1101151210063489',href:'javascript:;'},
                {id:4,content:'信息网络传播视听节目许可证 0102002号',href:'javascript:;'},
                {id:5,content:'营业执照',href:''},
            ],
            englishArr:[
                {id:1,content:'Copyright©2010-2017 cnrmall.com All Rights Reserved',href:'javascript:;'},
                {id:2,content:'服务热线：4008-518-518',href:'javascript:;'}
            ]
        }
    }
}   
</script>
<style lang="scss" scoped>
.bottom{
    width:100%;
    height:181px;
    background:#343a3a;
    .bottom_auto{
        width:1210px;
        height:181px;
        margin:0 auto;
        position: relative;
        .new_nav{
            width:440px;
            height:48px;
            top:0;
            left:0;
            right:0;
            margin:0 auto auto auto;
            position:absolute;
            text-align: center;
            line-height:48px;
            li{
                float: left;
                a{
                    color:#fff;
                    padding:0 13px;
                    border-left:1px solid #92b3b3;
                }
                a:hover{
                    text-decoration:underline;
                }
            }
            li:last-child{
                a{
                    padding-right:0;
                }
            }
            li:first-child{
                a{
                    padding-left:0;
                    border-left:0;
                }
            }
        }
        .wb{
            width:880px;
            height:20px;
            top:48px;
            left:0;
            right:0;
            margin:0 auto auto auto;
            line-height:20px;
            position:absolute;
            img{
                position:absolute;
                top:0;
                left:-4px;
            }
            li{
                float:left;
                padding-left:16px;
                a{
                    color:#fff;
                }
                a:hover{
                    text-decoration:underline;
                }
            }
        }
        .english{
            width:537px;
            height:50px;
            top:68px;
            left:0;
            right:0;
            line-height:50px;
            margin:0 auto auto auto;
            position:absolute;
            li{
                color:#fff;
            }
            li:first-child{
                float:left;
            }
            li:last-child{
                float:right;
            }
        }
        .baimg{
            width:492px;
            height:40px;
            top:121px;
            left:0;
            right:0;
            margin:0 auto auto auto;
            position:absolute;
            li{
                float:left;
                width:108px;
                height:40px;
                margin-left:20px;
                a{
                    display:inline-block;
                    width:100%;
                    height:100%;
                    background:url('../../assets/yangguang-footer.png');
                }
            }
            li:nth-child(1){
                margin-left:0;
            }
            li:nth-child(2){
                a{
                    background-position-x: -122px;
                }
            }
            li:nth-child(3){
                a{
                    background-position-x: -244px;
                }
            }
            li:nth-child(4){
                a{
                    background-position-x: -488px;
                }
            }
        }
    }
}
</style>
