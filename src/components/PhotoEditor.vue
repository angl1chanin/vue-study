<template>
    <div class="container">
        <div class="flex">
            <div class="img-wrapper">
                <img 
                v-show="isCatVisible"
                :class="imgFilters"
                src="../assets/images/cat.jpg" 
                />
            </div>
            <div class="controls">
                <h1>Шаверма-кот</h1>
                <h2>Фильтры</h2>
                <div class="btn-group flex">
                    <button :class="imgFilters.sepia ? 'active' : ''" @click="imgFilters.sepia = !imgFilters.sepia" type="button">Сепия</button>
                    <button :class="imgFilters.border ? 'active' : ''" @click="imgFilters.border = !imgFilters.border" type="button">Рамка</button>
                    <button :class="imgFilters.small ? 'active' : ''" @click="imgFilters.small = !imgFilters.small" type="button">Уменьшить</button>
                    <button :class="isCatVisible ? 'active' : ''" @click="isCatVisible = !isCatVisible">Показать / спрятать</button>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
export default {
    name: "PhotoEditor",
    data() {
        return {
            isCatVisible: true,
            imgFilters: {
                sepia: false,
                border: false,
                small: false,
            }
        }
    }
}
</script>

<style lang="scss" scoped>
  .container {
    margin-top: 40px;
  }
  .controls {
    margin-left: 20px;
  }
  .img-wrapper {
    width: 640px;
    height: 480px;
    background-color: #cecece;
  }
img {
    transition: 0.2s ease;
    &.sepia {
        filter: sepia(100%);
    }
    &.border {
        border: 5px dashed #464646
    }
    &.small {
        width: 400px;
    }
}

  button {
    margin-right: 10px;
    &.active {
            background-color: #dbdbdb;
        }
    }
    
    h2 {
        margin-bottom: 10px;
    }
    
    .btn-group {
        margin-bottom: 20px;
    }
    
    input[type="range"] {
        display: block;
    }
</style>
