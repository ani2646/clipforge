# ClipForge

A full-stack SaaS platform for video upload & compression and social media image resizing — built with Next.js, Cloudinary, Clerk, and Prisma.

🔗 **Live Demo:** [clipforge-livid-eight.vercel.app](https://clipforge-livid-eight.vercel.app/home)

## Features
- 🔐 **Authentication** — Secure sign-up/sign-in powered by Clerk
- 🎥 **Video Upload & Compression** — Upload videos, automatically compressed and optimized via Cloudinary
- 🖼️ **Social Media Image Resizer** — Upload one image, instantly reformat it for Instagram, Twitter, and Facebook using smart auto-cropping (Cloudinary gravity detection)
- 📊 **Video Dashboard** — Browse uploaded videos with original vs. compressed size comparison
- ⚡ **Real-time Feedback** — Toast notifications for upload progress, errors, and success states

## Tech Stack

**Frontend**
- [Next.js](https://nextjs.org/) (App Router) + TypeScript
- [Tailwind CSS](https://tailwindcss.com/) + [DaisyUI](https://daisyui.com/)
- [next-cloudinary](https://next.cloudinary.dev/) for optimized image rendering
- [react-hot-toast](https://react-hot-toast.com/) for notifications

**Backend**
- Next.js API Routes (App Router `route.ts` handlers)
- [Prisma ORM](https://www.prisma.io/) + PostgreSQL
- [Cloudinary](https://cloudinary.com/) for media storage, transformation & compression

**Auth**
- [Clerk](https://clerk.com/)

## Project Structure
```
app/
├── (app)/                  # Authenticated app routes
│   ├── layout.tsx
│   ├── home/
│   ├── social-share/
│   └── video-upload/
├── (auth)/                 # Clerk auth pages
│   ├── sign-in/[[...sign-in]]/
│   └── sign-up/[[...sign-up]]/
├── api/
│   ├── image-upload/
│   ├── video-upload/
│   └── videos/
├── layout.tsx               # Root layout (ClerkProvider, Toaster)
└── globals.css
components/
└── VideoCard.tsx
prisma/
├── schema.prisma
└── migrations/
types/
└── index.ts
```

## Getting Started

### Prerequisites
- Node.js 18+
- A PostgreSQL database (e.g. [Neon](https://neon.tech/) or [Supabase](https://supabase.com/))
- A [Cloudinary](https://cloudinary.com/) account
- A [Clerk](https://clerk.com/) account

### 1. Clone the repo
```bash
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
```

### 2. Install dependencies
```bash
npm install
```

### 3. Set up environment variables
Create a `.env` file in the root directory:
```env
# Database
DATABASE_URL="postgresql://user:password@host:5432/dbname"

# Cloudinary
NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Clerk
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_publishable_key
CLERK_SECRET_KEY=your_secret_key
```

### 4. Run Prisma migrations
```bash
npx prisma migrate dev
npx prisma generate
```

### 5. Run the dev server
```bash
npm run dev
```
Visit [http://localhost:3000](http://localhost:3000).

## Deployment
This project is deployed on [Vercel](https://vercel.com/):
1. Push your code to GitHub
2. Import the repo on Vercel
3. Add all environment variables listed above in your Vercel project settings
4. Add a `postinstall` script to `package.json` so Prisma generates on build:
   ```json
   "scripts": {
     "postinstall": "prisma generate"
   }
   ```
5. Deploy 🚀

> **Note:** Your `DATABASE_URL` must point to a hosted Postgres instance, not `localhost` — Vercel's servers need to reach it over the internet.

## Roadmap
- [ ] Video comments & likes
- [ ] User profile pages
- [ ] Search & filtering
- [ ] Video playback analytics

## License
This project was built for educational and portfolio purposes.
