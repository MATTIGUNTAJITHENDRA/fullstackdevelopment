# 🚀 DropCode — Code-Based File Transfer

DropCode is a modern, secure, and cross-device file transfer web application that allows users to share files using a simple transfer code.

Upload files on one device, generate a unique code, open DropCode on another device, enter the code, and download the files.

**No account is required for the core file-transfer workflow.**

---

## ✨ Features

- 📤 Upload multiple files
- 🔢 Generate a unique transfer code
- 📋 Copy transfer code with one click
- 📱 Transfer files between phones, tablets, laptops, and desktops
- 🖼️ Support for images
- 🎥 Support for videos
- 🎵 Support for audio
- 📄 Support for documents and PDFs
- 📦 Multiple-file download support
- 🔐 Secure file storage using Supabase
- ⏳ Temporary transfers with expiration
- 👤 Optional user authentication
- 📊 Transfer history for authenticated users
- 📱 Responsive mobile and desktop interface
- ⚡ Simple and fast user experience

---

## 🎯 How It Works

### 1. Upload

Select or drag and drop your files into DropCode.

### 2. Generate Code

After the upload is completed, DropCode generates a unique transfer code.

Example:

```text
482-731
```

### 3. Open on Another Device

Open DropCode on your phone, laptop, tablet, or another computer.

### 4. Enter the Code

Enter the transfer code generated on the first device.

### 5. Download

The available files are displayed and can be downloaded to the second device.

```text
Upload
   ↓
Generate Code
   ↓
Open on Another Device
   ↓
Enter Code
   ↓
Download Files
```

---

## 🛠️ Tech Stack

### Frontend

- React
- TypeScript
- Vite
- Modern responsive UI

### Backend

- Supabase
- PostgreSQL
- Supabase Storage
- Supabase Authentication
- Supabase Edge Functions where required

### Deployment

- Vercel

---

## 🗄️ Data Architecture

DropCode separates file metadata from the actual uploaded files.

### PostgreSQL

Stores information such as:

```text
Transfer
├── Transfer ID
├── Transfer Code
├── User ID
├── Status
├── Created At
├── Expiration Time
└── Download Count
```

File metadata:

```text
Transfer File
├── File ID
├── Transfer ID
├── File Name
├── File Size
├── MIME Type
├── Storage Path
└── Created At
```

### Supabase Storage

The actual uploaded files are stored in a private Supabase Storage bucket.

```text
Supabase
│
├── PostgreSQL
│   ├── transfers
│   └── transfer_files
│
├── Storage
│   └── file-transfers
│
└── Authentication
```

---

## 🔐 Security

Security is an important part of the application.

DropCode is designed to use:

- Private file storage
- Row Level Security (RLS)
- Secure transfer codes
- Temporary signed download URLs
- Transfer expiration
- Server-side validation
- File validation
- Rate limiting for transfer-code attempts
- Protected authentication
- Environment variables for credentials

Sensitive Supabase service-role/secret keys must never be exposed in frontend code.

---

## 👤 Authentication

Authentication is **optional**.

Users can transfer files without creating an account.

Authenticated users can receive additional features such as:

- Transfer history
- Active transfers
- Previous transfers
- Account management

The core workflow remains:

```text
Upload → Code → Download
```

without requiring registration.

---

## ⚙️ Getting Started

### Prerequisites

Make sure you have installed:

- Node.js
- npm
- Git
- A Supabase account

---

### 1. Clone the Repository

```bash
git clone https://github.com/harish987-programmer/Drop-Code.git
```

Navigate into the project:

```bash
cd Drop-Code
```

---

### 2. Install Dependencies

```bash
npm install
```

---

### 3. Create a Supabase Project

Create a project using:

https://supabase.com/

Create the required database tables and private Storage bucket according to the project's Supabase migrations/configuration.

---

### 4. Configure Environment Variables

Create a `.env.local` file in the project root:

```env
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_PUBLISHABLE_KEY=your_supabase_publishable_key
```

Replace the values with your Supabase project credentials.

### ⚠️ Important

Never commit `.env.local` to GitHub.

Never expose:

```text
SUPABASE_SERVICE_ROLE_KEY
```

or other secret/server credentials in frontend code.

---

### 5. Start the Development Server

```bash
npm run dev
```

The application should be available at the local development URL shown in your terminal.

---

## 🧪 Testing

Before deploying, test the complete workflow:

### Anonymous User

- Open the application
- Upload a file
- Generate a transfer code
- Copy the code
- Open the application on another device
- Enter the code
- Download the file

### Authentication

- Create an account
- Log in
- Create a transfer
- Check transfer history
- Delete a transfer

### Security

Test that:

- Invalid codes are rejected
- Expired transfers cannot be downloaded
- Private files cannot be accessed without authorization
- Users cannot access unrelated transfers
- Secret keys are not exposed to the browser

---

## 📁 Project Structure

The exact structure may vary, but the application generally follows:

```text
project/
│
├── src/
│   ├── components/
│   ├── pages/
│   ├── hooks/
│   ├── lib/
│   └── services/
│
├── public/
│
├── supabase/
│   ├── migrations/
│   └── functions/
│
├── .env.local
├── .gitignore
├── package.json
└── README.md
```

---

## 🚀 Deployment

The application can be deployed using Vercel.

Recommended architecture:

```text
User
  ↓
Vercel
  ↓
DropCode Frontend
  ↓
Supabase
  ├── PostgreSQL
  ├── Storage
  ├── Authentication
  └── Edge Functions
```

Configure the required Supabase environment variables in your deployment platform before deploying.

---

## 📌 Current Limitations

The free infrastructure used for development has storage, bandwidth, and file-size limitations.

For production use at larger scale, the application may require:

- Increased storage
- Higher bandwidth limits
- Larger upload limits
- Better large-file processing
- Background cleanup jobs
- Advanced rate limiting
- Monitoring and logging
- Additional infrastructure

---

## 🔮 Future Improvements

Planned improvements may include:

- 🔗 Shareable transfer links
- 📷 QR-code based transfers
- 📈 Transfer progress between devices
- 🔄 Resumable large-file uploads
- 📦 Improved ZIP generation
- 🔔 Transfer notifications
- 🗑️ Automatic expired-file cleanup
- 🌍 Improved global performance
- 📊 Admin dashboard
- 🛡️ Advanced abuse protection
- 📱 Improved mobile experience

---

## 🤝 Contributing

Contributions, suggestions, and feedback are welcome.

If you find a bug or have an idea for improvement:

1. Fork the repository
2. Create a new branch
3. Make your changes
4. Commit your changes
5. Open a Pull Request

---

## 📄 License

This project is available under the license specified in the repository.

---

## 👨‍💻 Author
M.jithendra

Built as a full-stack web development project to explore:

- React
- TypeScript
- Supabase
- PostgreSQL
- Cloud Storage
- Authentication
- Secure file transfer
- Deployment
- Modern web application architecture

---

⭐ If you find this project interesting, consider giving the repository a star and sharing your feedback.
