<template>
    <div class="container">
        <div class="flex">
            <div class="img-wrapper">
                <img 
                v-show="isCatVisible"
                :class="imgFilters"
                :style="imgStyle"
                src="../assets/images/cat.jpg" 
                />
            </div>
            <div class="controls">
                <h1>Шаверма-кот</h1>
                <h2>Фильтры</h2>
                <div class="btn-group flex">
                    <button :class="imgFilters.sepia ? 'active' : ''" @click="imgFilters.sepia = !imgFilters.sepia" type="button">Сепия</button>
                    <button :class="imgFilters.border ? 'active' : ''" @click="imgFilters.border = !imgFilters.border" type="button">Рамка</button>
                    <button :class="imgFilters.shadow ? 'active' : ''" @click="imgFilters.shadow = !imgFilters.shadow" type="button">Тень</button>
                </div>
                <h3>Размер</h3>
                <label>
                    Ширина: {{imgSizes.currentWidth}}
                    <input type="range"
                    :value="imgSizes.currentWidth"
                    @input="imgSizes.currentWidth = $event.target.value"
                    :min="imgSizes.minWidth"
                    :max="imgSizes.maxWidth"
                    />
                </label>
                <label>
                    Высота: {{imgSizes.currentHeight}}
                    <input type="range"
                    :value="imgSizes.currentHeight"
                    @input="imgSizes.currentHeight = $event.target.value"
                    :min="imgSizes.minHeight"
                    :max="imgSizes.maxHeight"
                    />
                </label>
                <h4>Поворот</h4>
                <label>
                    Угол: {{imgRotate.currentAngle}}
                    <input type="range"
                    :min="imgRotate.minAngle"
                    :max="imgRotate.maxAngle"
                    :value="imgRotate.currentAngle"
                    @input="imgRotate.currentAngle = $event.target.value"
                    />
                </label>
                <button v-if="isCatVisible" @click="isCatVisible = !isCatVisible">Спрятать</button>
                <button v-else @click="isCatVisible = !isCatVisible">Показать</button>
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
                shadow: false,
            },
            imgSizes: {
                maxWidth: 680,
                maxHeight: 480,
                currentWidth: 680,
                currentHeight: 480,
            },
            imgRotate: {
                currentAngle: 0,
                maxAngle: 360,
            }
        }
    },
    computed: {
        imgStyle() {
            return {
                width: `${this.imgSizes.currentWidth}px`,
                height: `${this.imgSizes.currentHeight}px`,
                transform: `rotate(${this.imgRotate.currentAngle}deg)`
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    .flex {
        display: flex;
    }
  .container {
    max-width: 1170px;
    margin: 0 auto;
  }
  .controls {
    margin-left: 20px;
  }
  .img-wrapper {
    position: relative;
    z-index: -1;
    width: 680px;
  }
img {
    transition: 0.2s ease;
    &.sepia {
        filter: sepia(100%);
    }
    &.border {
        border: 5px dashed #464646
    }
    &.shadow {
        box-shadow: 5px 5px 15px 5px #000000;
    }
}

  button {
    margin-right: 10px;
    padding: 10px 20px;
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