<template>
    <div>
        <img :src="oneroom.image" class="room-img">
        <h4 @click="send">{{oneroom.title}}</h4>
        <p>{{oneroom.price}}만원</p>
    </div>

</template>

<script>
export default {
    name : 'Card',
    props : {
        oneroom : Object,
        modal : Boolean,
    },
    methods : {
        send(){
            this.$emit('openModal', this.oneroom.id)
        }
    }
}
</script>

<style>
.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>