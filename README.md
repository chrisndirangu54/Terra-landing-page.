# TerraForge Labs — standalone brand and equipment shop
Independent website for African mineral exploration and hydrogeology consulting. No dependency on TerraForge's private GeoAI platform.

## Setup
1. `npm install && npm run dev`. Configure `.env` from `.env.example`.
2. Firebase project: enable Firestore, Storage and Google Authentication; register your domain.
3. Deploy rules and functions: `firebase deploy --only firestore:rules,storage,functions`.
4. Grant admins with Firebase Admin SDK **custom claim** `admin: true` only after identity verification; refresh their token. The UI alone is not a security boundary.
5. Create Firebase secret: `firebase functions:secrets:set PAYSTACK_SECRET_KEY` (never expose secret through Vite).
6. Configure Paystack webhook to the deployed `paystackWebhook` HTTPS function. Payment is marked paid only by verified webhook and independent transaction verification.
7. Configure Paystack M-Pesa payment channels for a verified Kenyan merchant account; availability and supported currencies depend on Paystack merchant configuration. Do not assume every customer can pay by M-Pesa.
8. Use Firestore `products` documents with `name, category, description, amountMinor, currency, imageUrl, active`; `gallery` with `title, url, published, createdAt`.
9. Formcarry endpoint was reused from the HTML repository. **It belongs to the earlier TeknTandao form**, so configure notification routing or a dedicated TerraForge form before launch to prevent mixed enquiries.
10. Launch only after shipping/tax/refund policies, product stock verification, final checkout tests, and production App Check configuration.

Prices are stored in minor currency units and **never trusted from the browser**. This is a starter storefront, not a certified fulfillment or drilling safety system.
