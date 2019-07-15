<template>
    <div>
        <div class="row">
            <div
                id="firstcard"
                class="card offset-md-2 col-md-3"
            >
                <div class="card-body tex-center d-flex align-items-center flex-column">
                    <img
                        height="128"
                        class="firstpic img-responsive text-center mb-3"
                        :src="product.selectedImage == null ? 'https://kaangokdemir.me/productsave/images/default.svg' : product.selectedImage"
                    >
                    <input
                        ref="file"
                        type="file"
                        accept="image/x-png,image/gif,image/jpeg"
                        style="display: none;"
                        @change="onChange($event)"
                        class="form-control"
                    >
                    <button
                        class="btn btn-outline-secondary "
                        type="button"
                        @click="$refs.file.click()"
                    >Choose a Pic</button>
                </div>
            </div>
            <div class="col-md-5">
                <div class="col-md-11 card">
                    <div class="card-body">
                        <div class="form-group">
                            <label>Product Name:</label>
                            <input
                                type="text"
                                v-model="product.title"
                                class="form-control"
                                placeholder="Type product name"
                            >
                        </div>
                        <div class="row">
                            <div class="form-group col-md-6">
                                <label>Amount:</label>
                                <input
                                    type="text"
                                    onkeypress='return event.charCode>= 48 &&event.charCode<= 57 || event.charCode==44 || event.charCode==46'
                                    v-model="product.count"
                                    class="form-control"
                                    placeholder="0-99"
                                >
                            </div>
                            <div class="form-group col-md-6">
                                <label>Price:</label>
                                <input
                                    type="text"
                                    onkeypress='return event.charCode>= 48 &&event.charCode<= 57 || event.charCode==44 || event.charCode==46'
                                    v-model="product.price"
                                    class="form-control"
                                    placeholder="$"
                                >
                            </div>
                        </div>
                        <button
                            @click="addProduct"
                            class="btn btn-outline-success btn-block"
                            :class="{isdisable:reachedMaxHere==12}"
                        >Add</button>
                    </div>
                </div>
            </div>
        </div>
        <br><br>
    </div>
</template>

<script>
import { eventBus } from "../main";
export default {
    data() {
        return {
            product: {
                title: null,
                count: null,
                price: null,
                totalPrice: null,
                selectedImage: null
            },
            reachedMaxHere: 0
        };
    },
    methods: {
        onChange(e) {
            const file = e.target.files[0];
            this.product.selectedImage = URL.createObjectURL(file);
        },
        addProduct() {
            this.product.totalPrice = this.product.count * this.product.price;
            eventBus.$emit("productAdded", this.product);
            this.product = {
                title: null,
                count: null,
                price: null,
                totalPrice: null,
                selectedImage: null
            };
        }
    },
    created() {
        eventBus.$on("reachedMax", limit => {
            this.reachedMaxHere = limit;
        });
    }
};
</script>   

<style scoped>
.isdisable {
    color: currentColor;
    opacity: 0.1;
    text-decoration: none;
    cursor: not-allowed !important;
}
</style>


