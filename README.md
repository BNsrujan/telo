# Telo - Machine Management Dashboard

A web application built with Next.js for managing machines, users, and financial transactions. Features a clean dashboard interface with authentication, machine management, and expense tracking capabilities.


## the project is in complite 

## Features

- **Dashboard Overview** - Centralized view of system metrics and data
- **Machine Management** - Add, view, and manage machines with unique IDs
- **User Management** - User registration and management system
- **Financial Tracking** - Recharge and expense management with data tables
- **Authentication** - Secure login system

## Tech Stack

- **Framework**: Next.js 15.2.0 with App Router
- **Language**: TypeScript
- **Styling**: Tailwind CSS v4
- **UI Components**: Radix UI primitives with shadcn/ui
- **Forms**: React Hook Form with Zod validation
- **Data Tables**: TanStack Table
- **Icons**: Lucide React
- **HTTP Client**: Axios
- **Theme**: next-themes for dark/light mode

## Project Structure

```
src/
├── app/
│   ├── (auth)/
│   │   └── login/          # Authentication pages
│   ├── (dashbords)/
│   │   ├── dashbord/       # Main dashboard
│   │   ├── setting/        # Settings page
│   │   └── user/           # User management
│   ├── globals.css         # Global styles
│   ├── layout.tsx          # Root layout
│   └── page.tsx            # Home page
├── components/
│   ├── addMachines/        # Machine creation dialog
│   ├── addUser/            # User creation dialog
│   ├── machines/           # Machine display components
│   ├── rechargeDialog/     # Recharge functionality
│   ├── rechrgeandexplence/ # Financial data tables
│   ├── sidbar/             # Navigation sidebar
│   └── ui/                 # Reusable UI components
├── data/
│   └── table.ts            # Table data definitions
├── hooks/
│   └── use-mobile.ts       # Mobile detection hook
└── lib/
    └── utils.ts            # Utility functions
```

## Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn package manager

### Installation

1. Clone the repository:

```bash
git clone <repository-url>
cd telo
```

2. Install dependencies:

```bash
npm install
```

3. Run the development server:

```bash
npm run dev
```

4. Open [http://localhost:3000](http://localhost:3000) in your browser.

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run start` - Start production server
- `npm run lint` - Run ESLint

## Key Components

### Machine Management

- Add new machines with unique IDs and names
- View and manage existing machines
- Machine-specific operations and tracking

### User Management

- User registration and profile management
- Role-based access control
- User-specific dashboards

### Financial Tracking

- Recharge system for account management
- Expense tracking and categorization
- Data tables with sorting and filtering
- Financial reporting and analytics

### Dashboard

- Overview of system metrics
- Quick access to key functions
- Responsive grid layout for different screen sizes

## Routing Architecture

The application uses Next.js 15 App Router with several routing patterns:

### Route Groups

- `(auth)` - Authentication routes that share common layout
- `(dashbords)` - Dashboard routes with shared sidebar layout

### Dynamic Routes

- `/dashbord/[slug]` - Machine-specific pages where `slug` is the machine identifier
- `/user/[id]` - User-specific pages where `id` is the user identifier

### Route Structure

```
/                           # Home page
├── /login                  # Authentication (route group: auth)
└── /dashbord              # Dashboard overview (route group: dashbords)
    ├── /dashbord/[slug]   # Dynamic machine pages
    ├── /setting           # Settings page
    └── /user              # User management
        └── /user/[id]     # Dynamic user pages
```

### Dynamic Route Implementation

The dynamic routes use Next.js App Router conventions:

**Machine Pages (`/dashbord/[slug]`)**:

```typescript
export default async function Page({ params }: { params: { slug: string } }) {
  const slug = params.slug;
  return <Machines slug={slug} />;
}
```

**User Pages (`/user/[id]`)**:

```typescript
// Handles routes like /user/123, /user/admin, etc.
function User({ params }: { params: { id: string } }) {
  // User-specific logic based on ID parameter
}
```

### Layout Hierarchy

- Root layout applies to all routes
- `(dashbords)` layout adds sidebar navigation for dashboard routes
- `(auth)` routes use minimal layout for login/signup flows


