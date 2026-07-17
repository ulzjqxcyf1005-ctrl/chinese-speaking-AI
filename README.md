# 🇨🇳 Chinese Speaking AI - Website Luyện Nói Tiếng Trung

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub Stars](https://img.shields.io/github/stars/ulzjqxcyf1005-ctrl/chinese-speaking-AI?style=flat-square)](https://github.com/ulzjqxcyf1005-ctrl/chinese-speaking-AI)

Website hiện đại giúp người dùng luyện nói tiếng Trung bằng AI, kết hợp công nghệ speech recognition, text-to-speech, và GPT.

## ✨ Tính Năng Chính

- 🎤 **Luyện phát âm** - Nhận chấm điểm chi tiết (Pronunciation, Tone, Fluency, Accuracy)
- 💬 **Hội thoại với AI** - Nói chuyện với AI giả lập các tình huống thực tế
- 📚 **Học theo chủ đề** - 16 chủ đề từ cơ bản đến HSK6
- 📊 **Phân tích lỗi** - Chỉ ra lỗi phát âm và đưa cách sửa
- 🎯 **Shadowing** - Lặp lại câu nói của AI với tốc độ tùy chỉnh
- 🎨 **Flashcard** - Spaced Repetition giúp ghi nhớ từ vựng
- 🏆 **Gamification** - XP, Level, Achievement, Leaderboard
- 📈 **Theo dõi tiến độ** - Biểu đồ học tập theo tuần/tháng
- 🌙 **Dark Mode** - Giao diện sáng/tối
- 📱 **Responsive** - Desktop, Tablet, Mobile
- ⚡ **PWA** - Hỗ trợ cài đặt ứng dụng

## 🛠️ Công Nghệ

### Frontend
- **React 18** + TypeScript
- **TailwindCSS** - Styling hiện đại
- **Framer Motion** - Animation mượt
- **Vite** - Build tool nhanh
- **Zustand** - State management
- **React Query** - Data fetching

### Backend
- **Node.js** + Express
- **TypeScript**
- **Supabase** - Database & Auth
- **OpenAI API** - GPT + Whisper
- **Socket.io** - Real-time communication

### AI Services
- **OpenAI GPT-4** - Conversation & Grammar Correction
- **Whisper** - Speech-to-Text
- **Text-to-Speech** - Tạo giọng nói
- **Chinese Pronunciation Scoring** - Đánh giá phát âm

## 📁 Cấu Trúc Dự Án

```
chinese-speaking-AI/
├── frontend/                    # React Frontend
│   ├── src/
│   │   ├── components/
│   │   │   ├── layouts/        # Header, Sidebar
│   │   │   ├── common/         # Reusable components
│   │   │   ├── pages/          # Page components
│   │   │   └── ui/             # UI primitives
│   │   ├── pages/              # Page logic
│   │   ├── hooks/              # Custom hooks
│   │   ├── services/           # API services
│   │   ├── store/              # Zustand stores
│   │   ├── types/              # TypeScript types
│   │   ├── utils/              # Utility functions
│   │   ├── styles/             # Global styles
│   │   ├── App.tsx
│   │   └── main.tsx
│   ├── public/                 # Static files
│   ├── tailwind.config.ts
│   ├── vite.config.ts
│   ├── tsconfig.json
│   └── package.json
│
├── backend/                     # Express Backend
│   ├── src/
│   │   ├── routes/             # API routes
│   │   ├── controllers/        # Route handlers
│   │   ├── services/           # Business logic
│   │   ├── middleware/         # Express middleware
│   │   ├── types/              # TypeScript types
│   │   ├── utils/              # Utilities
│   │   ├── config/             # Configuration
│   │   └── index.ts
│   ├── .env.example
│   ├── tsconfig.json
│   └── package.json
│
├── .github/
│   └── workflows/              # GitHub Actions CI/CD
│
└── README.md
```

## 🚀 Cài Đặt & Chạy Locally

### Yêu Cầu
- Node.js >= 18.0.0
- npm hoặc yarn
- Tài khoản OpenAI API
- Tài khoản Supabase

### 1. Clone Repository

```bash
git clone https://github.com/ulzjqxcyf1005-ctrl/chinese-speaking-AI.git
cd chinese-speaking-AI
```

### 2. Setup Backend

```bash
cd backend

# Copy .env.example to .env
cp .env.example .env

# Cập nhật các biến môi trường:
# OPENAI_API_KEY=your_key
# SUPABASE_URL=your_url
# SUPABASE_KEY=your_key

# Install dependencies
npm install

# Start development server
npm run dev
```

### 3. Setup Frontend

```bash
cd ../frontend

# Install dependencies
npm install

# Create .env.local
cat > .env.local << EOF
VITE_API_URL=http://localhost:5000
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_KEY=your_supabase_key
EOF

# Start development server
npm run dev
```

### 4. Access Application

- Frontend: http://localhost:5173
- Backend: http://localhost:5000
- API Docs: http://localhost:5000/api/docs

## 📋 Environment Variables

### Backend (.env)
```
# Server
PORT=5000
NODE_ENV=development

# Database
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_KEY=your-anon-key
SUPABASE_SERVICE_KEY=your-service-key

# OpenAI
OPENAI_API_KEY=sk-...

# JWT
JWT_SECRET=your-secret-key

# CORS
CORS_ORIGIN=http://localhost:5173
```

### Frontend (.env.local)
```
VITE_API_URL=http://localhost:5000
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_KEY=your-anon-key
```

## 🌐 Deployment

### Frontend - Netlify

```bash
# Build
cd frontend
npm run build

# Deploy
netlify deploy --prod --dir dist
```

**Hoặc:**
1. Push code lên GitHub
2. Kết nối repo với Netlify
3. Set build command: `npm run build`
4. Set publish directory: `dist`

### Backend - Render

1. Push code lên GitHub
2. Tạo Web Service trên Render
3. Set build command: `npm install && npm run build`
4. Set start command: `npm run start`
5. Add environment variables

## 📊 Database Schema (Supabase)

### Users
```sql
CREATE TABLE users (
  id UUID PRIMARY KEY,
  email TEXT UNIQUE,
  username TEXT,
  avatar_url TEXT,
  hsk_level INT DEFAULT 1,
  total_minutes INT DEFAULT 0,
  xp INT DEFAULT 0,
  level INT DEFAULT 1,
  created_at TIMESTAMP,
  updated_at TIMESTAMP
);
```

### Learning History
```sql
CREATE TABLE learning_history (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES users(id),
  topic_id TEXT,
  lesson_id TEXT,
  score INT,
  accuracy FLOAT,
  fluency FLOAT,
  pronunciation FLOAT,
  tone FLOAT,
  grammar FLOAT,
  audio_url TEXT,
  transcript TEXT,
  feedback TEXT,
  created_at TIMESTAMP
);
```

### Achievements
```sql
CREATE TABLE achievements (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES users(id),
  achievement_type TEXT,
  earned_at TIMESTAMP
);
```

## 📖 API Endpoints

### Authentication
- `POST /api/auth/register` - Đăng ký
- `POST /api/auth/login` - Đăng nhập
- `POST /api/auth/logout` - Đăng xuất
- `POST /api/auth/refresh` - Refresh token

### User
- `GET /api/user/profile` - Lấy profile
- `PUT /api/user/profile` - Cập nhật profile
- `GET /api/user/stats` - Lấy thống kê

### Learning
- `GET /api/topics` - Danh sách chủ đề
- `GET /api/lessons/:topicId` - Danh sách bài
- `GET /api/lesson/:lessonId` - Chi tiết bài
- `POST /api/practice/submit` - Submit bài luyện
- `GET /api/practice/score` - Lấy điểm

### AI
- `POST /api/ai/speak` - Lấy giọng nói AI
- `POST /api/ai/evaluate` - Đánh giá phát âm
- `POST /api/ai/chat` - Chat với AI
- `POST /api/ai/correct` - Sửa ngữ pháp

## 🎨 Thiết Kế UI/UX

### Màu Sắc (Glassmorphism + Apple Style)
- **Primary**: Blue (#2563EB)
- **Secondary**: Light Blue (#E0F2FE)
- **Dark**: #1E293B
- **Light**: #FFFFFF
- **Neutral**: #94A3B8

### Font
- **Primary**: Inter
- **Chinese**: Noto Sans SC

### Animation
- Transition: 300ms ease-in-out
- Hover effects: Scale 1.05
- Page transitions: Fade in/out
- Wave animation: Giả lập sóng âm

## 🧪 Testing

```bash
# Frontend
cd frontend
npm run test

# Backend
cd backend
npm run test
```

## 📝 Code Style

- ESLint + Prettier
- TypeScript strict mode
- Component-based architecture
- Functional components with hooks
- Composition over inheritance

## 🤝 Đóng Góp

Pull requests được hoan nghênh! Hãy:

1. Fork repo
2. Tạo branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push to branch: `git push origin feature/amazing-feature`
5. Mở Pull Request

## 📄 License

Dự án này được cấp phép dưới MIT License - xem file [LICENSE](LICENSE) để biết chi tiết.

## 📧 Contact

- Email: ulzjqxcyf1005@gmail.com
- GitHub: [@ulzjqxcyf1005-ctrl](https://github.com/ulzjqxcyf1005-ctrl)

## 🔗 Demo & Links

- **Website**: [Sắp ra mắt]
- **API Docs**: [Swagger API]
- **Frontend Deploy**: Netlify
- **Backend Deploy**: Render

---

**Made with ❤️ by AI Developer**
