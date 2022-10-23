<template>
    <div class="item">
        <input type="checkbox">
        <label for="">Hello there!</label>
    </div>
    <div class="item">
        <input type="checkbox">
        <label for="">Hello there!</label>
    </div>
    <div class="item">
        <input type="checkbox">
        <label for="">Hello there!</label>
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