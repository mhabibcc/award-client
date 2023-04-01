<template>
    <div class="coupon-box">
        <div class="coupon">
            <img :src="imgUrl" alt="img-1">
            <div class="label"><span class="badge" :class="typeAward">{{ type }}</span></div>
            <div class="exchange"><strong>{{ exchange }} Poin</strong></div>
        </div>
        <strong>{{ name }}</strong>
    </div>
</template>

<script>
export default {
    props:['imgUrl', 'type', 'exchange', 'name'],
    data()
    {
        return{
            typeAward: 'bg-primary'
        }
    }
}

</script>

<style scoped>

.coupon-box {
    margin-bottom: 15px;
}
.coupon {
    max-width: 100%;
    height: 150px;
    border-radius: 15px;
    position: relative;
  text-align: center;
  color: white;
  margin-bottom: 5px;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.5);
}
.coupon img {
    width: 100%;
    height: 150px;
    object-fit: cover;
    border-radius: 15px;
}

.label {
  position: absolute;
  top: 8px;
  right: 16px;
}

.exchange {
  position: absolute;
  bottom: 8px;
  left: 16px;
}

</style>