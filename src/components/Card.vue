<script>
export default {
}

</script>

<template>
      <div class="card">
        <slot>
        </slot>
      </div>
</template>

<style scoped>
.card{
    padding:1rem 2rem;
    background:white;
    border-radius:12px;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
    margin:1rem 0;
}
</style>
