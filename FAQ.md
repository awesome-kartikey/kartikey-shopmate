# Frequently Asked Questions (FAQ)

### Q1: How do I set up and run the project locally?

**A:** Follow these steps:

1.  Clone the repository: `git clone <your-repository-url>`
2.  Navigate into the project directory: `cd kartikey-shopmate`
3.  Install dependencies: `npm install`
4.  Start the development server: `npm start`
5.  Open your browser to `http://localhost:3000`.

### Q2: Is the "Add to Cart" or "Remove" functionality working?

**A:** No. Currently, the buttons for adding items to the cart (`ProductCard.js`) and removing items (`CartCard.js`) are present in the UI but do not have implemented logic. The product data displayed on both the Home and Cart pages is static and hardcoded within the respective page components (`Home.js`, `Cart.js`).

### Q3: How is navigation handled between pages?

**A:** The project uses `react-router-dom` (version 6) for client-side routing.

- The `src/routes/AllRoutes.js` file defines the available routes (`/` for Home and `/cart` for Cart).
- The `Header` component uses `NavLink` from `react-router-dom` to provide navigation links.
- The main `App.js` component renders the `Header` and the `AllRoutes` component to display the correct page based on the URL.

### Q4: How is the application state managed?

**A:** Currently, there is no explicit state management library (like Redux or Context API with reducers) implemented for the cart state or product data. The product lists are hardcoded directly within the `Home.js` and `Cart.js` page components. The cart item count in the header is also static. Implementing dynamic cart functionality would require adding state management.

### Q5: Where does the product data come from?

**A:** The product data (including names, prices, and image paths) is currently hardcoded as arrays of objects within the `Home.js` and `Cart.js` components. In a real-world application, this data would typically be fetched from a backend API.

### Q6: How is styling done in this project?

**A:** Styling is primarily done using standard CSS.

- Global styles are defined in `src/index.css`.
- App-level layout styles are in `src/App.css`.
- Each component (`Header`, `ProductCard`, `CartCard`) has its own corresponding CSS file (`Header.css`, `ProductCard.css`, `CartCard.css`) which is imported directly into the component's JavaScript file.

### Q7: What is the purpose of the `useTitle` hook?

**A:** `src/hooks/useTitle.js` is a custom React hook created to simplify the process of setting the document's title (the text shown in the browser tab). It takes a title string as an argument and uses the `useEffect` hook to update `document.title` whenever the title prop changes or the component using the hook mounts. This helps keep title management logic separate and reusable.

### Q8: Can I contribute to this project?

**A:** Yes, contributions are usually welcome. Please refer to the `Contributing` section in the [README.md](README.md) file for guidelines on how to contribute.
