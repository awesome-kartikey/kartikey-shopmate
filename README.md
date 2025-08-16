# Shopmate - Simple React Shopping Cart

Shopmate is a basic front-end web application built with React that simulates a simple e-commerce experience. Users can browse a list of products on the home page and view selected items (currently static) on a dedicated cart page. This project serves as a foundational example of using React, React Router, and basic component structure for an e-commerce UI.

## Features

- **Product Listing:** Displays a list of products with images, names, and prices on the homepage.
- **Shopping Cart Page:** A separate page to display items added to the cart.
- **Basic Routing:** Uses React Router v6 for navigation between the Home and Cart pages.
- **Component-Based Structure:** Organized into reusable components (Header, ProductCard, CartCard).
- **Custom Hook:** Includes a `useTitle` hook to dynamically update the page title.



## Tech Stack

- **Frontend:**
  - React (v18.2.0)
  - React DOM (v18.2.0)
  - React Router DOM (v6.4.0)
  - CSS (Standard CSS files per component and globally)
- **Build Tool:** Create React App (react-scripts v5.0.1)
- **Package Manager:** npm

## Setup Instructions

1.  **Clone the repository:**

    ```bash
    git clone <your-repository-url>
    cd kartikey-shopmate
    ```

2.  **Install dependencies:**

    ```bash
    npm install
    ```

3.  **Run the development server:**

    ```bash
    npm start
    ```

    This runs the app in development mode. Open [http://localhost:3000](http://localhost:3000) to view it in your browser. The page will reload when you make changes.

4.  **Build for production:**
    ```bash
    npm run build
    ```
    This builds the app for production to the `build` folder. It optimizes the build for the best performance.

## Usage

After starting the development server (`npm start`):

1.  Navigate to `http://localhost:3000` in your browser.
2.  You will see the **Home** page displaying a list of products.
3.  Click the **Cart** link in the header or navigate to `http://localhost:3000/cart` to view the **Cart** page.
