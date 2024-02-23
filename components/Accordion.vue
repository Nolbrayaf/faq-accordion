<template>
  <div class="container">
    <h1>
      <iconsStar />FAQs
    </h1>
    <section>
      <AccordionItem v-for="(item, index) in accordionItems" :key="index" :accordionItem="item"
        :isSelected="selectedAccordionIndex === index" @update:selected="showAnswer(index)" class="accordionItem" />
    </section>

  </div>
</template>

<script setup>



const showAnswer = (index) => {
  if (selectedAccordionIndex.value !== null && selectedAccordionIndex.value !== index) {
    selectedAccordionIndex.value = null;

    setTimeout(() => {
      selectedAccordionIndex.value = index;
    }, 1000);
  } else {
    selectedAccordionIndex.value = selectedAccordionIndex.value === index ? null : index;
  }
};


const selectedAccordionIndex = ref(0);



const accordionItems = ref([

  {
    question: "What is Frontend Mentor, and how will it help me?",
    answer: `Frontend Mentor offers realistic coding challenges to help developers improve their 
  frontend coding skills with projects in HTML, CSS, and JavaScript.It's suitable for 
  all levels and ideal for portfolio building.`
  },

  {
    question: "Is Frontend Mentor free ?",
    answer: `Yes, Frontend Mentor offers both free and premium coding challenges, with the free 
  option providing access to a range of projects suitable for all skill levels.`
  },

  {
    question: "Can I use Frontend Mentor projects in my portfolio ?",
    answer: `Yes, you can use projects completed on Frontend Mentor in your portfolio. It's an excellent
  way to showcase your skills to potential employers!`
  },

  {
    question: "How can I get help if I'm stuck on a Frontend Mentor challenge?",
    answer: `The best place to get help is inside Frontend Mentor's Discord community. There's a help 
  channel where you can ask questions and seek support from other community members.`
  }
])
</script>

<style lang="scss" scoped>
.container {
  background-color: #fff;
  width: 560px;
  border-radius: 16px;
  box-shadow: 0 32px 56px rgba(80, 0, 118, 0.1);
  padding: 40px;
  display: flex;
  flex-direction: column;
  gap: 32px;


  h1 {
    display: flex;
    align-items: center;
    gap: 24px;
    font-size: 56px;
    color: $darkPurple;
    margin: 0;
  }

}

@media screen and (max-width: $sm-breakpoint) {
  .container{
    width: 100%;
    padding: 24px;
    gap: 24px;
    h1{
      font-size: 32px;
    }
  } 

}
</style>