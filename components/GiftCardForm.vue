<template>
    <div class="flex justify-center items-center min-h-screen gap-5">
        <div class="h-[400px] card-content mt-16">
            <form @submit.prevent="submitForm"
                class="gift-card-form py-10 rounded-xl bg-white px-8 w-[580px] h-[650px]">
                <div>
                    <h1 class="text-[#D450BC] text-2xl font-bold mb-4">I would like to gift</h1>
                </div>
                <div class="form-group flex flex-col">
                    <div class="flex gap-6">
                        <div class="radio-group">
                            <input type="radio" id="amount" value="Amount" v-model="formData.selectedOption" />
                            <label class="font-semibold" for="amount">Amount</label>
                        </div>
                        <div class="radio-group">
                            <input type="radio" id="giftCard" value="Gift Card" v-model="formData.selectedOption" />
                            <label class="font-semibold" for="giftCard">Gift Card</label>
                        </div>
                        <div class="radio-group">
                            <input type="radio" id="package" value="Package" v-model="formData.selectedOption" />
                            <label class="font-semibold" for="package">Package</label>
                        </div>
                    </div>
                </div>

                <div v-if="formData.selectedOption === 'Gift Card'">
                    <div class="form-group flex flex-col mb-2">
                        <label class="font-bold pb-2 pt-4" for="giftCardCode">Enter Gift Card Code:</label>
                        <input type="text" id="giftCardCode" v-model="formData.giftCardCode"
                            class="border border-gray-300 font-bold rounded-[6px] py-3 shadow-md" />
                    </div>
                </div>
                <div class="form-group flex flex-col mb-2">
                    <label class="text-[#D450BC] text-xl font-bold pb-2 pl-2" for="amount">Select an Amount</label>
                    <select id="amount" v-model="formData.amount" class="pl-2 border font-bold border-gray-300 rounded-md py-4 shadow-md">
                        <option class="pb-5 pl-2 font-bold" value="$25">$25</option>
                        <option class="pb-5 pl-2 font-bold" value="$75">$75</option>
                        <option class="pb-5 pl-2 font-bold" value="$100">$100</option>
                        <option class="pb-5 pl-2 font-bold" value="Custom">Custom</option>
                    </select>
                </div>

                <div class="form-group flex flex-col mb-2">
                    <label class="text-[#D450BC] text-xl font-bold pb-2 pl-2" for="occasion">Choose Occasion</label>
                    <select id="occasion" v-model="formData.occasion"
                        class="pl-2 border border-gray-300 rounded-md font-bold py-4 shadow-md">
                        <option value="A Gift for you pl-2 font-bold">A Gift for you</option>
                        <option value="Mother’s Day pl-2 font-bold">Mother’s Day</option>
                        <option value="Anniversary pl-2 font-bold">Anniversary</option>
                        <option value="Happy Christmas pl-2 font-bold">Happy Christmas</option>
                    </select>
                </div>
                <label class="text-[#D450BC] text-xl font-bold pb-2 pl-2" for="occasion">Details</label>
                <div class="form-group flex flex-col mb-2">
                    <label class="font-bold pb-2 pt-4 pl-2" for="to">To</label>
                    <input type="text" id="to" v-model="formData.to"
                        class="border pl-2 font-bold border-gray-300 rounded-md py-4 shadow-md" />
                </div>

                <div class="form-group flex flex-col mb-2">
                    <label class="font-bold pb-2 pl-2" for="recipientEmail">Recipient’s Email</label>
                    <input type="email" id="recipientEmail" v-model="formData.recipientEmail"
                        class="border pl-2 font-bold border-gray-300 rounded-md py-4 shadow-md" />
                </div>

                <div class="form-group flex flex-col mb-2">
                    <label class="font-bold pb-2 pl-2" for="recipientPhone">Recipient’s Phone (optional)</label>
                    <input type="number" id="recipientPhone" v-model="formData.recipientPhone"
                        class="border pl-2 font-bold border-gray-300 rounded-md py-4 shadow-md" />
                </div>

                <div class="form-group flex flex-col mb-2">
                    <label class="font-bold pb-2 pl-2" for="message">Message (optional)</label>
                    <textarea id="message" v-model="formData.message"
                        class="border pl-2 font-bold border-gray-300 rounded-md py-4 shadow-md"></textarea>
                </div>

                <div class="form-group">
                    <label class="font-bold pb-2 pl-2" for="delivery">Delivery Date & Time</label>
                    <div class="flex justify-between mt-3">

                        <div class="radio-group">
                            <input type="radio" id="now" value="Now" v-model="formData.deliveryTime" />
                            <label class="font-semibold" for="now">Now</label>
                        </div>
                        <div class="radio-group">
                            <input type="radio" id="selectDateTime" value="Select Date & Time"
                                v-model="formData.deliveryTime" />
                            <label class="font-semibold" for="selectDateTime">Select Date & Time</label>

                        </div>
                    </div>
                </div>
            </form>
        </div>
        <div class="card">
            <div class="card-content">
                <h1 class="text-2xl pt-5 w-[440px] h-[450px] text-pink-600 font-bold">Preview</h1>
                
            </div>
        </div>
    </div>
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

.card {
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 20px;
}

.card-content {
    height: 100%;
    overflow-y: auto;
    /* Make the card content scrollable vertically */
}
</style>












