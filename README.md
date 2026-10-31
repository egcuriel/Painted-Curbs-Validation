## Getting started

1. Clone the repo:

```bash
git clone https://github.com/hackforla/peopledepot-django-sample.git
cd peopledepot-django-sample
```

1. Install `uv` on your machine:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

1. Install all project dependencies:

```bash
uv sync
```

1. Run database migrations:

```bash
uv run python manage.py migrate
```

1. Start the development server:

```bash
uv run python manage.py runserver
```

1. Open the app at `http://127.0.0.1:8000/` or `http://localhost:8000/`.

## Setting up Google Single Sign-On (SSO)

1. Go to the [Google Cloud Console](https://console.cloud.google.com/) and create a new project (or select an existing one):
    * **Project name:** *Can be left as default*
    * **Organization:** No organization

1. Go to **APIs & Services** > **OAuth consent screen** and configure your project:
    * **App name:** any name
    * **User support email:** your email
    * **Audience:** External
    * **Contact Information:** your email

1. Create **OAuth Client**:
    * **Application Type:** Web Application
    * **Name:** can be left as default
    * **Authorized redirect URIs:**
        * `http://127.0.0.1:8000/accounts/google/login/callback/`
        * `http://localhost:8000/accounts/google/login/callback/`

    ***Save `Client ID` and `Client Secret`!***

1. Create your local `.env` file from the template:

```bash
cp .env.example .env
```

Add your credentials in `.env`:

```env
GOOGLE_CLIENT_ID=<Your_Client_ID>
GOOGLE_CLIENT_SECRET=<Your_Client_Secret>
```

### Test Google SSO on the server

1. Restart the server if already running.
1. Go to `http://127.0.0.1:8000/` (or `http://localhost:8000/`) and sign in directly with **Google**.
1. Verify the following messages appear at the top of the screen upon:
    * **Sign In:** `Successfully signed in as <username>`
    * **Sign Out:** `You have signed out`
