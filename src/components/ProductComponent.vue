<template>
  <div>
    <div class="product">
      <div class="product-details">
        <h1 class="product-title">Levi's Classic Jeans</h1>
        <p class="product-description">
          Discover the timeless style and quality of Levi's Classic Jeans. These jeans are designed for comfort and durability, making them the perfect addition to your wardrobe.
        </p>
        <p class="product-price">$49.99</p>
      </div>
      <iframe
          src="http://localhost:8080/verification.html?brand=Levis&token=0xdc5669475b436a23330cb74934a6dd057c51d274&onchainid=1"
          width="300"
          height="140"
          frameborder="1"
      ></iframe>
      <div class="product-actions">
        <button class="btn btn-buy" @click="buy(1)">Buy Now</button>
        <button class="btn btn-add-to-cart" @click="addToCart">Add to Cart</button>
        <button class="btn btn-wishlist" @click="addToWishlist">Add to Wishlist</button>
      </div>
    </div>
    <div class="product">
      <div class="product-details">
        <h1 class="product-title">Levi's Classic Jeans</h1>
        <p class="product-description">
          Discover the timeless style and quality of Levi's Classic Jeans. These jeans are designed for comfort and durability, making them the perfect addition to your wardrobe.
        </p>
        <p class="product-price">$49.99</p>
      </div>
      <iframe
          src="http://localhost:8080/verification.html?brand=Levis&token=0xdc5669475b436a23330cb74934a6dd057c51d274&onchainid=2"
          width="300"
          height="140"
          frameborder="1"
      ></iframe>
      <div class="product-actions">
        <button class="btn btn-buy" @click="buy(2)">Buy Now</button>
        <button class="btn btn-add-to-cart" @click="addToCart">Add to Cart</button>
        <button class="btn btn-wishlist" @click="addToWishlist">Add to Wishlist</button>
      </div>
    </div>
    <div class="product">
      <div class="product-details">
        <h1 class="product-title">Levi's Classic Jeans</h1>
        <p class="product-description">
          Discover the timeless style and quality of Levi's Classic Jeans. These jeans are designed for comfort and durability, making them the perfect addition to your wardrobe.
        </p>
        <p class="product-price">$49.99</p>
      </div>
      <iframe
          src="http://localhost:8080/verification.html?brand=Levis&token=0xdc5669475b436a23330cb74934a6dd057c51d274&onchainid=3"
          width="300"
          height="140"
          frameborder="1"
      ></iframe>
      <div class="product-actions">
        <button class="btn btn-buy" @click="buy(3)">Buy Now</button>
        <button class="btn btn-add-to-cart" @click="addToCart">Add to Cart</button>
        <button class="btn btn-wishlist" @click="addToWishlist">Add to Wishlist</button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  methods: {
    async buy(id) {
      try {
        const res = await axios.post("http://localhost:4004/api/verify/usage",
            JSON.parse(localStorage.getItem(`iframe-data-${id}`)));
        if (res) {
          alert("You successfully bought this product");
        }
      } catch (err) {
        console.log(err);
        alert(`Error: ${err.message}`);
      }
    },
    addToCart() {
      // Implement add to cart logic here
      console.log("Added to Cart: Levi's Classic Jeans");
    },
    addToWishlist() {
      // Implement add to wishlist logic here
      console.log("Added to Wishlist: Levi's Classic Jeans");
    },
  },
  created() {
    window.addEventListener('message', (event) => {
      if (event.data.type === 'tw_signatureVerified') {
        const data = event.data.data;
        localStorage.setItem(`iframe-data-${data.onchainId}`, JSON.stringify(data));
      }
    });
  }
};
</script>

<style scoped>
.product {
  display: flex;
  justify-content: space-between;
  margin: 20px;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f5f5f5;
}

.product-details {
  flex: 1;
}

.product-title {
  font-size: 24px;
  margin: 0;
}

.product-description {
  font-size: 16px;
  margin: 10px 0;
}

.product-price {
  font-size: 18px;
  font-weight: bold;
}

.product-actions {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}

.btn {
  background-color: #4daf4a;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px;
}

.btn-buy {
  background-color: #4daf4a;
}

.btn-add-to-cart {
  background-color: #428bca;
}

.btn-wishlist {
  background-color: #f0ad4e;
}

.btn:hover {
  background-color: #449a44;
}
</style>
