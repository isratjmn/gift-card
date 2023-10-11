<template>
    <form @submit.prevent="submitForm"
        class="gift-card-form py-10 -mt-24 rounded-xl bg-white px-8 shadow-lg mx-auto w-[580px]">
        <div>
            <h1 class="text-pink-600 text-2xl font-bold mb-4">I would like to gift</h1>
        </div>
        <div class="form-group flex flex-col">
            <div class="flex gap-6">
                <div class="radio-group">
                    <input type="radio" id="amount" value="Amount" v-model="formData.selectedOption" />
                    <label for="amount">Amount</label>
                </div>
                <div class="radio-group">
                    <input type="radio" id="giftCard" value="Gift Card" v-model="formData.selectedOption" />
                    <label for="giftCard">Gift Card</label>
                </div>
                <div class="radio-group">
                    <input type="radio" id="package" value="Package" v-model="formData.selectedOption" />
                    <label for="package">Package</label>
                </div>
            </div>
        </div>
        <div v-if="formData.selectedOption === 'Amount'">
            <!-- Amount-related fields go here -->
            <div class="form-group flex flex-col mb-2">
                <label class="font-bold pb-2 pt-4" for="amount">Enter an amount:</label>
                <input type="text" id="amount" v-model="formData.amount"
                    class="border border-pink-500 rounded-[6px] py-3" />
            </div>
        </div>

        <div v-if="formData.selectedOption === 'Gift Card'">
            <div class="form-group flex flex-col mb-2">
                <label class="font-bold pb-2 pt-4" for="giftCardCode">Enter Gift Card Code:</label>
                <input type="text" id="giftCardCode" v-model="formData.giftCardCode"
                    class="border border-pink-500 rounded-[6px] py-3" />
            </div>
        </div>

        <div v-if="formData.selectedOption === 'Package'">

            <div class="form-group flex flex-col mb-2">
                <label class="font-bold pb-2 pt-4" for="packageType">Select a Package Type:</label>
                <select id="packageType" v-model="formData.packageType" class="border border-pink-500 rounded-[6px] py-3">
                    <option value="Basic">Basic</option>
                    <option value="Premium">Premium</option>
                </select>
            </div>
        </div>
        <div class="form-group flex flex-col mb-2">
            <label class="font-bold" for="amount">Select an amount:</label>
            <select id="amount" v-model="formData.amount" class="border border-pink-500 rounded-md py-4">
                <option class="pb-5" value="$25">$25</option>
                <option class="pb-5" value="$75">$75</option>
                <option class="pb-5" value="$100">$100</option>
                <option class="pb-5" value="Custom">Custom</option>
            </select>
        </div>

        <div class="form-group flex flex-col mb-2">
            <label class="font-bold" for="occasion">Choose Occasion:</label>
            <select id="occasion" v-model="formData.occasion" class="border border-pink-500 rounded-md py-4">
                <option value="A Gift for you">A Gift for you</option>
                <option value="Mother’s Day">Mother’s Day</option>
                <option value="Anniversary">Anniversary</option>
                <option value="Happy Christmas">Happy Christmas</option>
            </select>
        </div>

        <div class="form-group flex flex-col mb-2">
            <label class="font-bold" for="to">To:</label>
            <input type="text" id="to" v-model="formData.to" class="border border-pink-500 rounded-md py-4" />
        </div>

        <div class="form-group flex flex-col mb-2">
            <label class="font-bold" for="recipientEmail">Recipient’s Email:</label>
            <input type="email" id="recipientEmail" v-model="formData.recipientEmail"
                class="border border-pink-500 rounded-md py-4" />
        </div>

        <div class="form-group flex flex-col mb-2">
            <label class="font-bold" for="recipientPhone">Recipient’s Phone (optional):</label>
            <input type="number" id="recipientPhone" v-model="formData.recipientPhone"
                class="border border-pink-500 rounded-md py-4" />
        </div>

        <div class="form-group flex flex-col mb-2">
            <label class="font-bold" for="message">Message (optional):</label>
            <textarea id="message" v-model="formData.message" class="border border-pink-500 rounded-md py-4"></textarea>
        </div>

        <div class="form-group">
            <label class="font-bold" for="delivery">Delivery Date & Time:</label>
            <div class="flex justify-between mt-3">

                <div class="radio-group">
                    <input type="radio" id="now" value="Now" v-model="formData.deliveryTime" />
                    <label for="now">Now</label>
                </div>
                <div class="radio-group">
                    <input type="radio" id="selectDateTime" value="Select Date & Time" v-model="formData.deliveryTime" />
                    <label for="selectDateTime">Select Date & Time</label>

                </div>
            </div>
        </div>
    </form>
</template>

<script>
export default {
    data() {
        return {
            formData: {
                selectedOption: 'Amount',
                amount: '',
                giftCardCode: '',
                packageType: 'Basic',
                amount: '$25',
                occasion: 'A Gift for you',
                to: '',
                recipientEmail: '',
                recipientPhone: '',
                message: '',
                deliveryTime: 'Now',
                selectedDateTime: '',
            },
        };
    },
    methods: {
        submitForm() {

            console.log('Form submitted with data:', this.formData);
        },
    },
};
</script>

<style>
.form-group {
    margin-bottom: 1rem;
}

.radio-group {
    margin-bottom: 1rem;
}

#gift-card-form input[type="text"],
#gift-card-form input[type="email"],
#gift-card-form input[type="number"],
#gift-card-form textarea {
    border: 1px solid #e2e8f0;
    padding: 0.5rem;
    width: 100%;
}

#gift-card-form select {
    border: 1px solid #e2e8f0;
    padding: 0.5rem;
    width: 100%;
}

#gift-card-form #selectedDateTime {
    border: 1px solid #e2e8f0;
    padding: 0.5rem;
    width: 100%;
}

.form-group {
    margin-bottom: 1rem;
}

.radio-group {
    display: flex;
    align-items: center;
    margin-bottom: 0.5rem;
}

.radio-group input[type="radio"] {
    margin-right: 0.5rem;
}
</style>
  