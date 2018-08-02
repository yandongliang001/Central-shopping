<template>
    <div class="box">
        <div class="top_nav_box">
            <div class="top_nav">
                <ul class="nav_left">
                    <li v-for='i in navArr' :key='i.id'><a :href='i.href' :class='i.claName'>{{i.content}}</a><span></span></li>
                </ul>
                <ul class="nav_right">
                    <li><a href="#">您好请登陆</a></li>
                    <li class="login"><a href="#">免费注册</a></li>
                </ul>
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
                {id:1,content:'我的订单',claName:'',href:''},
                {id:2,content:'我的收藏',claName:'',href:''},
                {id:3,content:'客户服务',claName:'',href:''},
                {id:4,content:'成为供应商',claName:'gys',href:''}
            ]
        }
    }
}    
</script>
<style lang="scss" scoped>
.box{
    width:100%;
    height:189px;
    background:#fff;
    border-bottom:1px solid #f15c18;
    .top_nav_box{
        width:100%;
        height:39px;
        border-bottom:1px solid #e5e5e5;
        .top_nav{
            width:1210px;
            height:100%;
            margin:0 auto;
            background:#ccc;
            ul{
                float:right;
                li{
                    float: left;
                    line-height:39px;
                    color:#777777;
                }
            }
            .nav_left{
                li{
                    padding:0 12px;
                    position:relative;
                    a{
                        padding:0 12px;
                        border-left:1px solid #e1e1e1;
                    }
                    span{
                        width:6px;
                        height:3px;
                        top:18px;
                        position:absolute;
                        background: url('../../assets/top_bg.png') 0px 0px;
                    }
                }
                .gys span{
                    width:20px;
                    height:20px;
                }
            }
            .nav_right{
                .login{
                    a{
                        color:#ff5b57;
                    }
                }
            }
        }
    }
}
</style>
