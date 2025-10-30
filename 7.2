// Sample products
const products = [
  { id: 1, name: 'Laptop', price: 1200 },
  { id: 2, name: 'Smartphone', price: 800 },
  { id: 3, name: 'Headphones', price: 150 },
  { id: 4, name: 'Keyboard', price: 90 }
];

export default products;
import { configureStore } from '@reduxjs/toolkit';
import cartReducer from '../features/cart/cartSlice';

export const store = configureStore({
  reducer: {
    cart: cartReducer
  }
});
import { createSlice } from '@reduxjs/toolkit';

const initialState = {
  items: [] // {id, name, price, quantity}
};

const cartSlice = createSlice({
  name: 'cart',
  initialState,
  reducers: {
    addItem: (state, action) => {
      const existingItem = state.items.find(item => item.id === action.payload.id);
      if (existingItem) {
        existingItem.quantity += 1;
      } else {
        state.items.push({ ...action.payload, quantity: 1 });
      }
    },
    removeItem: (state, action) => {
      state.items = state.items.filter(item => item.id !== action.payload);
    },
    incrementQuantity: (state, action) => {
      const item = state.items.find(item => item.id === action.payload);
      if (item) item.quantity += 1;
    },
    decrementQuantity: (state, action) => {
      const item = state.items.find(item => item.id === action.payload);
      if (item && item.quantity > 1) {
        item.quantity -= 1;
      } else if (item && item.quantity === 1) {
        state.items = state.items.filter(i => i.id !== action.payload);
      }
    },
    clearCart: (state) => {
      state.items = [];
    }
  }
});

export const { addItem, removeItem, incrementQuantity, decrementQuantity, clearCart } = cartSlice.actions;
export default cartSlice.reducer;
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { incrementQuantity, decrementQuantity, removeItem, clearCart } from './cartSlice';

const Cart = () => {
  const cartItems = useSelector(state => state.cart.items);
  const dispatch = useDispatch();

  const total = cartItems.reduce((acc, item) => acc + item.price * item.quantity, 0);

  if (cartItems.length === 0) return <p>Your cart is empty.</p>;

  return (
    <div>
      <h2>Shopping Cart</h2>
      {cartItems.map(item => (
        <div key={item.id} style={{ borderBottom: '1px solid #ccc', padding: '10px' }}>
          <h3>{item.name}</h3>
          <p>Price: ${item.price}</p>
          <p>Quantity: {item.quantity}</p>
          <button onClick={() => dispatch(decrementQuantity(item.id))}>-</button>
          <button onClick={() => dispatch(incrementQuantity(item.id))}>+</button>
          <button onClick={() => dispatch(removeItem(item.id))} style={{ marginLeft: '10px', color: 'red' }}>Remove</button>
        </div>
      ))}
      <h3>Total: ${total.toFixed(2)}</h3>
      <button onClick={() => dispatch(clearCart())} style={{ marginTop: '10px' }}>Clear Cart</button>
    </div>
  );
};

export default Cart;
import React from 'react';
import products from '../data/products';
import { useDispatch } from 'react-redux';
import { addItem } from '../features/cart/cartSlice';

const ProductList = () => {
  const dispatch = useDispatch();

  return (
    <div>
      <h2>Products</h2>
      <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fill, minmax(200px, 1fr))', gap: '15px' }}>
        {products.map(product => (
          <div key={product.id} style={{ border: '1px solid #ddd', padding: '15px', borderRadius: '8px' }}>
            <h3>{product.name}</h3>
            <p>Price: ${product.price}</p>
            <button onClick={() => dispatch(addItem(product))}>Add to Cart</button>
          </div>
        ))}
      </div>
    </div>
  );
};

export default ProductList;
import React from 'react';
import products from '../data/products';
import { useDispatch } from 'react-redux';
import { addItem } from '../features/cart/cartSlice';

const ProductList = () => {
  const dispatch = useDispatch();

  return (
    <div>
      <h2>Products</h2>
      <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fill, minmax(200px, 1fr))', gap: '15px' }}>
        {products.map(product => (
          <div key={product.id} style={{ border: '1px solid #ddd', padding: '15px', borderRadius: '8px' }}>
            <h3>{product.name}</h3>
            <p>Price: ${product.price}</p>
            <button onClick={() => dispatch(addItem(product))}>Add to Cart</button>
          </div>
        ))}
      </div>
    </div>
  );
};

export default ProductList;
import React from 'react';
import ProductList from './components/ProductList';
import Cart from './features/cart/Cart';

function App() {
  return (
    <div style={{ padding: '20px', fontFamily: 'Arial, sans-serif' }}>
      <h1>🛍️ Shopping Cart</h1>
      <div style={{ display: 'flex', gap: '50px', flexWrap: 'wrap' }}>
        <div style={{ flex: '1 1 300px' }}>
          <ProductList />
        </div>
        <div style={{ flex: '1 1 300px' }}>
          <Cart />
        </div>
      </div>
    </div>
  );
}

export default App;
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';
import { Provider } from 'react-redux';
import { store } from './app/store';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <Provider store={store}>
    <App />
  </Provider>
);
