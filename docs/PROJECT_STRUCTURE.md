# Prime Sewing Machine - Project Structure

## Directory Layout

```
prime-sewing-machine/
│
├── public/
│   ├── logo.svg
│   ├── favicon.ico
│   ├── images/
│   │   ├── hero/
│   │   ├── products/
│   │   ├── testimonials/
│   │   └── services/
│   └── icons/
│
├── src/
│   ├── components/
│   │   ├── Header.js
│   │   ├── Navigation.js
│   │   ├── Footer.js
│   │   ├── ProductCard.js
│   │   ├── ProductGrid.js
│   │   ├── QuotationForm.js
│   │   ├── OrderForm.js
│   │   ├── ShoppingCart.js
│   │   ├── WhatsAppWidget.js
│   │   ├── MapComponent.js
│   │   └── AIProductDescription.js
│   │
│   ├── pages/
│   │   ├── Home.js
│   │   ├── Products.js
│   │   ├── ProductDetail.js
│   │   ├── Quotation.js
│   │   ├── Cart.js
│   │   ├── Checkout.js
│   │   ├── Orders.js
│   │   ├── Services.js
│   │   ├── Contact.js
│   │   ├── About.js
│   │   └── Dashboard.js
│   │
│   ├── styles/
│   │   ├── globals.css
│   │   ├── variables.css
│   │   ├── components.css
│   │   └── responsive.css
│   │
│   ├── utils/
│   │   ├── api.js
│   │   ├── auth.js
│   │   ├── payment.js
│   │   └── helpers.js
│   │
│   ├── context/
│   │   ├── AuthContext.js
│   │   ├── CartContext.js
│   │   └── OrderContext.js
│   │
│   ├── hooks/
│   │   ├── useAuth.js
│   │   ├── useCart.js
│   │   └── useFetch.js
│   │
│   ├── App.js
│   └── index.js
│
├── backend/
│   ├── server.js
│   ├── config/
│   │   ├── database.js
│   │   └── payment.js
│   │
│   ├── models/
│   │   ├── User.js
│   │   ├── Product.js
│   │   ├── Order.js
│   │   ├── Quotation.js
│   │   └── Review.js
│   │
│   ├── routes/
│   │   ├── auth.js
│   │   ├── products.js
│   │   ├── orders.js
│   │   ├── quotations.js
│   │   ├── payments.js
│   │   └── admin.js
│   │
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── productController.js
│   │   ├── orderController.js
│   │   ├── quotationController.js
│   │   └── paymentController.js
│   │
│   ├── middleware/
│   │   ├── auth.js
│   │   ├── validation.js
│   │   └── errorHandler.js
│   │
│   └── utils/
│       ├── emailService.js
│       ├── pdfGenerator.js
│       └── aiDescriptions.js
│
├── docs/
│   ├── API_DOCUMENTATION.md
│   ├── SETUP.md
│   ├── DEPLOYMENT.md
│   └── WIREFRAMES.md
│
├── .env.example
├── .gitignore
├── package.json
├── package-lock.json
├── README.md
└── BRAND_GUIDELINES.md
```

## Technology Stack

### Frontend
- **Framework:** React.js / Next.js
- **Styling:** CSS3 + Tailwind CSS
- **State Management:** Context API / Redux
- **HTTP Client:** Axios
- **Payment UI:** Stripe/Paystack SDK
- **Maps:** Google Maps API
- **Charts:** Chart.js / Recharts (for dashboard)

### Backend
- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB
- **Authentication:** JWT (JSON Web Tokens)
- **Validation:** Joi / Express Validator
- **Payment Gateway:** MTN Mobile Money, Airtel Money API
- **Email Service:** Nodemailer
- **PDF Generation:** PDFKit / jsPDF
- **AI Integration:** OpenAI API (for product descriptions)

### Deployment
- **Frontend:** Vercel / Netlify
- **Backend:** Heroku / Railway / DigitalOcean
- **Database:** MongoDB Atlas (Cloud)
- **Storage:** Cloudinary (Images)

---

## Key Features Implementation

### 1. Product Catalog
- Database of sewing machines
- AI-generated descriptions
- High-quality images (gallery)
- Specifications & pricing
- Customer reviews & ratings

### 2. E-Commerce
- Shopping cart functionality
- Product filtering & search
- Wishlist feature
- Product comparison

### 3. Quotation System
- Custom quote request form
- Email confirmation
- Quote history
- Quote to order conversion

### 4. Order Management
- Full payment or deposit options
- Order tracking
- Delivery management
- Receipt generation (PDF)
- Order history

### 5. Payment Integration
- MTN Mobile Money
- Airtel Money
- Bank transfer (optional)
- Deposit payment option

### 6. Admin Dashboard
- Product management
- Order management
- Quotation management
- Revenue analytics
- Customer management
- User activity logs

### 7. Customer Support
- WhatsApp integration (both numbers)
- Contact form
- Live chat (optional)
- FAQ section

### 8. Location & Services
- Google Map (Kiyembe City Complex location)
- Service descriptions (repair, training, warranty)
- Tailoring school partnerships

### 9. User Accounts
- Registration / Login
- Profile management
- Order history
- Wishlist
- Saved addresses

### 10. Notifications
- Email confirmations (orders, quotations)
- Receipt generation
- Order status updates
- Promotional emails

---

## Database Models

### User Model
```
{
  id,
  fullName,
  email,
  phone,
  password (hashed),
  address,
  city,
  userType (customer/admin),
  createdAt,
  updatedAt
}
```

### Product Model
```
{
  id,
  name,
  description (AI-generated),
  category,
  price,
  specifications,
  images [],
  stock,
  rating,
  reviews [],
  createdAt,
  updatedAt
}
```

### Order Model
```
{
  id,
  userId,
  items [],
  totalPrice,
  paymentMethod,
  paymentStatus (pending/partial/completed),
  depositAmount,
  remainingAmount,
  deliveryLocation,
  deliveryCharge,
  orderStatus (pending/processing/shipped/delivered),
  trackingNumber,
  notes,
  createdAt,
  updatedAt
}
```

### Quotation Model
```
{
  id,
  userId,
  items [],
  estimatedPrice,
  validUntil,
  status (pending/accepted/converted to order/expired),
  notes,
  createdAt,
  updatedAt
}
```

### Review Model
```
{
  id,
  productId,
  userId,
  rating (1-5),
  title,
  comment,
  helpful (count),
  createdAt,
  updatedAt
}
```

---

## API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout
- `POST /api/auth/forgot-password` - Password reset

### Products
- `GET /api/products` - Get all products
- `GET /api/products/:id` - Get single product
- `GET /api/products/search?q=query` - Search products
- `POST /api/products` - Create product (admin)
- `PUT /api/products/:id` - Update product (admin)
- `DELETE /api/products/:id` - Delete product (admin)

### Orders
- `POST /api/orders` - Create order
- `GET /api/orders/:id` - Get order details
- `GET /api/orders` - Get user orders
- `PUT /api/orders/:id/status` - Update order status
- `GET /api/orders/:id/receipt` - Generate receipt

### Quotations
- `POST /api/quotations` - Create quotation
- `GET /api/quotations/:id` - Get quotation
- `PUT /api/quotations/:id/convert` - Convert to order
- `DELETE /api/quotations/:id` - Delete quotation

### Payments
- `POST /api/payments/mobile-money` - Process mobile money payment
- `POST /api/payments/verify` - Verify payment
- `GET /api/payments/:id/status` - Check payment status

### Admin
- `GET /api/admin/dashboard` - Dashboard analytics
- `GET /api/admin/orders` - All orders
- `GET /api/admin/users` - All users
- `GET /api/admin/reports` - Generate reports

---

## Development Timeline

### Week 1: Foundation & Design
- ✅ Brand guidelines & logo
- ✅ Wireframes & mockups
- ✅ Project structure setup
- ✅ Database schema design

### Week 2: Backend & Frontend Development
- ✅ Backend API setup
- ✅ Database connection
- ✅ Frontend components
- ✅ Authentication system
- ✅ Payment integration setup

### Week 3: Integration & Testing
- ✅ Frontend-backend integration
- ✅ WhatsApp & Maps integration
- ✅ Testing (unit, integration)
- ✅ Bug fixes & optimization
- ✅ Deployment

---

## Environment Variables (.env)

```
# Database
MONGODB_URI=your_mongodb_connection_string

# Authentication
JWT_SECRET=your_jwt_secret
JWT_EXPIRE=7d

# Payment Gateway
MTN_API_KEY=your_mtn_api_key
MTN_API_SECRET=your_mtn_secret
AIRTEL_API_KEY=your_airtel_api_key

# Email Service
SMTP_HOST=your_email_host
SMTP_PORT=587
SMTP_USER=your_email
SMTP_PASS=your_password

# Third-party APIs
GOOGLE_MAPS_API_KEY=your_google_maps_key
OPENAI_API_KEY=your_openai_key
CLOUDINARY_URL=your_cloudinary_url

# Application
NODE_ENV=development
PORT=5000
FRONTEND_URL=http://localhost:3000
```

---

## Next Steps

1. ✅ Review this structure
2. ✅ Proceed to wireframes design
3. ✅ Set up development environment
4. ✅ Begin backend implementation
5. ✅ Build frontend components

Ready to move to **WIREFRAMES**? 🎨
