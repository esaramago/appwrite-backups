# The code is on https://gitlab.com/emanuelsaramago/appwrite-backups/-/tree/main(https://gitlab.com/emanuelsaramago/appwrite-backups/-/tree/main)

# Appwrite Backup Tool

Backup you Appwrite database to JSON and CSV files.

## 1. What it does

This tool automatically backs up all tables from an Appwrite database to both JSON and CSV files. It connects to your Appwrite instance, retrieves all collections (tables) and their data, then exports each table to separate JSON and CSV files in the `backups/` directory.

## 2. Requirements

- **Node.js** (version 14 or higher recommended)
- **npm** (comes with Node.js)
- **Appwrite account** with:
  - API Key with read permissions
  - Database ID
  - Project ID
  - Appwrite endpoint URL

## 3. Setup

1. **Clone or download this repository**

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Configure environment variables:**
   
   Rename the `.env.example` file to `.env`
   
   Edit the `.env` file and fill in your Appwrite credentials:
   ```
   APPWRITE_ENDPOINT=https://cloud.appwrite.io/v1
   APPWRITE_PROJECT_ID=your-project-id
   APPWRITE_DATABASE_ID=your-database-id
   APPWRITE_API_KEY=your-api-key
   ```

   **Where to find these values:**
   - **ENDPOINT**: Your Appwrite server URL (e.g., `https://cloud.appwrite.io/v1` for cloud, or your self-hosted URL)
   - **PROJECT_ID**: Found in your Appwrite project settings
   - **DATABASE_ID**: Found in your Appwrite database settings
   - **API_KEY**: Create an API key in your Appwrite project settings with read permissions for databases

## 4. Run the backup

Execute the backup script:

```bash
npm start
```

Or directly with Node.js:

```bash
node index.js
```

The script will:
1. Connect to your Appwrite instance
2. List all collections (tables) in the specified database
3. Export each table's data to:
   - `backups/{table-name}.json` (formatted JSON)
   - `backups/{table-name}.csv` (CSV format)

All backup files are saved in the `backups/` directory, which is automatically created if it doesn't exist.

**Note:** The `backups/` directory is ignored by git (as specified in `.gitignore`), so your backup files won't be committed to version control.
