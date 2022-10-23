<script>
let id = 0;

export default {
    data() {
        return {
            items: [
                { text: 'This is an inbox layout.', name:`input-${id}`, id:id++ },
                { text: 'Check one item', name:`input-${id}`, id:id++ },
                { text: 'Hold down your Shift key', name:`input-${id}`, id:id++} ,
                { text: 'Check a lower item', name:`input-${id}`, id:id++ },
                { text: 'Everything inbetween should also be set to checked', name:`input-${id}`, id:id++ },
                { text: 'Try to do it without any libraries', name:`input-${id}`, id:id++ },
                { text: 'Just regular Javascript', name:`input-${id}`, id:id++ },
                { text: 'Good Luck!', name:`input-${id}`, id:id++ },
                { text: "Don't forget to tweet your result!", name:`input-${id}`, id:id++ }
            ],
            shiftElements: [],
        };
    },
    methods: {
        toggleClass(element) {
            element.classList.toggle('checked');
        },
        clickHandler(event, id) {
            const element = event.target.parentNode;

            if(this.shiftElements.length === 2)
            {
                this.shiftElements.shift();
            }

            this.shiftElements.push({
                id: id,
                element: element
            });

            this.toggleClass(element);
        },
        checkElements(element1, element2, state)
        {
            let element = element1.element.previousElementSibling;
            for(let i = element1.id - 1; i > element2.id; i--)
            {
                element.querySelector('input[type="checkbox"]').checked = state;

                if(state && !element.classList.contains('checked'))
                {
                    element.classList.add('checked');
                }
                else if(!state && element.classList.contains('checked'))
                {
                    element.classList.remove('checked');
                }

                element = element.previousElementSibling;
            }
        },
        shiftClickHandler() {
            if(this.shiftElements.length === 2)
            {
                const state = this.shiftElements[1].element.querySelector('input[type="checkbox"]').checked;
                const [element1, element2] = this.shiftElements;

                (element1.id > element2.id)? this.checkElements(element1, element2, state) : this.checkElements(element2, element1, state);
            }
        }
    }
};
</script>

<template>
    <div class="item" v-for="item of items" :key="item.id">
        <input type="checkbox" :id="item.name" @click="clickHandler($event, item.id)" @click.shift.left="shiftClickHandler()">
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

    .item:first-child {
        border-top-right-radius: 10px;
    }

    .item:last-child {
        border-style: none;
        border-bottom-right-radius: 10px;
    }
</style>