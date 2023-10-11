<template>
  <div>
    <GiftCardCard />
    <GiftCardForm />
    <Button></Button>
  </div>
</template>

<script>
import Card from './components/GiftCard/Card.vue';

export default {
  components: {
    GiftCardCard: Card,
  },
};
</script>
