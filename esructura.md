multimedia-platform/
├── backend/
├── frontend/
├── storage/
├── infra/
└── README.md

Backend — Onion Architecture (monolito)
backend/
├── src/
│   │
│   ├── MultimediaApp.Domain/               ← sin dependencias externas
│   │   ├── Entities/
│   │   │   ├── User.cs
│   │   │   ├── Portfolio.cs
│   │   │   ├── Album.cs
│   │   │   ├── MediaFile.cs
│   │   │   ├── Tag.cs
│   │   │   └── Comment.cs
│   │   ├── Enums/
│   │   │   ├── FileType.cs
│   │   │   ├── MediaStatus.cs
│   │   │   └── UserRole.cs
│   │   └── Interfaces/
│   │       ├── Repositories/
│   │       │   ├── IUserRepository.cs
│   │       │   ├── IPortfolioRepository.cs
│   │       │   ├── IAlbumRepository.cs
│   │       │   └── IMediaFileRepository.cs
│   │       └── Services/
│   │           ├── IFileStorageService.cs
│   │           ├── IMessagePublisher.cs
│   │           └── IAiService.cs
│   │
│   ├── MultimediaApp.Application/          ← lógica de negocio pura
│   │   ├── DTOs/
│   │   │   ├── Auth/
│   │   │   │   ├── RegisterRequest.cs
│   │   │   │   ├── LoginRequest.cs
│   │   │   │   └── TokenResponse.cs
│   │   │   ├── Portfolio/
│   │   │   ├── Album/
│   │   │   └── MediaFile/
│   │   ├── UseCases/
│   │   │   ├── Auth/
│   │   │   │   ├── RegisterUseCase.cs
│   │   │   │   └── LoginUseCase.cs
│   │   │   ├── Portfolios/
│   │   │   │   ├── CreatePortfolioUseCase.cs
│   │   │   │   └── GetPortfoliosUseCase.cs
│   │   │   ├── Albums/
│   │   │   │   └── CreateAlbumUseCase.cs
│   │   │   └── MediaFiles/
│   │   │       ├── UploadImageUseCase.cs
│   │   │       └── UploadVideoUseCase.cs
│   │   └── Events/
│   │       ├── ImageUploadedEvent.cs
│   │       └── VideoUploadedEvent.cs
│   │
│   ├── MultimediaApp.Infrastructure/       ← implementaciones concretas
│   │   ├── Data/
│   │   │   ├── AppDbContext.cs
│   │   │   ├── Migrations/
│   │   │   └── Repositories/
│   │   │       ├── UserRepository.cs
│   │   │       ├── PortfolioRepository.cs
│   │   │       ├── AlbumRepository.cs
│   │   │       └── MediaFileRepository.cs
│   │   ├── Storage/
│   │   │   └── LocalFileStorageService.cs
│   │   ├── Messaging/
│   │   │   ├── RabbitMqPublisher.cs
│   │   │   ├── Consumers/
│   │   │   │   ├── ImageUploadedConsumer.cs
│   │   │   │   └── VideoUploadedConsumer.cs
│   │   ├── MediaProcessing/
│   │   │   ├── ImageSharpService.cs
│   │   │   └── FfmpegService.cs
│   │   ├── Auth/
│   │   │   └── JwtService.cs
│   │   └── AI/
│   │       └── OpenAiService.cs
│   │
│   └── MultimediaApp.Presentation/         ← punto de entrada HTTP
│       ├── Controllers/
│       │   ├── AuthController.cs           ← POST /auth/register, /login, /refresh
│       │   ├── PortfoliosController.cs
│       │   ├── AlbumsController.cs
│       │   ├── MediaFilesController.cs
│       │   ├── CommentsController.cs
│       │   └── AiController.cs
│       ├── Middleware/
│       │   ├── JwtMiddleware.cs
│       │   └── ExceptionMiddleware.cs
│       ├── Program.cs
│       ├── appsettings.json
│       └── appsettings.Development.json
│
├── tests/
│   ├── MultimediaApp.Domain.Tests/
│   ├── MultimediaApp.Application.Tests/
│   └── MultimediaApp.Infrastructure.Tests/
│
├── Dockerfile
└── MultimediaApp.sln

Frontend — React + TypeScript + Vite

frontend/
├── public/
└── src/
    ├── assets/
    ├── components/
    │   ├── ui/
    │   ├── layout/
    │   │   ├── Navbar.tsx
    │   │   └── Sidebar.tsx
    │   ├── portfolio/
    │   ├── album/
    │   └── media/
    │       ├── ImageCard.tsx
    │       └── VideoPlayer.tsx
    ├── pages/
    │   ├── LoginPage.tsx
    │   ├── RegisterPage.tsx
    │   ├── DashboardPage.tsx
    │   ├── PortfolioPage.tsx
    │   └── AlbumPage.tsx
    ├── hooks/
    │   ├── useAuth.ts
    │   └── useMedia.ts
    ├── services/
    │   ├── authService.ts
    │   ├── portfolioService.ts
    │   ├── mediaService.ts
    │   └── aiService.ts
    ├── store/
    │   └── authStore.ts
    ├── types/
    │   └── index.ts
    ├── App.tsx
    └── main.tsx
├── index.html
├── vite.config.ts
├── tsconfig.json
├── package.json
└── Dockerfile

Storage e Infra

storage/
├── images/
├── videos/
├── thumbnails/
└── optimized/

infra/
├── nginx/
│   └── nginx.conf
└── docker-compose.yml