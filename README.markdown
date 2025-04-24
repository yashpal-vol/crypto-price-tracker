# Crypto Price Tracker

## Overview

This project is a web-based application that tracks cryptocurrency prices in real-time. It displays key metrics such as current price, hourly/daily/weekly percentage changes, market cap, 24-hour volume, and circulating supply for assets like Bitcoin, Ethereum, Tether, and more. The app features a sortable table and a sparkline chart for visualizing 7-day price trends.

## Setup Instructions

1. **Clone the Repository**:

   ```
   git clone <https://github.com/yashpal-vol/crypto-price-tracker/>
   cd CryptoPriceTracker
   ```

2. **Open the Application**:

   - Locate the `crypto.html` file in the repository.
   - Open `crypto.html` in a modern web browser (e.g., Chrome, Firefox, Edge) by double-clicking the file or using the `file://` protocol.
   - No additional installation or server setup is required, as all dependencies are loaded via CDNs.

3. **Usage**:

   - The table will automatically load with initial data from the CoinGecko API.
   - Real-time updates will begin via the Binance WebSocket.
   - Use the "Sort by 24h Gain" or "Sort by Rank" button to toggle sorting of the table.

## Tech Stack and Architecture

### Tech Stack

- **HTML5**: Structure of the application.
- **React (18.x)**: For building the UI components and managing state.
- **Redux (4.2.0)**: State management for handling asset data and updates.
- **React-Redux (8.0.5)**: Connects React components to the Redux store.
- **Tailwind CSS**: For responsive styling.
- **Babel**: For JSX transformation in the browser.
- **CoinGecko API**: Fetches initial market data (price, market cap, etc.).
- **Binance WebSocket**: Provides real-time price updates.

### Architecture

- **Single HTML File (**`crypto.html`**)**:
  - Contains all the application logic, including React components, Redux store setup, and API/WebSocket integration.
  - Dependencies are loaded via CDNs in the `<head>` section.
- **State Management**:
  - Redux manages the state of assets in a single store.
  - The `cryptoReducer` handles actions like `UPDATE_PRICE` to update asset data.
  - State is persisted in `localStorage` for browser refreshes.
- **Data Flow**:
  - Initial data is fetched from the CoinGecko API using a `fetch` call in a `useEffect` hook.
  - Real-time updates are received via a WebSocket connection to Binance, dispatching updates to the Redux store.
  - The `CryptoTable` component uses `useSelector` to access the state and `useDispatch` to dispatch updates.
- **Components**:
  - `Sparkline`: A functional component that renders a 7-day price trend chart using SVG.
  - `CryptoTable`: The main component rendering the table, handling sorting, and displaying data.
- **Styling**:
  - Tailwind CSS provides responsive and utility-first styling, applied directly via `className` attributes.

## Demo

Below is a demo showcasing the UI layout, live updates, state flow, and thought process behind the implementation:
(https://drive.google.com/file/d/1HLtoZkSNO0AQFQ8CzltsKTcb4Oo3ODoe/view?usp=sharing)

## Features

- Real-time price updates via Binance WebSocket.
- Initial data fetched from CoinGecko API.
- Sortable table by rank or 24-hour percentage gain.
- Visual 7-day price trend using a custom Sparkline component.
- Responsive design with Tailwind CSS.

## Notes

- The application is client-side only; no server setup is needed.
- Error handling is minimal; ensure a stable internet connection for data updates.
- The WebSocket connection may occasionally disconnect; the app will attempt to reconnect automatically.

## License

This project is for educational purposes only and is not licensed for commercial use.