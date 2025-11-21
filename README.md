# Blooming 🌸

> Emotional Well-being Monitoring Platform for Elementary and Early Middle School Students

[![Node.js](https://img.shields.io/badge/Node.js-Latest-green.svg)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-Latest-lightgrey.svg)](https://expressjs.com/)
[![Angular](https://img.shields.io/badge/Angular-Latest-red.svg)](https://angular.io/)
[![Sequelize](https://img.shields.io/badge/Sequelize-ORM-blue.svg)](https://sequelize.org/)
[![License](https://img.shields.io/badge/License-GPL--3.0-blue.svg)](LICENSE)

Blooming is an innovative application designed to monitor the emotional well-being of students in school environments. The platform offers a comprehensive approach, combining a robust backend with an interactive frontend, enabling educators and administrators to track students' emotional states effectively and in real-time.

## 📋 Table of Contents

- [🎯 Overview](#-overview)
- [✨ Key Features](#-key-features)
- [🏗️ System Architecture](#-system-architecture)
- [🛠️ Technologies Used](#-technologies-used)
- [📦 Installation](#-installation)
- [⚙️ Configuration](#-configuration)
- [🚀 Usage](#-usage)
- [📁 Project Structure](#-project-structure)
- [📚 API Documentation](#-api-documentation)
- [🎨 Frontend Features](#-frontend-features)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)
- [📞 Contact](#-contact)

## 🎯 Overview

Blooming addresses the critical need for emotional well-being monitoring in educational settings, specifically targeting elementary and early middle school students. The platform provides educators with powerful tools to:

- **Track Emotional States**: Monitor students' emotional well-being in real-time
- **Analyze Trends**: Identify patterns and potential concerns through data visualization
- **Intervene Proactively**: Enable timely support based on comprehensive emotional metrics
- **Generate Reports**: Access key performance indicators (KPIs) for informed decision-making

The application combines modern web technologies with a user-centered design philosophy to create an intuitive, secure, and scalable solution for educational institutions.

## ✨ Key Features

### KPI Management
- Integration of key performance indicators for tracking students' emotional metrics
- Real-time data analysis and visualization
- Customizable dashboards for educators and administrators
- Comprehensive reporting capabilities

### Security and Scalability
- Robust security practices protecting sensitive student data
- Scalable architecture designed to support institutional growth
- Secure authentication and authorization mechanisms
- Data encryption and privacy compliance

### Intuitive User Interface
- User-centered design facilitating easy navigation
- Responsive layout optimized for various devices
- Interactive data visualization components
- Accessible and inclusive design principles

### Custom Graphics Engine
- WebGL-implemented graphics engine tailored to student experience
- Engaging visual elements enhancing user interaction
- Optimized performance for smooth animations
- Custom-built to meet specific educational needs

## 🏗️ System Architecture

```
┌─────────────────────┐
│   Angular Frontend  │  ← Interactive UI (WebGL, HTML5, CSS3)
│   (Port: 4200)      │
└──────────┬──────────┘
           │ HTTP/REST
┌──────────▼──────────┐
│   Express Server    │  ← RESTful API (Node.js)
│   (Port: 3000)      │
└──────────┬──────────┘
           │ Sequelize ORM
┌──────────▼──────────┐
│   SQL Database      │  ← Data Persistence (MySQL/PostgreSQL)
└─────────────────────┘
```

### Component Breakdown

**Frontend Layer**
- Angular framework for dynamic single-page application
- Custom WebGL graphics engine
- Responsive design with SCSS
- Component-based architecture

**Backend Layer**
- Node.js runtime environment
- Express.js for RESTful API
- Sequelize ORM for database abstraction
- MVC architecture pattern

**Data Layer**
- SQL database (MySQL or PostgreSQL)
- Normalized schema for optimal performance
- Secure data storage and retrieval
- Transaction management

## 🛠️ Technologies Used

### Backend
- **Node.js**: JavaScript runtime for scalable server-side applications
- **Express**: Fast, minimalist web framework for Node.js
- **Sequelize**: Promise-based ORM for SQL database management
  - Streamlined data access
  - Model-based approach
  - Migration support
  - Query builder

### Frontend
- **Angular**: Comprehensive frontend framework
  - Component-based architecture
  - Dependency injection
  - RxJS for reactive programming
  - TypeScript for type safety
- **HTML5**: Modern semantic markup
- **CSS3**: Advanced styling capabilities
- **SCSS**: Enhanced CSS with variables and nesting
- **WebGL**: Custom graphics engine implementation
  - Hardware-accelerated rendering
  - Interactive 3D visualizations
  - Optimized for educational content

### Development Tools
- **Angular CLI**: Command-line interface for Angular development
- **npm**: Package management
- **Git**: Version control
- **TypeScript**: Typed superset of JavaScript

## 📦 Installation

### Prerequisites
- **Node.js** (v14.x or higher)
- **npm** (v6.x or higher)
- **Angular CLI** (v12.x or higher)
- **SQL Database** (MySQL 8.x or PostgreSQL 12.x)
- **Git**

### Installation Steps

#### Step 1: Clone the Repository
```bash
git clone https://github.com/franndeli/Blooming.git
cd Blooming
```

#### Step 2: Backend Setup

**Install Dependencies**
```bash
cd backend
npm install
```

**Configure Database**
1. Create a new database in your SQL manager:
```sql
CREATE DATABASE blooming_db;
```

2. Update database credentials in `config/config.json`:
```json
{
  "development": {
    "username": "your_username",
    "password": "your_password",
    "database": "blooming_db",
    "host": "localhost",
    "dialect": "mysql"
  }
}
```

**Run Database Migrations**
```bash
npx sequelize-cli db:migrate
```

**Seed Database (Optional)**
```bash
npx sequelize-cli db:seed:all
```

**Start the Backend Server**
```bash
npm start
# Server will run on http://localhost:3000
```

#### Step 3: Frontend Setup

**Install Dependencies**
```bash
cd ../frontend
npm install
```

**Configure API Endpoint**
Update the API URL in `src/environments/environment.ts`:
```typescript
export const environment = {
  production: false,
  apiUrl: 'http://localhost:3000/api'
};
```

**Start the Frontend Application**
```bash
ng serve
# Application will run on http://localhost:4200
```

## ⚙️ Configuration

### Backend Configuration

**Database Configuration** (`config/config.json`)
```json
{
  "development": {
    "username": "root",
    "password": "password",
    "database": "blooming_dev",
    "host": "localhost",
    "dialect": "mysql",
    "logging": false
  },
  "test": {
    "username": "root",
    "password": "password",
    "database": "blooming_test",
    "host": "localhost",
    "dialect": "mysql"
  },
  "production": {
    "use_env_variable": "DATABASE_URL",
    "dialect": "postgres",
    "dialectOptions": {
      "ssl": {
        "require": true,
        "rejectUnauthorized": false
      }
    }
  }
}
```

**Server Configuration** (`server.js` or `.env`)
```bash
PORT=3000
NODE_ENV=development
JWT_SECRET=your_secret_key_here
SESSION_SECRET=your_session_secret
```

### Frontend Configuration

**Environment Settings** (`src/environments/`)
```typescript
// environment.ts (development)
export const environment = {
  production: false,
  apiUrl: 'http://localhost:3000/api',
  enableDebug: true
};

// environment.prod.ts (production)
export const environment = {
  production: true,
  apiUrl: 'https://api.blooming.app/api',
  enableDebug: false
};
```

## 🚀 Usage

### Starting the Application

**Development Mode**
```bash
# Terminal 1 - Backend
cd backend
npm run dev  # Uses nodemon for auto-restart

# Terminal 2 - Frontend
cd frontend
ng serve --open  # Opens browser automatically
```

**Production Mode**
```bash
# Build frontend
cd frontend
ng build --prod

# Start backend (serves frontend)
cd ../backend
npm start
```

### Accessing the Application

- **Frontend**: http://localhost:4200
- **Backend API**: http://localhost:3000/api
- **API Documentation**: http://localhost:3000/api-docs (if configured)

### Default Credentials (if seeded)
```
Admin:
  Email: admin@blooming.app
  Password: admin123

Teacher:
  Email: teacher@blooming.app
  Password: teacher123
```

## 📁 Project Structure

```
Blooming/
│
├── backend/                          # Node.js + Express backend
│   ├── controllers/                  # Request handlers
│   │   ├── admins.js                 # Admin management
│   │   ├── alumnos.js                # Student (alumnos) management
│   │   ├── auth.js                   # Authentication logic
│   │   ├── centros.js                # Educational centers management
│   │   ├── clases.js                 # Class management
│   │   ├── opciones.js               # Answer options controller
│   │   ├── preguntas.js              # Questions controller
│   │   ├── profesores.js             # Teacher management
│   │   ├── respuestas.js             # Student responses controller
│   │   └── sesiones.js               # Session management
│   │
│   ├── database/                     # Database configuration
│   │   └── configdb.js               # Sequelize database config
│   │
│   ├── helpers/                      # Utility helpers
│   │   ├── jwt.js                    # JWT token utilities
│   │   ├── reset.js                  # Password reset helpers
│   │   └── ultimaEjecucion.txt       # Last execution tracker
│   │
│   ├── middleware/                   # Custom middleware
│   │   ├── hashHelper.js             # Password hashing
│   │   ├── validaciones.js           # Input validation
│   │   ├── validar-jwt.js            # JWT validation
│   │   └── validar-rol.js            # Role-based access control
│   │
│   ├── models/                       # Sequelize models
│   │   ├── admin.js                  # Admin model
│   │   ├── alumno.js                 # Student model
│   │   ├── ambito.js                 # Domain/scope model
│   │   ├── associations.js           # Model relationships
│   │   ├── centro.js                 # Educational center model
│   │   ├── clase.js                  # Class model
│   │   ├── opcion.js                 # Answer option model
│   │   ├── pregunta.js               # Question model
│   │   ├── profesor.js               # Teacher model
│   │   ├── respuesta.js              # Response model
│   │   └── sesion.js                 # Session model
│   │
│   ├── routes/                       # API routes
│   │   ├── admins.js                 # Admin endpoints
│   │   ├── alumnos.js                # Student endpoints
│   │   ├── auth.js                   # Authentication endpoints
│   │   ├── centros.js                # Center endpoints
│   │   ├── clases.js                 # Class endpoints
│   │   ├── opciones.js               # Option endpoints
│   │   ├── preguntas.js              # Question endpoints
│   │   ├── profesores.js             # Teacher endpoints
│   │   ├── respuestas.js             # Response endpoints
│   │   └── sesiones.js               # Session endpoints
│   │
│   ├── .env                          # Environment variables
│   ├── index.js                      # Application entry point
│   ├── package-lock.json             # Dependency lock file
│   └── package.json                  # Dependencies
│
├── frontend/                         # Angular frontend
│   ├── .vscode/                      # VS Code configuration
│   │   ├── extensions.json           # Recommended extensions
│   │   ├── launch.json               # Debug configuration
│   │   └── tasks.json                # Task runner config
│   │
│   ├── src/
│   │   ├── app/
│   │   │   ├── auth/                 # Authentication module
│   │   │   │   ├── inicio/           # Landing page component
│   │   │   │   ├── login/            # Login component
│   │   │   │   ├── recovery/         # Password recovery
│   │   │   │   ├── registro/         # Registration component
│   │   │   │   ├── auth.module.ts
│   │   │   │   └── auth.routing.ts
│   │   │   │
│   │   │   ├── commons/              # Shared UI components
│   │   │   │   ├── footer/           # Footer component
│   │   │   │   ├── navbar/           # Navigation bar
│   │   │   │   ├── sidebar/          # Sidebar navigation
│   │   │   │   ├── sidebar-centro/   # Center-specific sidebar
│   │   │   │   └── commons.module.ts
│   │   │   │
│   │   │   ├── components/           # Reusable components
│   │   │   │   ├── pagination/       # Pagination component
│   │   │   │   └── components.module.ts
│   │   │   │
│   │   │   ├── graphics/             # Custom WebGL graphics engine
│   │   │   │   ├── arbol_escena/     # Scene graph implementation
│   │   │   │   │   ├── camara.ts     # Camera class
│   │   │   │   │   ├── entidad.ts    # Entity class
│   │   │   │   │   ├── luz.ts        # Light class
│   │   │   │   │   ├── malla.ts      # Mesh class
│   │   │   │   │   └── nodo.ts       # Scene node class
│   │   │   │   ├── gestor_recursos/  # Resource management
│   │   │   │   │   ├── gestorRecursos.ts     # Resource manager
│   │   │   │   │   ├── recurso.ts            # Base resource class
│   │   │   │   │   ├── TRecursoMalla.ts      # Mesh resource type
│   │   │   │   │   ├── TRecursoMaterial.ts   # Material resource type
│   │   │   │   │   ├── TRecursoShader.ts     # Shader resource type
│   │   │   │   │   └── TRecursoTextura.ts    # Texture resource type
│   │   │   │   ├── motor/            # Graphics engine core
│   │   │   │   │   └── motorGrafico.ts       # Main graphics engine
│   │   │   │   └── index.ts          # Graphics module exports
│   │   │   │
│   │   │   ├── guards/               # Route guards
│   │   │   │   └── auth.guard.ts     # Authentication guard
│   │   │   │
│   │   │   ├── interfaces/           # TypeScript interfaces
│   │   │   │   ├── centros.interface.ts
│   │   │   │   ├── login-form.interface.ts
│   │   │   │   ├── navbar.interface.ts
│   │   │   │   ├── sidebar.interface.ts
│   │   │   │   └── token-response.ts
│   │   │   │
│   │   │   ├── layouts/              # Page layouts
│   │   │   │   ├── admin-layout/     # Admin dashboard layout
│   │   │   │   ├── alumno-layout/    # Student view layout
│   │   │   │   └── auth-layout/      # Authentication pages layout
│   │   │   │
│   │   │   ├── pages/                # Application pages
│   │   │   │   ├── admin/            # Admin panel pages
│   │   │   │   │   ├── admindashboard/
│   │   │   │   │   ├── crear-alumnos/
│   │   │   │   │   ├── crear-centros/
│   │   │   │   │   ├── crear-clases/
│   │   │   │   │   ├── crear-profesores/
│   │   │   │   │   ├── editar-admin/
│   │   │   │   │   ├── editar-alumnos/
│   │   │   │   │   ├── editar-centros/
│   │   │   │   │   ├── editar-clases/
│   │   │   │   │   ├── editar-profesores/
│   │   │   │   │   ├── perfil-admin/
│   │   │   │   │   ├── ver-alumnos/
│   │   │   │   │   ├── ver-centros/
│   │   │   │   │   ├── ver-clases/
│   │   │   │   │   └── ver-profesores/
│   │   │   │   │
│   │   │   │   ├── alumnos/          # Student pages
│   │   │   │   │   ├── arbol-escena/ # 3D scene interaction
│   │   │   │   │   └── recompensas/  # Rewards/achievements
│   │   │   │   │
│   │   │   │   ├── centros/          # Educational center pages
│   │   │   │   │   ├── crear-alumnos-c/
│   │   │   │   │   ├── crear-clases-c/
│   │   │   │   │   ├── crear-profesores-c/
│   │   │   │   │   ├── editar-alumnos-c/
│   │   │   │   │   ├── editar-centro/
│   │   │   │   │   ├── editar-clases-c/
│   │   │   │   │   ├── editar-profesores-c/
│   │   │   │   │   ├── perfil-centro/
│   │   │   │   │   ├── ver-alumnos-c/
│   │   │   │   │   ├── ver-clases-c/
│   │   │   │   │   └── ver-profesores-c/
│   │   │   │   │
│   │   │   │   ├── profesores/       # Teacher pages
│   │   │   │   │   ├── actividad-reciente/
│   │   │   │   │   ├── actividad-reciente-negativa/
│   │   │   │   │   ├── ayuda-ambitos/
│   │   │   │   │   ├── editar-profesor/
│   │   │   │   │   ├── perfil-profesor/
│   │   │   │   │   ├── todos-alumnos/
│   │   │   │   │   ├── ver-alumnos-p/
│   │   │   │   │   ├── ver-mas-preguntas/
│   │   │   │   │   └── ver-perfil-alumno/
│   │   │   │   │
│   │   │   │   ├── condiciones-uso/  # Terms of use
│   │   │   │   ├── cookies/          # Cookie policy
│   │   │   │   ├── dashboard/        # Main dashboard
│   │   │   │   ├── informacion-legal/    # Legal information
│   │   │   │   ├── politica-privacidad/  # Privacy policy
│   │   │   │   ├── pages.module.ts
│   │   │   │   └── pages.routing.ts
│   │   │   │
│   │   │   ├── services/             # Angular services
│   │   │   │   ├── graphics/         # Graphics-related services
│   │   │   │   │   ├── helpers/
│   │   │   │   │   │   └── globalstate.service.ts
│   │   │   │   │   ├── cube.service.ts
│   │   │   │   │   └── finalscreen.service.ts
│   │   │   │   ├── admins.service.ts
│   │   │   │   ├── alumnos.service.ts
│   │   │   │   ├── auth.service.ts
│   │   │   │   ├── cargaPreguntas.service.ts
│   │   │   │   ├── centros.service.ts
│   │   │   │   ├── clases.service.ts
│   │   │   │   ├── cubo.service.ts
│   │   │   │   ├── motor.service.ts
│   │   │   │   ├── navbar.service.ts
│   │   │   │   ├── opciones.service.ts
│   │   │   │   ├── plano.service.ts
│   │   │   │   ├── preguntas.service.ts
│   │   │   │   ├── profesores.service.ts
│   │   │   │   ├── respuestas.service.ts
│   │   │   │   ├── sesiones.service.ts
│   │   │   │   └── sidebar.service.ts
│   │   │   │
│   │   │   ├── app-routing.module.ts
│   │   │   ├── app.component.ts
│   │   │   ├── app.module.server.ts
│   │   │   └── app.module.ts
│   │   │
│   │   ├── assets/                   # Static assets
│   │   │   ├── css/                  # Stylesheets
│   │   │   │   ├── icons/            # Icon fonts
│   │   │   │   ├── styles.css
│   │   │   │   └── styles.min.css
│   │   │   │
│   │   │   ├── fonts/                # Custom fonts
│   │   │   │   └── helvetiker_regular.typeface.json
│   │   │   │
│   │   │   ├── glTF/                 # 3D models (glTF format)
│   │   │   │   ├── cubo_final_blooming.bin
│   │   │   │   ├── cubo_final_blooming.gltf
│   │   │   │   ├── pieza_tablero.bin
│   │   │   │   ├── pieza_tablero.gltf
│   │   │   │   ├── plano_final_prueba_2.bin
│   │   │   │   └── plano_final_prueba_2.gltf
│   │   │   │
│   │   │   ├── images/               # Image assets
│   │   │   │   ├── backgrounds/      # Background images
│   │   │   │   ├── como_jugar/       # Tutorial screenshots
│   │   │   │   ├── logos/            # Application logos
│   │   │   │   ├── opciones/         # Answer option images (1-98)
│   │   │   │   ├── profile/          # User profile images
│   │   │   │   └── threejs/          # 3D textures and models
│   │   │   │
│   │   │   ├── js/                   # JavaScript files
│   │   │   │   ├── app.min.js
│   │   │   │   ├── dashboard.js
│   │   │   │   └── sidebarmenu.js
│   │   │   │
│   │   │   ├── libs/                 # Third-party libraries
│   │   │   │   ├── apexcharts/       # Chart library
│   │   │   │   ├── bootstrap/        # Bootstrap framework
│   │   │   │   ├── jquery/           # jQuery library
│   │   │   │   └── simplebar/        # Custom scrollbar
│   │   │   │
│   │   │   ├── scss/                 # SCSS source files
│   │   │   │   ├── component/
│   │   │   │   ├── layouts/
│   │   │   │   ├── pages/
│   │   │   │   ├── utilities/
│   │   │   │   ├── variables/
│   │   │   │   └── styles.scss
│   │   │   │
│   │   │   └── shaders/              # GLSL shaders
│   │   │       ├── fragmentShader.glsl
│   │   │       └── vertexShader.glsl
│   │   │
│   │   ├── environments/             # Environment configurations
│   │   │   ├── environment.development.ts
│   │   │   ├── environment.produccion.ts
│   │   │   └── environment.ts
│   │   │
│   │   ├── favicon.png
│   │   ├── index.html                # Entry HTML
│   │   ├── main.server.ts            # Server-side rendering entry
│   │   ├── main.ts                   # Application bootstrap
│   │   └── styles.css                # Global styles
│   │
│   ├── .editorconfig                 # Editor configuration
│   ├── .gitignore                    # Git ignore rules
│   ├── angular.json                  # Angular configuration
│   ├── package-lock.json             # Dependency lock file
│   ├── package.json                  # Frontend dependencies
│   ├── README.md                     # Frontend documentation
│   ├── server.ts                     # SSR server configuration
│   ├── tsconfig.app.json             # App TypeScript config
│   ├── tsconfig.json                 # TypeScript configuration
│   └── tsconfig.spec.json            # Test TypeScript config
│
├── .gitignore                        # Git ignore rules
├── LICENSE                           # GPL-3.0 license
└── README.md                         # This file
```

## 📚 API Documentation

### Authentication Endpoints

**POST /api/auth/register**
- Register a new user
- Body: `{ email, password, role, name }`
- Returns: `{ token, user }`

**POST /api/auth/login**
- Authenticate user
- Body: `{ email, password }`
- Returns: `{ token, user }`

**GET /api/auth/me**
- Get current user
- Headers: `Authorization: Bearer <token>`
- Returns: `{ user }`

### Student Endpoints

**GET /api/students**
- List all students
- Query params: `page, limit, search`
- Returns: `{ students[], total, page, pages }`

**GET /api/students/:id**
- Get student by ID
- Returns: `{ student }`

**POST /api/students**
- Create new student
- Body: `{ name, age, grade, ... }`
- Returns: `{ student }`

**PUT /api/students/:id**
- Update student
- Body: `{ name, age, grade, ... }`
- Returns: `{ student }`

**DELETE /api/students/:id**
- Delete student
- Returns: `{ message }`

### Emotional Metrics Endpoints

**GET /api/students/:id/metrics**
- Get emotional metrics for student
- Query params: `startDate, endDate`
- Returns: `{ metrics[] }`

**POST /api/students/:id/metrics**
- Record emotional metric
- Body: `{ category, value, notes, date }`
- Returns: `{ metric }`

### KPI Endpoints

**GET /api/kpis/overview**
- Get KPI overview
- Query params: `timeframe`
- Returns: `{ kpis }`

**GET /api/kpis/students/:id**
- Get KPIs for specific student
- Returns: `{ kpis }`

**GET /api/kpis/trends**
- Get trend analysis
- Query params: `metric, period`
- Returns: `{ trends }`

### Report Endpoints

**GET /api/reports**
- List all reports
- Returns: `{ reports[] }`

**POST /api/reports/generate**
- Generate new report
- Body: `{ type, studentId, dateRange, ... }`
- Returns: `{ report }`

**GET /api/reports/:id/download**
- Download report (PDF/CSV)
- Returns: File download

## 🎨 Frontend Features

### Dashboard
- Real-time emotional well-being overview
- Interactive charts and visualizations
- Quick access to critical metrics
- Customizable widget layout

### Student Management
- Comprehensive student profiles
- Emotional metric tracking
- Historical data visualization
- Individual progress monitoring

### KPI Analytics
- Key performance indicators dashboard
- Trend analysis and predictions
- Comparative analytics
- Exportable reports

### WebGL Graphics Engine
- Custom-built visualization system
- Hardware-accelerated rendering
- Engaging student interactions
- Smooth animations and transitions

### Responsive Design
- Mobile-first approach
- Tablet and desktop optimized
- Touch-friendly interfaces
- Accessible on all devices

## 🤝 Contributing

We welcome contributions from the community! To contribute to Blooming:

### Getting Started

1. **Fork the Repository**
   ```bash
   # Click 'Fork' on GitHub, then:
   git clone https://github.com/YOUR_USERNAME/Blooming.git
   cd Blooming
   ```

2. **Create a Feature Branch**
   ```bash
   git checkout -b feature/AmazingFeature
   ```

3. **Make Your Changes**
   - Write clean, documented code
   - Follow existing code style
   - Add tests for new features
   - Update documentation as needed

4. **Commit Your Changes**
   ```bash
   git add .
   git commit -m 'Add some AmazingFeature'
   ```

5. **Push to Your Fork**
   ```bash
   git push origin feature/AmazingFeature
   ```

6. **Open a Pull Request**
   - Go to the original repository
   - Click 'New Pull Request'
   - Select your feature branch
   - Describe your changes in detail

### Contribution Guidelines

- **Code Style**: Follow existing conventions (ESLint, Prettier)
- **Commits**: Use clear, descriptive commit messages
- **Testing**: Ensure all tests pass before submitting
- **Documentation**: Update docs for any new features
- **Issues**: Check existing issues before creating new ones

### Code of Conduct

- Be respectful and inclusive
- Provide constructive feedback
- Focus on what's best for the community
- Show empathy towards others

## 📄 License

This project is licensed under the **GNU General Public License v3.0 (GPL-3.0)**.

### Key Points:
- ✅ **Freedom to Use**: Use the software for any purpose
- ✅ **Freedom to Study**: Access and modify the source code
- ✅ **Freedom to Share**: Distribute copies to help others
- ✅ **Freedom to Improve**: Distribute modified versions

### Copyleft Requirement:
Any derivative work must also be distributed under GPL-3.0, ensuring the software remains free and open-source.

For full license details, see the [LICENSE](LICENSE) file.

## 📞 Contact

### Development Team

**Lead Developer**: Francisco Delicado

- **Email**: delicadofranvi@gmail.com
- **GitHub**: [@franndeli](https://github.com/franndeli)
- **Project Repository**: [Blooming](https://github.com/franndeli/Blooming)

### Get in Touch

Whether you:
- 💡 Have questions about the project
- 🚀 Want to contribute or collaborate
- 📚 Need more information or documentation
- 🐛 Found a bug or have feature requests
- 💼 Are interested in commercial partnerships

**Feel free to reach out!** We're always happy to hear from users, contributors, and fellow developers interested in educational technology and student well-being.

### Support

- **Issues**: Report bugs via [GitHub Issues](https://github.com/franndeli/Blooming/issues)
- **Discussions**: Join conversations in [GitHub Discussions](https://github.com/franndeli/Blooming/discussions)
- **Email**: For general inquiries and support

## 🌟 Star History

If you find Blooming useful, please consider giving it a star ⭐ on GitHub! It helps others discover the project and motivates continued development.

---

**Thank you for visiting Blooming!** 🌸
