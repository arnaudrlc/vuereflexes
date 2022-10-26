<script>
export default {
    name: 'Target',
    props: ['delay'],
    data() {
        return {
            show: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.show = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        fireEvent() {
            clearInterval(this.timer)
            this.$emit('fired', { 'reactionTime': this.reactionTime })
        }
    }
}
</script>

<template>
    <div class="ui primary button" v-show="show" @click="fireEvent">
        Click!
    </div>
</template>

<style scoped>

</style>
