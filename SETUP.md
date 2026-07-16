# Setup Profile Generation

## Langkah 1: Siapkan Portrait (Foto Anda)

Anda perlu menyediakan **portrait.png** - foto transparan Anda sendiri (recommended: PNG dengan background transparan, ukuran ~300-400px).

### Opsi A: Upload Portrait Langsung ke Repository
1. Letakkan file `portrait.png` di root repository
2. Push ke branch `main`
3. Workflow otomatis akan menjalankan generate

### Opsi B: Jalankan Lokal
Jika Anda sudah punya `portrait.png`:

```bash
# Install dependencies
npm install

# Generate dengan portrait
npm run generate -- --source /absolute/path/to/portrait.png

# Atau generate hanya README (tanpa portrait)
npm run generate:readme

# Validate hasilnya
npm run check

# Commit
git add README.md assets/hero/
git commit -m "chore: update profile with new portrait"
git push
```

## Langkah 2: Buat Portrait Anda

Beberapa opsi untuk membuat portrait:

1. **AI-Generated (Rekomendasi)**
   - Gunakan Midjourney, DALL-E, atau Stable Diffusion
   - Prompt: "professional portrait, transparent background, illustrative style"
   - Export sebagai PNG dengan transparent background

2. **From Photo**
   - Ambil foto Anda
   - Remove background menggunakan: remove.bg, Photoshop, atau GIMP
   - Crop dan resize ke ~400x400px

3. **Avatar Service**
   - Clay Avatars (claypot.ai)
   - Dicebear Avatars (dicebear.com)
   - Generate sebagai PNG

## Struktur Generate

Script `npm run generate` akan:
1. ✅ Membaca `profile.config.json`
2. ✅ Process portrait.png menggunakan Sharp
3. ✅ Generate 4 responsive SVG hero images:
   - Desktop Dark Mode
   - Desktop Light Mode
   - Mobile Dark Mode
   - Mobile Light Mode
4. ✅ Generate README.md dengan data dari config
5. ✅ Output ke `assets/hero/` dengan manifest.json

## Troubleshooting

### Error: "portrait.png not found"
→ Pastikan file ada di root directory dengan nama EXACTLY `portrait.png`

### Error: "Sharp error"
→ Pastikan `portrait.png` adalah valid PNG file

### README tidak terupdate
→ Jalankan: `npm run generate:readme`

### Validate gagal
→ Jalankan: `npm run check` untuk melihat detail error

## Scripts Available

```bash
npm run setup              # Initial setup wizard
npm run generate           # Generate profile + README (requires portrait.png)
npm run generate:readme    # Generate hanya README (without portrait)
npm run generate:hero      # Generate hanya hero SVG assets
npm run activity           # Update recent activity section
npm run validate / check   # Validate configuration
```

---

**Tips:** Setelah Anda punya portrait.png, cukup push ke repo dan workflow akan otomatis generate semuanya! 🚀
