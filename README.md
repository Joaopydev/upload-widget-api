# Cloudflare R2 File Upload API

A fast and efficient file upload API built with Fastify and Cloudflare R2 Storage. This API allows you to upload files to Cloudflare's R2 object storage with ease.

## Features

- 🚀 **Fast File Uploads**: Built with Fastify for high performance
- ☁️ **Cloudflare R2 Integration**: Seamless integration with Cloudflare's R2 Storage
- 🔒 **Secure**: File type and size validation
- 📦 **Simple API**: Easy-to-use REST endpoint for file uploads
- 🛡️ **CORS Support**: Configured with CORS for cross-origin requests
- 📏 **File Size Limit**: Configurable maximum file size (default: 4MB)

## Prerequisites

Before you begin, ensure you have the following:

- Node.js (v14 or later)
- npm or yarn
- Cloudflare R2 bucket and credentials

## Environment Variables

Create a `.env` file in the root directory with the following variables:

```env
CLOUDFLARE_ACCESS_KEY_ID=your_access_key_id
CLOUDFLARE_SECRET_ACCESS_KEY=your_secret_access_key
CLOUDFLARE_BUCKET=your_bucket_name
CLOUDFLARE_ACCOUNT_ID=your_account_id
CLOUDFLARE_PUBLIC_URL=https://your-public-url.r2.dev
```

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/upload-widget-api.git
   cd upload-widget-api
   ```

2. Install dependencies:
   ```bash
   npm install
   # or
   yarn install
   ```

3. Start the development server:
   ```bash
   npm run dev
   # or
   yarn dev
   ```

The server will start on `http://localhost:3333` by default.

## API Endpoints

### Upload a File

**Endpoint:** `POST /uploads`

Upload a file to Cloudflare R2 Storage.

**Request:**
- **Content-Type:** `multipart/form-data`
- **Body:**
  - `file`: The file to upload (max 4MB)

**Response (Success - 201 Created):**
```json
{
  "url": "https://your-public-url.r2.dev/filename.ext"
}
```

**Response (Error - 400 Bad Request):**
```json
{
  "message": "Invalid file provided."
}
```

**Response (Error - 400 Bad Request - File too large):**
```json
{
  "message": "File size must be a maximum of 4MB."
}
```

## Error Handling

The API returns appropriate HTTP status codes and JSON error messages for different scenarios:

- `400 Bad Request`: Invalid or missing file, or file exceeds size limit
- `500 Internal Server Error`: Server-side error during file upload

## Security

- File names are sanitized to remove special characters
- CORS is enabled with a permissive policy (configure as needed for production)
- File size is limited to prevent abuse
- Sensitive credentials are stored in environment variables

## Development

### Available Scripts

- `dev`: Start the development server with hot-reload
- `build`: Build the TypeScript project
- `start`: Start the production server
- `test`: Run tests (if any)

### Linting

```bash
npm run lint
# or
yarn lint
```

## Deployment

1. Build the project:
   ```bash
   npm run build
   ```

2. Start the production server:
   ```bash
   npm start
   ```

For production deployment, consider using a process manager like PM2 or deploying to a platform like Vercel, Railway, or your preferred cloud provider.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [Fastify](https://www.fastify.io/)
- [Cloudflare R2](https://developers.cloudflare.com/r2/)
- [@fastify/multipart](https://github.com/fastify/fastify-multipart)
- [@fastify/cors](https://github.com/fastify/fastify-cors)
