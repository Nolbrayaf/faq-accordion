<template>
    <article>
        <div @click="showAnswer" class="question" tabindex="0" @keyup.enter="showAnswer" role="button"
            :aria-expanded="isSelected.toString()" :aria-controls="'accordion-content-' + accordionItem.id">
            <h2>{{ accordionItem.question }}</h2>
            <img src="../assets/images/icons/icon-plus.svg" v-if="!isSelected" alt="Plus icon" />
            <img src="../assets/images/icons/icon-minus.svg" alt="Minus icon" v-else />
        </div>
        <Transition name="showAnswer">
            <p v-if="isSelected" class="answer" :id="'accordion-content-' + accordionItem.id">{{ accordionItem.answer }}</p>
        </Transition>
    </article>
    <hr>
</template>
<script setup>

const props = defineProps({
    accordionItem: Object,
    isSelected: Boolean
})

const emit = defineEmits(['update:selected']);

const showAnswer = () => {
    emit('update:selected', !props.isSelected)
}


</script>
<style lang="scss" scoped>
article {
    display: flex;
    flex-direction: column;
    gap: 24px;


    .question {
        display: flex;
        justify-content: space-between;
        align-items: center;
        color: $darkPurple;
        cursor: pointer;

        &:hover {
            h2 {
                color: $pink;
            }
        }


        h2 {
            font-size: 18px;
            font-weight: 700;
        }
    }

    .answer {
        color: $grayishPurple;
    }
}

hr {
    border-color: $lightPink;

    &:last-of-type {
        display: none;
    }
}

.question:focus{
    outline: 2px solid $pink;

}


@media screen and (max-width: $sm-breakpoint) {

    article {
        gap: 20px;

        .question {
            gap: 24px;

            h2 {
                font-size: 16px;

            }
        }

        p {
            font-size: 14px;
        }
    }
}




// TRANSITION STYLES

.showAnswer-enter-from,
.showAnswer-leave-to {
    max-height: 0;
    opacity: 0;
}

.showAnswer-enter-to,
.showAnswer-leave-from {
    max-height: 500px;
    opacity: 1;
}

.showAnswer-enter-active {
    transition: max-height 1s ease-in-out, opacity 1s ease-in-out;
}

.showAnswer-leave-active {
    transition: max-height 0.5s ease-in-out, opacity 0.5s ease;
}
</style>