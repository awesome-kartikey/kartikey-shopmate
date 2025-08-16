# Shopmate Application Architecture

## 1. Overview

Shopmate is a client-side Single Page Application (SPA) built using React and Create React App. It features a component-based architecture for UI rendering and uses React Router for navigation between different views (pages). The application currently simulates an e-commerce front-end for displaying products and a shopping cart, using static data.

## 2. Project Folder Structure

```
kartikey-shopmate/
├── README.md               # Main project documentation
├── package.json            # Project dependencies and scripts
├── public/                 # Static assets served directly
│   ├── index.html          # HTML entry point template
│   ├── manifest.json       # PWA configuration
│   ├── robots.txt          # Instructions for web crawlers
│   └── assets/             # Static assets like images
│       └── images/         # Product images, logos
└── src/                    # Main application source code
    ├── App.css             # Main application layout styles
    ├── App.js              # Root application component
    ├── index.css           # Global styles
    ├── index.js            # Application entry point (renders App)
    ├── assets/             # Assets used within the src code (e.g., logo import)
    ├── components/         # Reusable UI components
    │   ├── CartCard.css    # Styles for CartCard
    │   ├── CartCard.js     # Component for displaying items in the cart
    │   ├── Header.css      # Styles for Header
    │   ├── Header.js       # Site header/navigation component
    │   ├── index.js        # Exports components for easier imports
    │   ├── ProductCard.css # Styles for ProductCard
    │   └── ProductCard.js  # Component for displaying a single product
    ├── hooks/              # Custom React hooks
    │   └── useTitle.js     # Hook to set the document title
    ├── pages/              # Page-level components (views)
    │   ├── Cart.js         # Cart page component
    │   ├── Home.js         # Home page component
    │   └── index.js        # Exports pages for easier imports
    └── routes/             # Routing configuration
        └── AllRoutes.js    # Defines application routes using React Router
```

## 3. Major Components

- **`index.js`**: The entry point of the application. It renders the root `App` component into the DOM element with `id="root"` in `public/index.html`. It also wraps the `App` component with `BrowserRouter` from `react-router-dom` to enable client-side routing.
- **`App.js`**: The main application component. It renders the persistent `Header` component and the `AllRoutes` component, which conditionally renders the page components based on the current URL.
- **`Header.js` (`src/components/`)**: Displays the site logo, name, and navigation links (Home, Cart). It also shows a static cart item count. Uses `NavLink` for active link styling.
- **`ProductCard.js` (`src/components/`)**: A reusable component responsible for displaying a single product's image, name, price, and an "Add To Cart" button (currently non-functional). Used on the `Home` page.
- **`CartCard.js` (`src/components/`)**: A reusable component for displaying an item within the shopping cart, showing its image, name, price, and a "Remove" button (currently non-functional). Used on the `Cart` page.
- **`Home.js` (`src/pages/`)**: The component representing the home page. It fetches (currently uses hardcoded data) and displays a list of products using the `ProductCard` component. It also uses the `useTitle` hook.
- **`Cart.js` (`src/pages/`)**: The component representing the shopping cart page. It displays a list of items added to the cart (currently hardcoded) using the `CartCard` component. It also uses the `useTitle` hook.
- **`AllRoutes.js` (`src/routes/`)**: Defines the application's routing logic using `react-router-dom`. It maps URL paths (`/` and `/cart`) to their corresponding page components (`Home` and `Cart`).
- **`useTitle.js` (`src/hooks/`)**: A custom hook to abstract the logic for updating the `document.title` based on the current page.

## 4. Data Flow

1.  **Initialization**: `index.js` renders `App.js` wrapped in `BrowserRouter`.
2.  **Routing**: `App.js` renders `Header` and `AllRoutes`. `AllRoutes` listens to the URL provided by `BrowserRouter`.
3.  **Page Rendering**: Based on the current URL (e.g., `/`), `AllRoutes` renders the corresponding page component (e.g., `Home.js`).
4.  **Data Display (Static)**: The page component (`Home.js` or `Cart.js`) contains a hardcoded array of product data.
5.  **Component Mapping**: The page component maps over its data array and renders the appropriate presentational component (`ProductCard` or `CartCard`) for each item, passing the item data down as props.
6.  **UI Display**: The presentational components (`ProductCard`, `CartCard`) receive props and render the UI elements (image, name, price, buttons).
7.  **Navigation**: Clicking links in the `Header` component updates the URL via `react-router-dom`, causing `AllRoutes` to render the new corresponding page component, restarting the flow from step 3 for the new page.

_Note: Currently, there is no data flow related to adding/removing items from the cart as this functionality is not implemented. State is not shared between components dynamically._

## 5. Design Decisions

- **Create React App (CRA):** Chosen for its simplicity in setting up a modern React development environment with minimal configuration. Provides build optimizations, development server, and testing setup out-of-the-box.
- **React Router DOM v6:** Used for client-side routing to create a Single Page Application (SPA) experience. V6 offers a more intuitive API with hooks (`useRoutes`, `useNavigate`) and element-based route configuration (`<Routes>`, `<Route>`).
- **Component Structure:** Separation into `pages` (view controllers) and `components` (reusable UI elements) promotes modularity, reusability, and maintainability. `index.js` files within these folders act as barrel files for easier importing.
- **CSS Modules/Styling:** Basic CSS files colocated with components provide scoped styling (implicitly, by convention of importing). Global styles are handled in `index.css`. This approach is simple but could be scaled using CSS Modules, Styled Components, or utility-first CSS like Tailwind CSS for larger projects.
- **Custom Hooks (`useTitle`):** Encapsulating side effects like updating the document title into custom hooks makes components cleaner and the logic reusable.
- **Static Data:** Using hardcoded data initially allows focusing on UI development and component structure without the immediate need for backend setup or complex state management. This is typical for front-end prototypes or learning exercises.
