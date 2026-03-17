# 📚 Bulky Book Web

A full-featured **ASP.NET Core MVC** e-commerce web application for buying and managing books online. Built with clean architecture, secure authentication, and integrated Stripe payment processing — deployed on Azure.

---

## 📸 Screenshots

### 🏠 Home Page
<img width="1470" height="801" alt="Image" src="https://github.com/user-attachments/assets/316d9c4d-4a19-476f-b18f-4b5949da4d9b" />

---

### 🔐 Register and Login Page
<img width="1470" height="797" alt="Image" src="https://github.com/user-attachments/assets/41a08bdd-0e15-4cf4-9a41-c3d99fab40e6" />

<img width="1470" height="798" alt="Image" src="https://github.com/user-attachments/assets/b92a42fb-df75-4604-9f07-481041006559" />
---

### 📂 Category Management (Admin)
<img width="1470" height="805" alt="Image" src="https://github.com/user-attachments/assets/60c5ae48-09f1-485b-b33f-edc34515f7af" />

---

### 📖 Product Page
<img width="1470" height="803" alt="Image" src="https://github.com/user-attachments/assets/ad3a3e9f-5030-4d85-9868-7dddf682e61e" />

---

### 🏢 Company Page (Admin)
<img width="1470" height="801" alt="Image" src="https://github.com/user-attachments/assets/fbc15f47-8a09-4f8f-b155-df303ee96594" />

---

### 🛒 Shopping Cart
<img width="1470" height="801" alt="Image" src="https://github.com/user-attachments/assets/3a7769de-9cac-4df9-b367-dd223c78737b" />

---

### ✅ Order Confirmation
<img width="1470" height="809" alt="Image" src="https://github.com/user-attachments/assets/bb471b27-d3ea-492e-b888-08f95f07ff7f" />

---

### 💳 Checkout Page
<img width="1470" height="798" alt="Image" src="https://github.com/user-attachments/assets/af1eed1d-2576-414d-8fd5-775ce3c49911" />

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Framework | ASP.NET Core (.NET 7) MVC + Razor Pages |
| Language | C# |
| Database | SQL Server + Entity Framework Core |
| Auth | ASP.NET Core Identity |
| Payments | Stripe API |
| Email | SMTP / SendGrid |
| UI | Bootstrap 5, DataTables, Toastr |
| Cloud | Microsoft Azure |

---

## ✨ Features

### 🔐 Authentication & Authorization
- User registration and login with **ASP.NET Core Identity**
- Role-based access control: `Admin`, `Employee`, `Company User`, `Customer`
- Custom user fields (e.g., company name, street address, state, city)
- Session management
- Email notifications on registration and order updates

### 🛍️ Shopping & Orders
- Product browsing with detail views
- **Shopping cart** with quantity controls
- **Stripe-integrated checkout** with real payment processing
- Order tracking (Pending → Processing → Shipped → Delivered)
- Order management dashboard for admins

### 📦 Product & Inventory Management
- Full **CRUD** for products with multiple price tiers (individual, 50+, 100+)
- Product image upload and management
- Category management
- Company management (for B2B accounts with net-30 payment terms)

### 🏗️ Architecture & Patterns
- **Repository Pattern** + **Unit of Work** for clean data access
- **Entity Framework Core** with code-first migrations
- **Automatic database seeding** on startup
- Custom **Tag Helpers**
- Multi-project solution structure (DataAccess, Models, Utility, Web)

---

## 🗂️ Project Structure

```
Bulky/
├── Bulky.DataAccess/        # EF Core DbContext, Repositories, Migrations
│   ├── Data/
│   ├── Repository/
│   └── DbInitializer/
├── Bulky.Models/            # Domain models and ViewModels
├── Bulky.Utility/           # Constants, email sender, Stripe config
└── BulkyWeb/                # ASP.NET Core MVC Web App
    ├── Areas/
    │   ├── Admin/           # Controllers & Views for admin panel
    │   └── Customer/        # Controllers & Views for storefront
    └── wwwroot/             # Static assets (CSS, JS, images)
```

---

## ⚙️ Getting Started

### Prerequisites

- [.NET 7 SDK](https://dotnet.microsoft.com/download/dotnet/7.0)
- [SQL Server](https://www.microsoft.com/en-us/sql-server) or LocalDB
- [Stripe Account](https://stripe.com) (for payment testing)
- Visual Studio 2022 or VS Code

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/chintan712/Bulky.git
   cd Bulky
   ```

2. **Configure `appsettings.json`** in `BulkyWeb/`:
   ```json
   {
     "ConnectionStrings": {
       "DefaultConnection": "Server=.;Database=Bulky;Trusted_Connection=True;"
     },
     "Stripe": {
       "PublishableKey": "your_stripe_publishable_key",
       "SecretKey": "your_stripe_secret_key"
     },
   }
   ```

3. **Apply migrations & seed the database**
   ```bash
   cd BulkyWeb
   dotnet ef database update
   ```
   > The app auto-seeds roles and an admin user on first launch.

4. **Run the app**
   ```bash
   dotnet run
   ```
   Navigate to `https://localhost:{PORT}`

---

## 🚢 Deployment

This app is deployed on **Microsoft Azure App Service** with an **Azure SQL Database**.

Steps:
1. Publish from Visual Studio → Azure App Service
2. Set connection strings and Stripe keys in Azure App Service → Configuration
3. Run EF migrations against the Azure SQL instance

---

## 🙏 Acknowledgements

- [Bhrugen Patel / DotNetMastery](https://github.com/bhrugen)
- [Stripe Docs](https://stripe.com/docs)
- [Microsoft ASP.NET Core Docs](https://learn.microsoft.com/en-us/aspnet/core)
