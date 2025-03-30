# Netflix Clone Production Deployment Guide

## Requirements
- Node.js v16+
- npm/yarn
- Web server (Nginx, Apache, etc.)

## Steps

1. **Install Tailwind CSS properly**:
```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init
```

2. **Build for production**:
```bash
npm run build
```

3. **Configure PostCSS** (create postcss.config.js):
```js
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  }
}
```

4. **Optimize assets**:
- Minify CSS/JS
- Compress images
- Enable gzip compression

5. **Server configuration** (Nginx example):
```nginx
server {
    listen 80;
    server_name yourdomain.com;
    root /var/www/netflix-clone;
    
    gzip on;
    gzip_types text/css application/javascript;
    
    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

6. **Security recommendations**:
- Implement HTTPS
- Add security headers
- Set up proper caching policies