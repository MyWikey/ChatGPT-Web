<template>
    <el-row justify="center">
        <el-col :span="16">
            <el-row justify="center">
                <p class="hero-title">ChatGPT-Web {{ version }}</p>
            </el-row>
            <el-row justify="center" align="middle">
                <el-button size="large" type="warning" icon="Iphone" @click="jumpMobile" circle>
                    </el-button>
                <el-link icon="Link" class="hero-subtitle" href="https://github.com/MyWikey/ChatGPT-Web" target="_blank">
                    GitHub
                </el-link>
                <el-switch v-model="theme" size="large" active-icon="Sunny" inactive-icon="Moon"
                    style="--el-switch-on-color:#f89898;" inline-prompt />
            </el-row>
            <el-row justify="center">
                <el-image style="width: 150px; height: 150px"
                    src="https://i.postimg.cc/GtDQxC78/1.png" />
            </el-row>
            <el-row justify="center">
                <p class="desc-small">😊个人微信号 </p>
            </el-row>
            <el-row><p></p></el-row>
            <el-row justify="center">
                <p class="desc">🚀遇事不决问AI,无限制体验ChatGPT！</p>
            </el-row>
            <el-row><p></p></el-row>
        </el-col>
    </el-row>
</template>

<script>
import packageJSON from "../../package.json";
export default {

    name: "Hero",
    emits: ['turnMobile'],
    data() {
        return {
            theme: true,
            version: packageJSON.version,
        }
    },
    watch: {
        theme: {
            handler(val) {
                console.log(val);
                this.changeTheme(val);
                localStorage.setItem('theme', val)
            },
            deep: true
        },

    },
    mounted() {
        if (localStorage.getItem('theme')) {
            this.theme = localStorage.getItem('theme') == "true" ? true : false;
        }

    },
    methods: {

        jumpMobile() {
            this.$emit('turnMobile', true)
        },
        changeTheme(light) {

            document.documentElement.className = light ? '' : 'dark';

        }
    }

}
</script>

<style>
.hero-title {
    font-size: 2rem;
    margin: 1rem;
    font-weight: bolder;
}

.hero-subtitle {
    font-size: 1.5rem;
    margin: 1rem;
    font-weight: bold;
}

.el-image {
    margin: 1px;
}

.desc {
    font-size: 1.5rem;
    margin: 0rem 0;


}

.desc-small {
    font-size: 1rem;
    margin: 0rem 0;
    font-weight: bolder;

}
</style>