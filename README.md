# GolfBayAi
Merch
#Python code for creating the database tables
import sqlite3

#Create database connection
conn = sqlite3.connect('store.db')

#Create Products Table
conn.execute('''CREATE TABLE Products
             (ProductID INTEGER PRIMARY KEY, 
             Name TEXT, 
             Description TEXT, 
             Price REAL, 
             StockQuantity INTEGER, 
             CategoryID INTEGER, 
             FOREIGN KEY (CategoryID) REFERENCES Categories(CategoryID))''')

#Create Categories Table
conn.execute('''CREATE TABLE Categories
             (CategoryID INTEGER PRIMARY KEY, 
             CategoryName TEXT)''')

#Create Customers Table
conn.execute('''CREATE TABLE Customers
             (CustomerID INTEGER PRIMARY KEY, 
             FirstName TEXT, 
             LastName TEXT, 
             Email TEXT, 
             Password TEXT, 
             Address TEXT, 
             Phone TEXT)''')

#Create Orders Table
conn.execute('''CREATE TABLE Orders
             (OrderID INTEGER PRIMARY KEY, 
             CustomerID INTEGER, 
             OrderDate TEXT, 
             TotalAmount REAL, 
             FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID))''')

#Create OrderItems Table
conn.execute('''CREATE TABLE OrderItems
             (OrderItemID INTEGER PRIMARY KEY, 
             OrderID INTEGER, 
             ProductID INTEGER, 
             Quantity INTEGER, 
             Subtotal REAL, 
             FOREIGN KEY (OrderID) REFERENCES Orders(OrderID), 
             FOREIGN KEY (ProductID) REFERENCES Products(ProductID))''')

#Commit changes and close connection
conn.commit()
conn.close()

#HTML code for displaying the database tables on a website
<html>
    <head>
        <title>Online Merch Store Database</title>
    </head>
    <body>
        <h1>Online Merch Store Database</h1>
        <h2>Products Table</h2>
        <table>
            <tr>
                <th>ProductID</th>
                <th>Name</th>
                <th>Description</th>
                <th>Price</th>
                <th>StockQuantity</th>
                <th>CategoryID</th>
            </tr>
        </table>
        <h2>Categories Table</h2>
        <table>
            <tr>
                <th>CategoryID</th>
                <th>CategoryName</th>
            </tr>
        </table>
        <h2>Customers Table</h2>
        <table>
            <tr>
                <th>CustomerID</th>
                <th>FirstName</th>
                <th>LastName</th>
                <th>Email</th>
                <th>Password</th>
                <th>Address</th>
                <th>Phone</th>
            </tr>
        </table>
        <h2>Orders Table</h2>
        <table>
            <tr>
                <th>OrderID</th>
                <th>CustomerID</th>
                <th>OrderDate</th>
                <th>TotalAmount</th>
            </tr>
        </table>
        <h2>OrderItems Table</h2>
        <table>
            <tr>
                <th>OrderItemID</th>
                <th>OrderID</th>
                <th>ProductID</th>
                <th>Quantity</th>
                <th>Subtotal</th>
            </tr>
        </table>
    </body>
</html>
