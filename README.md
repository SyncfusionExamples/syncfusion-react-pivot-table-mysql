# MySQL Sales Analytics: Interactive Pivot Table Dashboard

**Bind and perform CRUD operations with interactive sales analytics using MySQL data**

**MySQL Pivot Table Dashboard** is a full-stack business intelligence sample that combines a **React + TypeScript frontend** with an **ASP.NET Core backend** connected to a **MySQL database**.

## 🔄 How It Works

The application uses **Syncfusion DataManager** to handle real-time CRUD operations through an interactive pivot table interface:

- **React Client**: Renders the Syncfusion pivot table UI and lets users visualize and analyze sales data.
- **DataManager**: Sends HTTP requests for read, insert, update, and delete operations.
- **ASP.NET Core Backend**: Exposes REST endpoints under the Sales controller for data operations.
- **MySQL Database**: Stores sales records and serves them to the UI through the backend.

The complete workflow is: user interaction in the pivot table → DataManager request → backend processing → MySQL query → UI refresh.

---

## 📋 Table of Contents

- [Quick Overview](#quick-overview)
- [Key Features](#key-features)
- [Technology Stack](#technology-stack)
- [Installation & Setup](#installation--setup)
- [Configuration](#configuration)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Troubleshooting](#troubleshooting)

---

## 🎯 Quick Overview

This sample provides an intuitive experience for exploring sales data without writing SQL. Users can:

- Visualize sales data by country, region, category, product, and salesperson
- Create, update, and delete records directly from the pivot table experience
- Drill into details and edit records inline
- Reorganize the pivot table layout with drag-and-drop fields

### Why This Stack?

- **Type-safe frontend** with React and TypeScript
- **Reliable backend** with ASP.NET Core and .NET 10
- **Fast, lightweight database access** with MySqlConnector
- **Professional UI** with Syncfusion pivot components

---

## ✨ Key Features

- Interactive pivot table with drag-and-drop field configuration
- End-to-end CRUD support for sales records
- Seamless frontend-to-backend data synchronization
- Responsive layout for desktop and tablet use
- Date and numeric formatting for sales analysis

---

## 🛠️ Technology Stack

### Frontend
| Technology | Version | Purpose |
|-----------|---------|---------|
| React | 19.2.7 | UI framework |
| TypeScript | ~6.0.2 | Type-safe JavaScript |
| Vite | 8.1.1 | Build and development tool |
| Syncfusion EJ2 | 34.1.32 | Pivot table and DataManager support |

### Backend
| Technology | Version | Purpose |
|-----------|---------|---------|
| .NET | 10.0 | Web API framework |
| ASP.NET Core | 10.0 | Backend application host |
| MySqlConnector | 2.6.1 | MySQL database connectivity |
| Syncfusion EJ2 | 34.1.32 | DataManager integration |

### Database
| Technology | Purpose |
|-----------|---------|
| MySQL | Primary relational database |
| MySqlConnector | .NET provider for MySQL |

---

## 📦 Installation & Setup

### Prerequisites

- .NET 10 SDK
- Node.js 18+ and npm
- MySQL 8.0 or later
- Ports 3306, 7086, and 5173 available

### Database Setup

1. Create a MySQL database:

```bash
mysql -u root -p
CREATE DATABASE salesdb;
```

2. Create the sales table:

```sql
CREATE TABLE salesdata (
  orderid INT AUTO_INCREMENT PRIMARY KEY,
  customername VARCHAR(255),
  region VARCHAR(255),
  country VARCHAR(255),
  productcategory VARCHAR(255),
  productname VARCHAR(255),
  orderdate DATE,
  quantity INT,
  unitprice DECIMAL(10,2),
  totalamount DECIMAL(10,2),
  salesperson VARCHAR(255)
);
```

3. Optionally seed the table with sample records.

### Backend Installation

1. Navigate to the backend folder:

```bash
cd PivotTable_MySQL.Server
```

2. Restore dependencies:

```bash
dotnet restore
```

3. Update the connection string in appsettings.json:

```json
{
  "ConnectionStrings": {
    "SalesDb": "Server=localhost;Port=3306;Database=salesdb;User Id=root;Password=YourPassword;"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*"
}
```

4. Build and run the backend:

```bash
dotnet build
dotnet run
```

The backend will run at https://localhost:7086.

### Frontend Installation

1. Navigate to the frontend folder:

```bash
cd pivottable_mysql.client
```

2. Install dependencies:

```bash
npm install
```

3. Start the development server:

```bash
npm run dev
```

The frontend will be available at http://localhost:5173.

---

## ⚙️ Configuration

### Backend Configuration

The backend reads the MySQL connection string from appsettings.json using the `SalesDb` key.

```json
{
  "ConnectionStrings": {
    "SalesDb": "Server=localhost;Port=3306;Database=salesdb;User Id=root;Password=YOUR_PASSWORD;"
  }
}
```

### Frontend Configuration

The Vite app is already configured for local development. If needed, update the API URL in the frontend code to match your backend host.

---

## 🚀 Getting Started

1. Start the MySQL server.
2. Create the database and table shown above.
3. Update the backend connection string.
4. Run the backend with `dotnet run`.
5. Run the frontend with `npm run dev`.
6. Open http://localhost:5173 in your browser.

You should see the pivot table load with sales data and allow CRUD operations.

---

## 📁 Project Structure

```text
syncfusion-react-pivot-table-mysql-database-binding-sample/
├── README.md
├── pivottable_mysql.client/
│   ├── package.json
│   ├── src/
│   │   ├── App.tsx
│   │   ├── main.tsx
│   │   └── App.css
│   └── vite.config.ts
└── PivotTable_MySQL.Server/
    ├── Program.cs
    ├── appsettings.json
    ├── Controllers/
    │   └── SalesController.cs
    └── PivotTable_MySQL.Server.csproj
```

### Key Files

- [pivottable_mysql.client/src/App.tsx](pivottable_mysql.client/src/App.tsx): Main React component and pivot configuration
- [PivotTable_MySQL.Server/Controllers/SalesController.cs](PivotTable_MySQL.Server/controllers/SalesController.cs): API endpoints for CRUD operations
- [PivotTable_MySQL.Server/Program.cs](PivotTable_MySQL.Server/Program.cs): Service registration and CORS setup
- [PivotTable_MySQL.Server/appsettings.json](PivotTable_MySQL.Server/appsettings.json): MySQL connection settings

---

## 🔧 Troubleshooting

### Common Issues

- **Cannot connect to the backend**: Make sure the ASP.NET Core app is running and CORS is enabled.
- **MySQL connection failed**: Verify the server, port, database name, and credentials in appsettings.json.
- **No data appears**: Confirm the `salesdata` table exists and contains records.
- **Frontend build error**: Run `npm install` again and ensure Node.js is up to date.

### Useful checks

```bash
mysql -u root -p -e "SHOW DATABASES;"
```

```bash
dotnet build
```

---

## 📜 License

This sample is intended for demo and development use. Please review the Syncfusion licensing terms before using it in production.
