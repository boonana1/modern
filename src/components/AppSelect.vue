<template>
    <div class="custom-select" :tabindex="tabindex" @blur="open = false">
        <div class="selected" :class="{ open: open }" @click="open = !open">
            {{ selected }}
        </div>
        <div class="items" :class="{ selectHide: !open }">
            <div v-for="(option, i) of options" :key="i" @click="
                selected = option;
            open = false;
            $emit('input', option);
            ">
                {{ option }}
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    props: {
        options: {
            type: Array,
            required: true,
        },
        default: {
            type: String,
            required: false,
            default: null,
        },
        tabindex: {
            type: Number,
            required: false,
            default: 0,
        },
    },
    data() {
        return {
            selected: this.default
                ? this.default
                : this.options.length > 0
                    ? this.options[0]
                    : null,
            open: false,
        };
    },
    mounted() {
        this.$emit("input", this.selected);
    },
};
</script>
  
<style scoped>
.custom-select {
    position: relative;
    max-width: 540px;
    width: 100%;
    text-align: left;
    outline: none;
    height: 32px;
    line-height: 32px;
}

.custom-select .selected {
    border: 1px solid #B3B3B3;
    background: #FFF;
    color: #b3b3b3;
    padding-left: 10px;
    cursor: pointer;
    user-select: none;
}

.error .custom-select .selected {
    border: 1px solid var(--error-color);
    color: var(--error-color);
}

.custom-select .selected.open {
    border: 1px solid #B3B3B3;
}

.custom-select .selected:before {
    position: absolute;
    content: "";
    top: 1px;
    right: 1px;
    width: 32px;
    height: 100%;
    background: var(--primary-color);
}

.custom-select .selected.open:after {
    transform: rotate(180deg);
}

.custom-select .selected:after {
    position: absolute;
    content: "";
    top: 1px;
    right: 0;
    width: 32px;
    height: 100%;
    background: url("@/assets/img/keyboard-arrow-down.svg") center/cover;
    filter: brightness(5);
    transform: rotate(0deg);
    transition: transform .2s ease-in-out;
    /* border: 5px solid transparent;
    border-color: #fff transparent transparent transparent; */
}

.custom-select .items {
    overflow: hidden;
    border-right: 1px solid #B3B3B3;
    border-left: 1px solid #B3B3B3;
    border-bottom: 1px solid #B3B3B3;
    position: absolute;
    background-color: #fff;
    padding-left: 10px;
    left: 0;
    right: 0;
    z-index: 1;
}

.custom-select .items div {
    cursor: pointer;
    user-select: none;
}

.custom-select .items div:hover {
    background-color: var(--primary-color);
    color: #FFF;
}

.selectHide {
    display: none;
}
</style>
  