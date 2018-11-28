<template>
  <div class="dy-checkbox-wrap">
    <label class="dy-checkbox-label">
      <input type="checkbox" class="dy-checkbox-input" v-model="selectedAll">
      <span class="dy-checkbox-icon"></span>
      <span class="dy-checkbox-title">
        是否全选
      </span>
    </label>
    <label class="dy-checkbox-label" v-for="item in optionsArr">
      <input type="checkbox" class="dy-checkbox-input" v-model="selectedArr" :value="item">
      <span class="dy-checkbox-icon"></span>
      <span class="dy-checkbox-title">
        <span class="dy-checkbox-date">{{item.date}}</span>
        <span class="dy-checkbox-price">{{item.price}}</span>
      </span>
    </label>
  </div>
</template>

<script>

  export default {
    props: {
      options: {
        type: Array
      },
      value: {
        type: Array
      }
    },
    data() {
      return {
        selectedAll: false,
        optionsArr: this.options,
        selectedArr: this.value
      }
    },
    watch: {
      selectedAll(newValue) {
        if(newValue){
          this.selectedArr = [...this.optionsArr]
        }
      },
      selectedArr(newValue) {
        if(newValue.length==this.optionsArr.length){
          this.selectedAll = true
        } else {
          this.selectedAll = false
        }
        this.$emit('input', newValue)
        this.$emit('change', newValue)
      },
      options(val) {
        this.optionsArr = val
      },
      value(val) {
        this.selectedArr = val
      }
    }
  }
</script>

<style lang="less">
  .dy-checkbox-label {
    padding-left: 10px;
    height: 45px;
    line-height: 45px;
    display: flex;
    align-items: center;
    border-bottom: 1px solid #f1f1f1;
  }

  .dy-checkbox-input {
    display: none;

    & ~ .dy-checkbox-icon{
      display: inline-block;
      width: 20px;
      height: 20px;
      border-radius: 50%;
      border: 1px solid #ddd;
    }


    &:checked ~ .dy-checkbox-icon {
      position: relative;
      background-color: #409eff;

      &::after {
        content: '';
        position: absolute;
        left: 50%;
        top: 35%;
        transform: translate(-50%, -50%) rotateZ(-45deg);
        display: inline-block;
        width: 10px;
        height: 5px;
        border: 2px solid transparent;
        border-left-color: #fff;
        border-bottom-color: #fff;

      }
    }
  }

  .dy-checkbox-title {
    flex: 1;
    display: flex;
    justify-content: space-between;
    padding: 0 10px;
  }
</style>
