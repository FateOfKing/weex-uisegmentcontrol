<template>
    <div class="segment">
        <div v-for="(item, index) in items" 
            :key="index" 
            :class="[ (index === 0) ? 'tabStart': '',
            (index === items.length -1) ? 'tabEnd': '',
            (index !== items.length -1) && (index !== 0) ? 'tabLine': '',
            (index === activeIndex) ? 'activeBG': 'normalBG' ]" @click="onClick(index)">
            <text :class="[(index === activeIndex) ? 'activeText': 'normalText']">{{item}}</text>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        items:{
            type: Array,
            default: function () { return ['item1', 'item2'] }   
        },
        initIndex: {
            type: Number,
            default: 0
        }, 
    },
    data() {
        return {
            activeIndex: this.initIndex,
        }
    },
    methods: {
        onClick(index) {
            if(index !== this.activeIndex) {
                this.activeIndex = index;           
            }
            this.$emit("zzhSegmentClicked", {
                data: this.activeIndex
            });
        }
    }
}
</script>

<style scoped>
.segment {
    border-radius: 20px;
    border-color: lightgrey;
    border-width: 2px;
    height: 90px;
    width: 580px;
    flex-direction: row;
    justify-content: space-between;
    align-content: center;
}
.text {
    font-size: 28px;
    align-content: center;
}
.test {
    border-top-right-radius: 20px;
}
.tabStart {
    margin-top: 0px;
    margin-left: 0px;
    margin-right: 0px;
    margin-bottom: 0px;
    background-color: aquamarine;
    align-content: center;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    flex: 1;
    border-top-left-radius: 20px;
    border-bottom-left-radius: 20px;
    border-right-width: 2px;
    border-color: rgb(173, 173, 187);
}
.tabEnd {
    margin-top: 0px;
    margin-left: 0px;
    margin-right: 0px;
    margin-bottom: 0px;
    background-color: aquamarine;
    align-content: center;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    flex: 1;
    border-top-right-radius: 20px;
    border-bottom-right-radius: 20px;
}
.tabLine {
    margin-top: 0px;
    margin-left: 0px;
    margin-right: 0px;
    margin-bottom: 0px;
    background-color: aquamarine;
    align-content: center;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    flex: 1;
    border-right-width: 2px;
    border-color: rgb(173, 173, 187);
}
.line {
    width: 10px;
    background-color: black;
}
.activeText {
    color: orange;
}
.normalText {
    color: black;
}
.activeBG {
    background-color: black;
}
.normalBG {
    background-color: white;
}
</style>
