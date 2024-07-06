# StockSync

<img src="https://images.unsplash.com/photo-1535320903710-d993d3d77d29?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" width="300px" align="right">

This project is a stock market application built using Flask, a Python-based web framework. It includes functionalities for user registration, login, adding stocks to a wishlist, predicting stock prices, and fetching stock data. The application uses MongoDB for data storage, yfinance for fetching stock data, and scikit-learn for linear regression modeling.

### Main Components

1. **Flask Web Framework**
   - Flask is used to create the web application with various routes to handle user interactions.

2. **MongoDB**
   - MongoDB stores user data and wishlist data. `pymongo` is used to interact with MongoDB.
   - Collections:
     - `users_collection`: Stores user credentials.
     - `wishlist_collection`: Stores users' stock wishlists.

3. **YFinance**
   - `yfinance` library is used to fetch stock data for a given ticker.

4. **Scikit-Learn**
   - The `LinearRegression` model from scikit-learn is used to predict the next day's stock price based on historical data.

### Routes and Their Functions

1. **User Registration**
   - `@app.route('/register', methods=['GET', 'POST'])`
   - Handles user registration. Checks if the username already exists, then saves the new user if the username is unique.

2. **User Login**
   - `@app.route('/login', methods=['GET', 'POST'])`
   - Handles user login. Verifies user credentials and starts a session if the credentials are valid.

3. **Index Page**
   - `@app.route('/', methods=['GET'])`
   - The landing page of the application. Redirects to the dashboard if the user is logged in.

4. **Dashboard**
   - `@app.route('/dashboard', methods=['GET', 'POST'])`
   - Displays the user's dashboard with stock data and wishlist.

5. **Add to Wishlist**
   - `@app.route('/add_to_wishlist', methods=['POST'])`
   - Allows logged-in users to add a stock ticker to their wishlist.

6. **Logout**
   - `@app.route('/logout')`
   - Logs out the user by clearing the session.

7. **Predict Price**
   - `@app.route('/predict_price', methods=['POST'])`
   - Uses the `predict_next_day_price` function to predict the next day's stock price for a given ticker.

8. **Search Ticker**
   - `@app.route('/search_ticker', methods=['POST'])`
   - Fetches and returns stock data for a given ticker.

### Key Functions

1. **Predict Next Day Price**
   - `predict_next_day_price(ticker)`
   - Fetches the last month's stock data, trains a linear regression model, and predicts the next day's closing price.

2. **Search Ticker Data**
   - `search_ticker_data(ticker)`
   - Fetches the last 6 months of stock data and the current day's stock data. It also predicts the next day's closing price using the `predict_next_day_price` function.

### Prediction Model

- **Linear Regression Model**
  - The model is trained using the historical closing prices of a stock.
  - The date is converted to ordinal format to serve as the feature for the model.
  - The trained model is used to predict the next day's closing price based on the most recent date.

### Technologies Used

1. **Flask**: Web framework to handle routing and web requests.
2. **MongoDB**: Database to store user and wishlist information.
3. **YFinance**: Library to fetch historical stock data.
4. **Scikit-Learn**: Machine learning library to build the linear regression model.
5. **Gunicorn**: WSGI HTTP server for running the Flask app in production.
