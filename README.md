🚀 Mini-ATSA modern, lightning-fast recruitment platform built for speed and simplicity.Manage jobs, track candidates via Kanban, and streamline your hiring process. OverviewMini-ATS is a full-featured recruitment tool designed to bridge the gap between complex enterprise software and simple spreadsheets. It features a public-facing application portal for candidates and a secure dashboard for recruiters, all powered by a real-time database.Unlike bloated legacy systems, Mini-ATS focuses on developer experience and UI responsiveness, utilizing React 19, Supabase for instantaneous state synchronization, and a custom lightweight router.✨ Key Features🎨 Interactive Kanban Board – Drag-and-drop candidates through stages (New, Interview, Offer, Hired) using @hello-pangea/dnd.🌍 Multi-Language Support – Full support for Swedish (SV) and English (EN) with a floating toggle.⚡ Custom Lightweight Router – A purpose-built, zero-dependency router for maximum performance and easy GitHub Pages deployment.🛡️ Role-Based Security – Secure Admin vs. Customer roles. Admins can manage all users; Customers manage their own jobs.🔗 Public Application Portal – Shareable links (e.g., ?apply=123) for candidates to apply and upload CVs securely.📊 Real-time Dashboard – Live statistics on active jobs, total candidates, and hiring progress.📚 Onboarding Wizard – Built-in tutorial guide for new users.📸 Features BreakdownFor RecruitersFeatureDescriptionPipeline BoardVisual Kanban board to manage candidate progress.Job ManagementCreate, edit, delete, and toggle visibility of job postings.Candidate ProfilesRich profile view with CV preview (PDF) and notes.Smart NavigationCustom routing allows deep-linking to specific jobs or views.For Candidates (Public Portal)FeatureDescriptionInstant ApplyNo login required. Apply directly via a shared link.File UploadSecure CV upload directly to Supabase Storage buckets.Mobile ReadyFully responsive design for applying on the go.🛠️ Tech StackLayerTechnologyFrontend FrameworkReact 19 + ViteLanguageTypeScript 5DatabaseSupabase (PostgreSQL)AuthSupabase Auth (Magic Links / Email)StylingTailwindCSS + Lucide IconsRoutingCustom SimpleRouter (Zero dependencies)Drag & Drop@hello-pangea/dnd📂 Project StructureWe use a clean, component-based architecture with a custom router implementation.Plaintextmini-ats/
├── src/
│   ├── components/        # Shared UI components
│   │   ├── dashboard/     # Dashboard-specific (JobCard, StatsGrid, etc.)
│   │   ├── KanbanBoard.tsx
│   │   ├── Navbar.tsx
│   │   └── ...
│   ├── pages/             # Page Views (The "Screens")
│   │   ├── Dashboard.tsx  # Main overview
│   │   ├── JobKanban.tsx  # Specific job view
│   │   └── Customers.tsx  # Admin view
│   ├── router.tsx         # ⚡ Custom Router Logic
│   ├── translations.ts    # SV/EN Dictionary
│   ├── supabaseClient.ts  # Database connection
│   └── App.tsx            # Main Entry Point
├── supabase/              # SQL migrations
├── public/                # Static assets
└── vite.config.ts         # Configuration
🚀 Quick StartPrerequisitesNode.js 18+Supabase Account (Free Tier)InstallationClone repositoryBashgit clone https://github.com/b1-loop/min-sida.git
cd min-sida
Install dependenciesBashnpm install
Setup EnvironmentCreate a .env file in the root directory:KodavsnittVITE_SUPABASE_URL=your_project_url
VITE_SUPABASE_ANON_KEY=your_anon_key
Database Setup (Supabase)You need three tables:profiles (id, email, role, full_name...)jobs (id, title, user_id, status...)candidates (id, job_id, status, cv_url...)Start Development ServerBashnpm run dev
💾 Database Schema & SecurityCore Tablesprofiles: Extends auth.users. Handles roles (admin, customer).jobs: Stores job postings, rich text descriptions, and active status.candidates: Candidate data linked to jobs. Stores CV URLs.Security (RLS)Authentication: Managed via Supabase Auth.Authorization:jobs can only be edited by the creator (Recruiter) or Admin.candidates are private to the recruiter who owns the job.Public access is allowed ONLY for inserting new applications via the public portal.🚦 StatusComponentStatusCore Features✅ CompleteKanban Board✅ Production ReadyCustom Router✅ ImplementedMulti-Language✅ ImplementedFile Uploads✅ ImplementedAdmin Panel✅ Implemented📄 LicenseMIT License - see https://www.google.com/search?q=LICENSE for details.Built by Bozhidar N Ivanov