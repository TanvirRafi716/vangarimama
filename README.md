# Vangari Mama

A Django-based online marketplace for trading scrap materials — connecting sellers who list scrap items with buyers who can browse, bid, and place orders.

🔗 **Live demo:** [vangarimama.vercel.app](https://vangarimama.vercel.app)

## Features

- **User accounts** — registration, login, and social auth via `django-allauth`, with phone number verification support
- **Listings** — post scrap items for sale with images and details
- **Bidding** — buyers can place bids on active listings
- **Orders** — order placement and management once a deal is finalized
- **Reviews** — buyer/seller feedback and ratings
- **Notifications** — in-app alerts for bids, orders, and other activity
- **Media handling** — image uploads via Cloudinary

## Tech Stack

- **Backend:** Django 6.1
- **Database:** PostgreSQL (via `psycopg2-binary`, `dj-database-url`)
- **Auth:** django-allauth
- **Media storage:** Cloudinary (`django-cloudinary-storage`)
- **Static files:** WhiteNoise
- **Styling:** Tailwind CSS
- **Deployment:** Vercel

## Project Structure

```
vangarimama/
├── vangari_mama/       # Django project settings/config
├── core/               # Core app (shared views, home, etc.)
├── users/              # User accounts & authentication
├── listings/           # Scrap item listings
├── bids/               # Bidding system
├── orders/             # Order management
├── reviews/            # Ratings & reviews
├── notifications/      # User notifications
├── media/              # Uploaded media (local dev)
├── static/             # Static assets
├── manage.py
├── requirements.txt
├── tailwind.config.js
└── vercel.json
```

## Getting Started

### Prerequisites

- Python 3.10
- PostgreSQL
- A Cloudinary account (for media uploads)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/TanvirRafi716/vangarimama.git
   cd vangarimama
   ```

2. **Create a virtual environment and install dependencies**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. **Configure environment variables**

   Create a `.env` file in the project root (loaded via `python-decouple`) with values such as:
   ```
   SECRET_KEY=your-secret-key
   DEBUG=True
   DATABASE_URL=postgres://user:password@localhost:5432/vangarimama
   CLOUDINARY_URL=cloudinary://<api_key>:<api_secret>@<cloud_name>
   ```

4. **Run migrations**
   ```bash
   python manage.py migrate
   ```

5. **Create a superuser (optional)**
   ```bash
   python manage.py createsuperuser
   ```

6. **Start the development server**
   ```bash
   python manage.py runserver
   ```

   The app will be available at `http://127.0.0.1:8000/`.

## Deployment

This project includes a `vercel.json` configuration for deployment on [Vercel](vangarimama.vercel.app), with `gunicorn` and `whitenoise` set up for production use.

## Contributing

Contributions are welcome. Please open an issue or submit a pull request with a clear description of your changes.

## License

No license has been specified for this repository yet.