<template>
    <div class="black-bg" v-if="modal === true">
        <div class="white-bg">
            <h4>{{oneroom[modalIndex].title}}</h4>
            <p>{{oneroom[modalIndex].content}}</p>
            <input v-model="month" type="text">
            <p>{{month}}개월 선택함 : {{oneroom[modalIndex].price * month}}원</p>
            <button @click="$emit('closeModal')">닫기</button>
        </div>
    </div>
</template>

<script>
import oneroom from '../assets/oneroom';

export default {
    name : 'Modal',
    props : {
        oneroom : Object,
        modal : Boolean,
        modalIndex : Number,
    },
    data (){
        return {
            month : 1,
        }
    },
    watch : {
        month(a){
            if(isNaN(a) == true){
                alert('숫자를 입력해주세요');
                this.month = 1;
            }
        }
    },
}
</script>

<style>
.black-bg {
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    position: fixed;
    padding: 20px;
    margin: 0 auto;
}

.white-bg {
    width: 50%;
    background: white;
    border-radius: 8px;
    padding: 20px;
    color: black;
}
</style>