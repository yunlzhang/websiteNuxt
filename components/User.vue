<template>
    <div class="userinfo-wrap" ref="userinfo-wrap">
        <div class="userinfo">
            <div class="username">昵称 : {{userInfo.name}}</div>
            <div class="signout"  @click="signout">退出登录</div>
        </div>
    </div>
</template>

<script>

export default {
    name: 'User',
    data() {
        return {
            
        }
    },
    props:['userInfo'],
    mounted: function () {
    },
    methods:{
        signout(){
            this.$axios({
                method:'get',
                url:'/signout'
            })
            .then(res=>{
                if(res.data.code === 200){
                    location.reload();
                }else{
                    this.$message({
                        message: res.data.message,
                        type: 'info'
                    });
                }
            }).catch(err=>{
                console.log(err);
            })
        }
    }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
    .userinfo-wrap{
        position:fixed;
        width:160px;
        right:0;
        top:60px;
        border-radius:5px;
        text-align: center;
        background: #fff;
        // border:1px solid #ccc;
        box-shadow: 0 10px 30px 0 rgba(0, 0, 0, 0.1);
        display:none;
        z-index: 1000;
        .signout{
            cursor:pointer;
            &:hover{
                color:#0db4f9;
            }
        }
    }
</style>
