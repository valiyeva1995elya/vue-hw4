<script>
export default {
    data() {
        return {
            images: [],
            image: 0,
            src: ""
        }
    },
    methods: {
        addImg() {
            if (this.src == "") {
                return
            }
            let newBlock = this.src
            this.images.push(newBlock)
            this.src = ""
        },



    }
}


</script>

<template>
    <main>
        <div>
            <input type="text" placeholder="URL" v-model="src">
            
            <button @click="addImg">Добавить</button>
        </div>

        <button v-for="(n, i) in images" @click="image = i">
            Картинка №{{ i + 1 }}
        </button>

        <transition name="image" mode="out-in">
            <img :key="image" :src="images[image]">
        </transition>


    </main>
</template>

<style scoped>
main{
    display: flex;
    flex-direction: column;
}
.image-enter-active,
.image-leave-active {
  transition: opacity .3s;
}

.image-enter,
.image-leave-to {
  opacity: 0;
}
</style>
