# 🎬 AI Shorts Generator

> Generate engaging short-form videos automatically using AI-powered scripts, images, voiceovers, and captions.

[![Next.js](https://img.shields.io/badge/Next.js-15.x-black?style=flat-square&logo=next.js)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue?style=flat-square&logo=typescript)](https://www.typescriptlang.org/)
[![Prisma](https://img.shields.io/badge/Prisma-6.x-2D3748?style=flat-square&logo=prisma)](https://www.prisma.io/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4.x-38B2AC?style=flat-square&logo=tailwind-css)](https://tailwindcss.com/)

## ✨ Features

- 🤖 **AI-Powered Script Generation** - Create engaging video scripts using OpenAI GPT
- 🎨 **Automated Image Generation** - Generate relevant visuals using Replicate AI models
- 🗣️ **Professional Voiceovers** - Convert text to natural speech with ElevenLabs
- 📝 **Auto-Generated Captions** - Create accurate subtitles using AssemblyAI
- 🎥 **Cloud Video Rendering** - Render videos using Remotion on AWS Lambda
- 👤 **User Authentication** - Secure authentication powered by Clerk
- 💳 **Payment Integration** - Subscription management with Stripe
- ⚡ **Background Processing** - Queue-based video processing with Redis
- 📱 **Responsive Design** - Modern UI with Tailwind CSS and Framer Motion

## 🏗️ Tech Stack

### Frontend
- **Next.js 15** - React framework with App Router
- **TypeScript** - Type-safe development
- **Tailwind CSS** - Utility-first CSS framework
- **Framer Motion** - Smooth animations
- **Radix UI** - Accessible component primitives

### Backend
- **Prisma** - Database ORM
- **PostgreSQL** - Primary database
- **BullMQ** - Job queue management
- **Redis** - Cache and queue storage

### AI & Media Services
- **OpenAI** - Script generation
- **Replicate** - Image generation
- **ElevenLabs** - Text-to-speech
- **AssemblyAI** - Speech-to-text
- **Remotion** - Video rendering
- **AWS S3** - Media storage

### Infrastructure
- **Clerk** - Authentication
- **Stripe** - Payment processing
- **Upstash Redis** - Managed Redis
- **AWS Lambda** - Serverless compute

## 🚀 Quick Start

### Prerequisites

- Node.js 18+ and npm
- PostgreSQL database
- Redis instance (Upstash recommended)
- Required API keys (see [Setup Guide](./SETUP_GUIDE.txt))

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/AKV-7/AI_Shorts_Generator.git
   cd AI_Shorts_Generator
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment setup**
   ```bash
   cp .env.example .env.local
   # Fill in your API keys (see SETUP_GUIDE.txt for details)
   ```

4. **Database setup**
   ```bash
   npx prisma generate
   npx prisma db push
   ```

5. **Start development server**
   ```bash
   npm run dev
   ```

6. **Start background worker** (in a separate terminal)
   ```bash
   npm run worker:dev
   ```

Visit `http://localhost:3000` to see the application.

## 📋 Environment Variables

Create a `.env.local` file with the following variables:

```env
# Authentication (Clerk)
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
CLERK_SECRET_KEY=your_clerk_secret_key

# Database
DATABASE_URL=your_postgresql_connection_string
DIRECT_URL=your_postgresql_direct_connection_string

# AI Services
OPENAI_API_KEY=your_openai_api_key
REPLICATE_API_TOKEN=your_replicate_token
ELEVENLABS_API_KEY=your_elevenlabs_key
ASSEMBLY_API_KEY=your_assemblyai_key

# AWS Services
AWS_REGION=your_aws_region
AWS_ACCESS_KEY_ID=your_aws_access_key
AWS_SECRET_ACCESS_KEY=your_aws_secret_key
S3_BUCKET_NAME=your_s3_bucket_name

# Remotion (AWS Lambda)
REMOTION_AWS_ACCESS_KEY_ID=your_remotion_aws_key
REMOTION_AWS_SECRET_ACCESS_KEY=your_remotion_aws_secret

# Payment (Stripe)
STRIPE_SECRET_KEY=your_stripe_secret_key
STRIPE_WEBHOOK_SECRET=your_stripe_webhook_secret

# Queue (Redis)
UPSTASH_REDIS_HOST=your_upstash_host
UPSTASH_REDIS_PORT=your_upstash_port
UPSTASH_REDIS_PASSWORD=your_upstash_password
```

For detailed instructions on obtaining these API keys, see [SETUP_GUIDE.txt](./SETUP_GUIDE.txt).

## 🎯 How It Works

1. **User Input** - User provides a topic or prompt for the video
2. **Script Generation** - OpenAI generates an engaging script
3. **Image Creation** - Replicate AI creates relevant visuals
4. **Voice Synthesis** - ElevenLabs converts script to natural speech
5. **Caption Generation** - AssemblyAI creates accurate subtitles
6. **Video Rendering** - Remotion combines all elements into a final video
7. **Delivery** - User can download or stream the completed video

## 📁 Project Structure

```
├── app/
│   ├── (auth)/              # Authentication pages
│   ├── actions/             # Server actions
│   │   ├── audio.ts         # ElevenLabs integration
│   │   ├── captions.ts      # AssemblyAI integration
│   │   ├── image.ts         # Replicate integration
│   │   ├── script.ts        # OpenAI integration
│   │   └── render.ts        # Video rendering
│   ├── api/                 # API routes
│   ├── components/          # React components
│   ├── dashboard/           # User dashboard
│   ├── lib/                 # Utility functions
│   ├── remotion/           # Video composition
│   └── ...
├── components/              # Reusable UI components
├── prisma/                  # Database schema
├── worker/                  # Background job processing
└── public/                  # Static assets
```

## 🛠️ Available Scripts

```bash
# Development
npm run dev          # Start development server
npm run worker:dev   # Start background worker (development)

# Production
npm run build        # Build for production
npm run start        # Start production server
npm run worker       # Start background worker (production)

# Database
npx prisma generate  # Generate Prisma client
npx prisma db push   # Push schema to database
npx prisma studio    # Open database browser

# Code Quality
npm run lint         # Run ESLint
```

## 🎨 UI Components

This project uses a modern component library built with:
- **Radix UI** - Accessible primitives
- **Tailwind CSS** - Styling
- **Framer Motion** - Animations
- **Lucide React** - Icons

## 🔧 Configuration

### Video Settings
Customize video parameters in the Remotion composition:
- Duration, dimensions, frame rate
- Transition effects and timing
- Font styles and sizing

### AI Model Settings
Configure AI models in respective action files:
- OpenAI model selection and parameters
- Replicate model choices
- ElevenLabs voice settings

## 🚀 Deployment

### Vercel (Recommended)
1. Connect your GitHub repository to Vercel
2. Configure environment variables
3. Deploy automatically on push

### Manual Deployment
1. Build the application: `npm run build`
2. Start the server: `npm run start`
3. Deploy worker separately: `npm run worker`

## 📊 Monitoring

- Monitor API usage and costs
- Set up error tracking (Sentry recommended)
- Track video processing metrics
- Monitor queue performance

## 💰 Cost Considerations

Estimated monthly costs based on usage:
- **Light usage** (100 videos): $17-33/month
- **Medium usage** (500 videos): $50-100/month
- **Heavy usage** (1000+ videos): $100-300/month

See [SETUP_GUIDE.txt](./SETUP_GUIDE.txt) for detailed cost breakdown.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push to branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- Check [SETUP_GUIDE.txt](./SETUP_GUIDE.txt) for detailed setup instructions
- Open an issue for bugs or feature requests
- Join our community discussions

## 🙏 Acknowledgments

- [Remotion](https://www.remotion.dev/) for video rendering capabilities
- [Vercel](https://vercel.com/) for hosting and deployment
- All the amazing AI services that make this possible

---

**Made with ❤️ for content creators**
