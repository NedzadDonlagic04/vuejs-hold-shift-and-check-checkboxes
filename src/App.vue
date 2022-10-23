<script>
let id = 0;

export default {
    data() {
        return {
            items: [
                { text: 'This is an inbox layout.', name:`input-${id}`, id:id++ },
                { text: 'Check one item', name:`input-${id}`, id:id++ },
                { text: 'Hold down your Shift key', name:`input-${id}`} ,
                { text: 'Check a lower item', name:`input-${id}`, id:id++ },
                { text: 'Everything inbetween should also be set to checked', name:`input-${id}`, id:id++ },
                { text: 'Try to do it without any libraries', name:`input-${id}`, id:id++ },
                { text: 'Just regular Javascript', name:`input-${id}`, id:id++ },
                { text: 'Good Luck!', name:`input-${id}`, id:id++ },
                { text: "Don't forget to tweet your result!", name:`input-${id}`, id:id++ }
            ] 
        };
    },
    methods: {
        toggleClass(element) {
            element.classList.toggle('checked');
        },
        clickHandler(event) {
            this.toggleClass(event.path[1]);
        }
    }
};
</script>

<template>
    <div class="item" v-for="item of items" :key="item.id">
        <input type="checkbox" :id="item.name" @click="clickHandler">
        <label :for="item.name">{{item.text}}</label>
    </div>
</template>

<style scoped>
    .item {
        min-height: 3rem;
        vertical-align: middle;
        display: flex;
        align-items: center;
        border-bottom: 1px solid var(--label-border);
    }

    .item > input[type="checkbox"] {
        accent-color: black;
        margin: 1rem 1.5rem;
    }

    .item > input[type="checkbox"]:hover {
        cursor: pointer;
    }

    .item > label {
        border-left: 1px solid var(--label-border);
        min-height: 3rem;
        width: 100%;
        padding-left: .4rem;
        padding-top: 1rem;
        vertical-align: middle;
        font-size: 1rem;
    }

    .item.checked {
        background-color: hsla(0, 7%, 79%, 0.335);
        text-decoration: line-through;
    }

    .item:first-child > label {
        border-top-right-radius: 10px;
    }

    .item:last-child {
        border: none;
    }

    .item:last-child > label {
        border-bottom-right-radius: 10px;
    }
</style>