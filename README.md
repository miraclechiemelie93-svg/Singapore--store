# Singapore Store — production ecommerce starter

This package turns the Singapore Store frontend into a real ecommerce application with:

- Product catalog and search
- Shopping cart
- Customer registration/login
- Customer order history
- Secure server-side Paystack transaction initialization
- Paystack payment verification
- Paystack webhook signature verification
- SQLite order/product/customer storage
- Admin dashboard for products and orders
- Product stock tracking
- Basic security headers
- Responsive storefront

## 1. Requirements

- Node.js 20+
- A Paystack account
- A real HTTPS domain for production

## 2. Setup

```bash
npm install
cp .env.example .env
```

Edit `.env`.

**Never put the Paystack secret key in frontend code.** Paystack requires transaction initialization and verification to happen on the server. The frontend only uses the public key. See the official Paystack documentation: https://paystack.com/docs/payments/accept-payments/

For first testing, use your Paystack TEST public key and TEST secret key. Before taking real payments, switch both to LIVE keys.

## 3. Run

```bash
npm start
```

Open:

http://localhost:3000

The database is created automatically under `data/store.db`.

## 4. Admin

The first admin account is created from:

ADMIN_EMAIL
ADMIN_PASSWORD

in `.env`.

Change the password before production use.

Open:

http://localhost:3000/admin.html

## 5. Paystack webhook

After deploying, configure the Paystack webhook URL to:

`https://YOUR-DOMAIN.com/api/paystack/webhook`

The server validates the `x-paystack-signature` before accepting the event.

## 6. Going live

Before launch:

1. Use HTTPS.
2. Set a strong random JWT_SECRET.
3. Use Paystack LIVE keys.
4. Replace sample products/images.
5. Set your actual store contact details.
6. Configure your delivery policy and delivery charges.
7. Configure the Paystack webhook.
8. Change the admin password.
9. Back up the database.
10. Test successful, cancelled, failed and pending payment flows.

This is a complete application starter, but hosting, domain/DNS, business registration/tax requirements, shipping operations, backups and production monitoring still need to be configured for your specific business.
