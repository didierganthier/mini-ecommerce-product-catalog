# 📝 Mini E-commerce Product Catalog - Technical Challenge

**Tech Stack**: Next.js (App Router, latest version)

## ✅ Objective

Build a modern, performant, and user-friendly product catalog web app using **Next.js (App Router)**. This challenge tests your skills in Next.js routing, data fetching with React Server Components, state management, and creating a seamless e-commerce experience.

## 🛍️ Core Features

### 1. Homepage (Product Listing)
- Create a homepage (`/`) that displays a list of products fetched from a public API (e.g., [Fake Store API](https://fakestoreapi.com/)).
- Display for each product:
  - Image
  - Title
  - Short description
  - Price
- Use **React Server Components** for data fetching to prerender the product list.
- Implement **Incremental Static Regeneration (ISR)** or dynamic fetching with caching for optimal performance.

### 2. Product Details Page (Dynamic Route)
- Set up dynamic routing in the App Router (`app/products/[id]/page.js` or `app/products/[slug]/page.js`).
- Show full product details (image, title, description, price, category, etc.) when a user clicks a product.
- Fetch product data server-side using **React Server Components** or a **Route Handler** for dynamic data.

### 3. Shopping Cart
- Allow users to add products to a shopping cart from the homepage or product details page.
- Manage cart state using:
  - **React Context** or a lightweight state management library (e.g., Zustand or Jotai) for client-side state.
  - Optionally, persist cart data using `localStorage` or a server-side solution (e.g., via a Route Handler).
- Create a cart page (`/cart`) that displays:
  - Selected items
  - Quantities (with ability to update)
  - Total cost
- Include a button to clear the cart.

### 4. Basic Checkout (Optional but Encouraged)
- Add a checkout page (`/checkout`) with a form collecting:
  - Name
  - Address
  - Email
- Implement client-side validation (e.g., required fields, email format) using a library like `react-hook-form` or native HTML5 validation.
- Optionally, simulate a checkout API call using a **Route Handler** (`app/api/checkout/route.js`).

### 5. Responsive Layout & Styling
- Style the app using one of:
  - **CSS Modules**
  - **Tailwind CSS** (recommended for rapid development)
  - **styled-components** or **Emotion**
- Ensure the app is responsive and looks polished on desktop and mobile devices.
- Use **Next.js Image** component for optimized image loading.

## ⚙️ Technical Requirements
- Use **Next.js (latest version, App Router)** for:
  - File-based routing in the `app/` directory.
  - Data fetching with **React Server Components** (server-side by default) or **Route Handlers** for API routes.
  - Static generation with **ISR** or dynamic rendering as appropriate.
- Keep components **modular**, reusable, and well-organized.
- Fetch product data from a public API (e.g., Fake Store API) or a local JSON file.
- Use **TypeScript** (recommended but optional) for type safety.
- Optimize performance with:
  - **Next.js Image** for images.
  - **Suspense** or `loading.js` for streaming UI and loading states.
  - Proper caching strategies (e.g., `fetch` with `{ cache: 'force-cache' }` or `{ next: { revalidate: 3600 } }`).
- Ensure accessibility (e.g., semantic HTML, ARIA attributes where needed).

## 📦 Submission Details

### GitHub Repository
- Push your project to a **public GitHub repository**.
- Include a **README.md** with:
  - Project overview
  - Setup instructions (`npm install`, `npm run dev`)
  - API used (or instructions for local JSON)
  - Any bonus features implemented
- Maintain a clean commit history with descriptive messages.

### Live Demo
- Deploy the app to **Vercel** (recommended) or another hosting platform.
- Include the live URL in the README.

### Deadline
- Submit your GitHub repo link and live demo link within **[X days]** of receiving this brief.

## 🌟 Bonus (Optional)
Showcase your creativity with one or more of the following:
- Add **client-side filtering** or **search** for products (e.g., by category or price).
- Implement **smooth animations** (e.g., using Framer Motion or CSS transitions).
- Add a **dark mode** toggle using Next.js `useTheme` or CSS variables.
- Use **Server Actions** (if stable in Next.js 15) for form submissions or cart updates.
- Add **unit tests** for components or utilities using Jest or React Testing Library.

## ✅ Evaluation Criteria
- A clean, well-structured **Next.js App Router** project.
- Correct use of **React Server Components** and modern data fetching patterns.
- Effective state management for the cart and UI.
- Responsive, user-friendly design with attention to detail.
- Clear documentation and a professional GitHub repository.
- Performance optimization and accessibility considerations.

## 🚀 Example Starter Code

Below is a basic example of fetching products in the App Router:

```jsx
// app/page.js
async function fetchProducts() {
  const res = await fetch('https://fakestoreapi.com/products', {
    next: { revalidate: 3600 }, // ISR: revalidate every hour
  });
  return res.json();
}

export default async function Home() {
  const products = await fetchProducts();
  return (
    <div className="grid grid-cols-1 md:grid-cols-3 gap-4 p-4">
      {products.map((product) => (
        <div key={product.id} className="border p-4 rounded">
          <img src={product.image} alt={product.title} className="w-full h-48 object-cover" />
          <h2 className="text-lg font-bold">{product.title}</h2>
          <p className="text-sm">{product.description.slice(0, 100)}...</p>
          <p className="text-lg font-semibold">${product.price}</p>
          <a href={`/products/${product.id}`} className="text-blue-500">View Details</a>
        </div>
      ))}
    </div>
  );
}
```
## Resources
 - Next.js Documentation
 - Fake Store API
 - Vercel Deployment Guide
 - React Server Components

Good luck, and we’re excited to see your Next.js skills in action! 🚀

