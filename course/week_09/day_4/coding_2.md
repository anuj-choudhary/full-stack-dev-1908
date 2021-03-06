# Week 9 - Day 4

#### Coding B

Create an ecommerce app with redux and react and routing

Create the following routes:

- Home page : `/` 
- Add products page : `/addproducts`
- Cart Page: `/cart`
- Orders: `/orders`

It should have the following features:

Home Page: (`/`)

- See all the products of the company
- List by category (by default all should be shown)
- Add items to the cart
- A Shopping Cart on the right side of the page
- Shopping cart should not be visible if the cart is empty

Shopping Cart Component:

- Should list the products with 
    - Name
    - Qty
    - Price
- Add and Reduce qty. If qty is 1, and you remove the item should be removed from cart.
- If cart becomes empty the Shopping Cart component should be removed
- on confirm order, goto `/cart`

Add Product Page: (`/addproducts`)

- Admin should be able to Add/Remove/Edit/ products
- Create new category

Products should contain the following information:

- Name
- UUID
- Cost
- Description
- Category
- Image url / image (default image should be given)

Cart Page: `/cart`:

- Should list the products with all details
- Add and Reduce qty. If qty is 1, and you remove the item should be removed from cart.
- If cart becomes empty the Shopping Cart component should be removed
- Ask for user address, phone no, payment details etc
- Once order is confirmed, add confirmed orders to redux store

Orders Page: `/orders`

- Should list all the orders with product information in a meaningful way

Use Redux:

- to store the information of all the products
- to store cart details
- create seperate action reducer and store files
- Shopping Cart component should be given limited store and dispatch information
- Home Page component should not be given Cart information
- Confirmed orders list with all necessary details