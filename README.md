# McFarlane Tyres

### Overview

McFarlane Tyres is an iOS app I built to practice and showcase my Swift and SwiftUI skills. It originally started as a college graded unit project but I expanded it into a full working prototype of a tyre shop app to get more hands-on experience with application architecture.

Since this is a standalone project, it uses Apple's SwiftData for local storage to mock a backend database. This means anyone can download the project and run it immediately without needing to configure a server. 

The app handles three distinct user roles. Admins can manage stock and users, Staff can check orders and Customers can search for tyres, manage their basket and complete a checkout flow. I focused on writing clean object-oriented code throughout the project. It includes custom salted SHA256 password hashing, dynamic search filtering and automatic data seeding so the app is populated with dummy data on the first launch.

---

### Features & Highlights

- **Search Functionality**: Users can filter tyres by width, profile, rim size and speed rating
- **Basket & Checkout**: Tyres can be added to a basket, quantities adjusted and orders placed seamlessly
- **Order Management**: Orders are automatically created and stored with custom details like fitting dates and vehicle registration
- **Role-Based Views**: The app adapts based on user role showing tailored views for Admin, Staff and Customers
- **Local Persistence**: All data is stored locally using SwiftData to simulate a persistent database
- **Security**: Passwords are securely hashed using a custom salted SHA256 algorithm implementation
- **Data Seeding**: Preloaded mock tyres and user accounts make the app usable right from the start

---

### Local Environment Setup

Before running the app, make sure the in-app SwiftData store is properly initialised. This usually happens automatically the first time you launch the app:

1. Check that `TyreManager` and `UserManager` are set up to call `loadDefaultTyres()` and `loadDefaultUsers()` if no data exists
2. Launch the app – the seeding and setup processes are triggered in the `HomeView` using `.onAppear`
3. If the data doesn't initialise, perform a clean build (`Cmd + Shift + K`) in Xcode, delete the app from your simulator or device and reinstall it
    
---

### Running the Application

To run the app in Xcode:

1. Open the project in Xcode
2. Build and run the app on either a simulator or a physical device
3. Navigate through the Home, Search, Basket and Checkout interfaces

_Note: This app was primarily designed and tested on an iPhone 16 Pro Max_

---

### Test Accounts

The following seeded test accounts are available to explore the different role views:

**Admin** - Email: `admin`  
- Password: `password`  

**Staff** - Email: `staff1`  
- Password: `password`  

**Customer** - Email: `cust1`  
- Password: `password`  

_Note: Additional accounts can be found in the `DefaultUserData.swift` file_

---

### Project Structure

- `Managers/` – Logic handlers: `BasketManager`, `OrderManager`, `TyreManager`, `UserManager`  
- `Models/` – Core data models: `User`, `Tyre`, `BasketItem`, `Order`, `OrderLine`  
- `Views/` – SwiftUI screens and UI components  
- `Shared/` – Reusable UI components: cards, taskbars and other common elements  
- `Seeding/` – Contains `DefaultTyreData` and `DefaultUserData` to populate the initial mock data

---

### Screenshots

#### Home
The main dashboard offering quick access to all core sections of the app. Users can easily navigate to search tyres, view their basket or access their account from this view

<div>
  <img src="Screenshots/Home.png" alt="Home View" width="250"/>
</div>

#### Search & Basket  
A streamlined interface for searching tyres using detailed filters such as width, profile, rim size and speed rating. Users can add tyres to their basket which triggers a confirmation pop-up and haptic feedback.
The basket view adapts depending on whether the user is logged in or logged out allowing logged-in users to manage their selected items, modify quantities and proceed to checkout while guests have a limited view.

<div>
  <img src="Screenshots/Search_and_add_to_basket.png" alt="Search and Add to Basket" width="250"/>
  <img src="Screenshots/Basket_logged_out.png" alt="Basket Logged Out" width="250"/>
  <img src="Screenshots/Basket_logged_in.png" alt="Basket Logged In" width="250"/>
</div>

#### Checkout  
A clear, step-by-step process for finalising tyre orders. This view guides users through confirming order details, selecting fitting dates and completing payment ensuring a smooth user experience

<div>
  <img src="Screenshots/Checkout_view.png" alt="Checkout View" width="250"/>
  <img src="Screenshots/Order_confirmation.png" alt="Order Confirmation" width="250"/>
</div>

#### Customer Account  
A personalised view where customers can review their order history, track current orders and change passwords

<div>
  <img src="Screenshots/Customer_settings.png" alt="Customer Settings" width="250"/>
  <img src="Screenshots/Orders.png" alt="Orders" width="250"/>
</div>

#### Staff Account  
A personalised view extending the customer account. Staff can view orders but do not have access to sensitive administrative controls

<div>
  <img src="Screenshots/Staff_settings.png" alt="Staff Settings" width="250"/>
  <img src="Screenshots/All_orders.png" alt="All Orders" width="250"/>
</div>

#### Admin Dashboard  
A comprehensive control panel for administrators featuring full system management capabilities. Admins can oversee users, add new users while assigning roles, manage tyre inventories and configure system settings to maintain smooth operations

<div>
  <img src="Screenshots/Admin_settings.png" alt="Admin Settings" width="250"/>
  <img src="Screenshots/Manage_tyres.png" alt="Manage Tyres" width="250"/>
  <img src="Screenshots/Add_user.png" alt="Add User" width="250"/>
</div>
