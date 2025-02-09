# Direct-Dil-Se-Akash-Shop
Direct Dil Se Akash Shop "फिटनेस और न्यूट्रिशन का आपका 24x7 साथी! पर्सनलाइज्ड डाइट प्लान्स, फिटनेस टिप्स, और हेल्दी लाइफस्टाइल गाइड के लिए जुड़ें।"
const express = require("express");
const mongoose = require("mongoose");
const cors = require("cors");
const Razorpay = require("razorpay");

const app = express();
app.use(express.json());
app.use(cors());

mongoose.connect("YOUR_MONGO_URI", { useNewUrlParser: true, useUnifiedTopology: true });

const ProductSchema = new mongoose.Schema({
  name: String,
  price: Number,
  image: String,
});
const Product = mongoose.model("Product", ProductSchema);

app.get("/api/products", async (req, res) => {
  const products = await Product.find();
  res.json(products);
});

app.post("/api/payment", async (req, res) => {
  const razorpay = new Razorpay({ key_id: "YOUR_KEY", key_secret: "YOUR_SECRET" });
  const payment = await razorpay.orders.create({ amount: req.body.amount * 100, currency: "INR" });
  res.json(payment);
});

app.listen(5000, () => console.log("Server running on port 5000"));
import React, { useEffect, useState } from "react";
import axios from "axios";

function App() {
  const [products, setProducts] = useState([]);

  useEffect(() => {
    axios.get("https://yourapi.com/api/products").then((response) => setProducts(response.data));
  }, []);

  return (
    <div>
      <h1>Products</h1>
      <ul>
        {products.map((product) => (
          <li key={product._id}>
            <img src={product.image} alt={product.name} width="100" />
            <h2>{product.name}</h2>
            <p>₹{product.price}</p>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default App;
import React from "react";
import { NavigationContainer } from "@react-navigation/native";
import { createStackNavigator } from "@react-navigation/stack";
import LoginScreen from "./screens/LoginScreen";
import ProductList from "./screens/ProductList";
import PaymentScreen from "./screens/PaymentScreen";

const Stack = createStackNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Login" component={LoginScreen} />
        <Stack.Screen name="Products" component={ProductList} />
        <Stack.Screen name="Payment" component={PaymentScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
cd android
