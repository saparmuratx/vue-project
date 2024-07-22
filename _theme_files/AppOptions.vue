<script>
export default {
    data () {
        return {
            name: "Altair",
            status: false,
            products: [
                    {
                        "id": 1,
                        "name": "Wireless Headphones",
                        "description": "High-quality wireless headphones with noise cancellation",
                        "price": 99.99,
                        "vendor": "Bose"
                    },
                    {
                        "id": 2,
                        "name": "Smartwatch",
                        "description": "Sleek and feature-packed smartwatch with fitness tracking",
                        "price": 149.99,
                        "vendor": "Apple"
                    },
                    {
                        "id": 3,
                        "name": "Gaming Mouse",
                        "description": "Precision gaming mouse with customizable buttons and RGB lighting",
                        "price": 59.99,
                        "vendor": "Logitech"
                    },
                    {
                        "id": 4,
                        "name": "Portable Bluetooth Speaker",
                        "description": "Powerful and portable Bluetooth speaker with long battery life",
                        "price": 79.99,
                        "vendor": "JBL"
                    },
                    {
                        "id": 5,
                        "name": "Fitness Tracker",
                        "description": "Lightweight and water-resistant fitness tracker with heart rate monitoring",
                        "price": 49.99,
                        "vendor": "Fitbit"
                    }
            ]
        };
    },
}
</script>

<template>

    <div class="body-page">
        <h1>Vue Store innit? {{ name }}</h1>

        <p v-if="status"> User is active: {{ name }}</p>
        <p v-else> User is inactive {{ name }}</p>


        <h2>Product List</h2>

        <div class="product-grid">
            <div class="product-card" v-for="product in products">
                <h2>{{ product.name }}</h2>
                <p>Vendor: {{ product.vendor }}</p>
                <p>Price: {{ product.price.toFixed(2) }}$</p>
            </div>

        </div>
        <div> 
            <button @click="status = !status"> Toggle User </button>
        </div>
    </div>
</template>


<style>

.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 16px;
  padding: 20px;
}

.product-card {
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 16px;
  text-align: center;
  background-color: #2c3e50; /* Dark background color */
  color: #ecf0f1; /* Light text color */
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2); /* Optional shadow for depth */
}

.product-card h2 {
  margin: 0 0 10px; /* Space below the heading */
}

.product-card p {
  margin: 5px 0; /* Space between paragraphs */
}

</style>