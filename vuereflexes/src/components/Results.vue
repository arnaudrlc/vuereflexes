<script>
export default {
    name: 'Results',
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 250) {
            this.rank = 'Obiwan Kenobi reflexes'
        } else if (this.score < 400) {
            this.rank = 'Nice reflexes'
        } else {
            this.rank = 'Common reflexes'
        }
    }
}
</script>

<template>
    <div>
        <div class="ui segment">
            <p>Reaction time - {{ score }} ms</p>
            <p>{{ rank }}</p>
        </div>
    </div>
</template>

<script></script>
