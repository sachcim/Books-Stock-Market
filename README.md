# Books Stock Market

Books Stock Market is a comprehensive web platform designed to facilitate the trading, selling, and exchanging of books. It acts as a bridge between book enthusiasts, providing a dual marketplace system for standard book announcements and a visual-centric offer board.

## Key Features

### 🛍️ Dual Marketplace
The platform features two distinct ways to trade:
1.  **Announcements Marketplace**: A traditional listing system where users can post books with detailed descriptions, including subject, grade, and contact information.
2.  **Visual Offers (Image Board)**: A "Marketplace of Offers" where the experience is driven by book covers and visual condition. Users can upload high-quality images, and other users can interact directly with these visual cards.

### 💬 Advanced Messaging System
Communication is central to the Books Stock Market experience. The system implements a robust, multi-channel messaging architecture:
*   **Announcement Messages**: Direct private inquiries sent to sellers regarding specific book announcements.
*   **Offer Messages (MMessages)**: A dedicated message stream for the visual offers marketplace.
*   **Deep Threading (Respond-to-Respond)**: The system supports nested conversations, allowing users to reply to replies, creating a continuous dialogue thread rather than simple one-off messages.

### 🔐 User Accounts & Security
*   **Authentication**: Built on **ASP.NET Core Identity**, ensuring secure user registration, login, and session management.
*   **Profile Management**: Users can manage their personal data and track their active listings and messages.

### 🛠️ Administration & Content Management
*   **Moderation Tools**: Administrators have access to a dashboard to `Accept`, `Reject`, or `Delete` content.
*   **Lifecycle Management**: Listings go through a defined lifecycle status (e.g., `Requested` -> `Accepted` / `Rejected`), ensuring quality control of the marketplace content.
*   **Dynamic Categorization**: Admins can manage book subjects and categories dynamically.

## Technology Stack

The project is built using a modern .NET ecosystem, focusing on robust architecture and maintainable code.

*   **Framework**: [ASP.NET Core 6/7/8](https://dotnet.microsoft.com/en-us/apps/aspnet) (MVC Pattern)
*   **Language**: C#
*   **Database**: SQLite (Development) / SQL Server (Production Ready)
*   **ORM**: [Entity Framework Core](https://learn.microsoft.com/en-us/ef/core/) (Code-First Approach)
*   **Frontend**:
    *   Razor Views (`.cshtml`)
    *   HTML5 / CSS3
    *   JavaScript
    *   **External Libs**: `blowup` (jQuery plugin for image zooming capabilities)

## Architecture Overview

The application follows a clean **Separation of Concerns** using the **Repository Pattern** and a Service Layer facade.

### Data Access Layer (Repositories)
The application abstracts direct database access using Repositories. This ensures that the business logic is decoupled from the specific database implementation (EF Core).
*   `AnnouncementsRepository`: Handles CRUD operations for standard listings.
*   `ImageRepository`: Manages the visual offers data.
*   `MessagesRepository` / `MMessagesRepository`: specialized repositories for the different messaging streams.

### Service Layer (ViewModel Providers)
Instead of Controllers containing complex logic, the application uses **ViewModel Providers** (e.g., `AnnouncementsViewModelProvider`).
*   **Role**: These providers act as a service layer that aggregates data from multiple repositories (e.g., fetching a user, their listings, and related messages) and constructs a ready-to-use `ViewModel` for the View.
*   **Benefit**: This keeps Controllers thin and makes the presentation logic reusable and testable.

### Entities & Data Model
*   `AnnouncementEntity`: The core entity for book listings.
*   `ImageEntity`: Represents the visual offers.
*   `MessageEntity`: Maps to messages for announcements.
*   `MMessageEntity`: Maps to messages for visual offers.
*   `RespondMessageEntity`: Handles the reply threads.

## Getting Started

### Prerequisites
*   [.NET SDK](https://dotnet.microsoft.com/download) (Version 6.0 or later recommended)
*   Your preferred IDE (Visual Studio, VS Code, or Rider)

### Installation

1.  **Clone the repository**
    ```bash
    git clone https://github.com/yourusername/Books-Stock-Market.git
    cd Books-Stock-Market
    ```

2.  **Restore dependencies**
    ```bash
    dotnet restore
    ```

3.  **Setup the Database**
    The project uses Entity Framework Core Migrations. Apply them to create your local SQLite database.
    ```bash
    dotnet ef database update
    ```

4.  **Run the Application**
    ```bash
    dotnet run
    ```
    The application will start, typically at `https://localhost:7025` or `http://localhost:5248`.

## Usage
1.  **Register** a new account.
2.  Navigate to the **Marketplace** to browse books.
3.  Use the **"Add Announcement"** feature to list your own books.
4.  Interact with other users via the **Messages** tab.
