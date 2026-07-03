# Workshop: Frontend–Backend Integration & Debugging

Materi praktik untuk workshop **Frontend–Backend Integration & Debugging Mastery**, menggunakan proyek **creditappdemo** sebagai studi kasus.

## File

| File | Untuk siapa | Isi |
|------|-------------|-----|
| [`playwright-intro.md`](./playwright-intro.md) | Peserta | **Mulai di sini** — 3 latihan Playwright dasar sebelum use case nyata |
| [`frontend-backend-integration-practice.md`](./frontend-backend-integration-practice.md) | Peserta | Lab, quiz, dan skenario debugging langkah demi langkah |

**Fasilitator:** kunci jawaban ada di `answer-key.md` — file **tidak** di-commit ke repo (lihat bagian Fasilitator di bawah).

## Prasyarat peserta

```bash
cd creditappdemo
npm install
npx playwright install chromium   # WAJIB untuk tes E2E (tidak otomatis dari npm install)
cp .env.example .env
npm run dev
```

Buka http://localhost:5173 — alur demo: **Formulir → Verifikasi dokumen → Scoring → Hasil**.

> **Tes Playwright gagal dengan `Executable doesn't exist`?**  
> Jalankan `npx playwright install chromium` sekali per mesin, lalu ulangi `npm run test:e2e:intro`.

## Tes otomatis

### Intro Playwright (45–60 menit, sebelum lab integrasi)

```bash
npx playwright install chromium   # wajib sekali, sebelum tes pertama
npm run test:e2e:intro            # harapan: 4 passed, 3 skipped
```

Panduan: [`playwright-intro.md`](./playwright-intro.md).

### Use case nyata (Sesi 2 & 4)

```bash
npm install
npx playwright install chromium
npm run test:e2e          # intro + use case (01–03)
npm run test:e2e:ui       # mode interaktif
npm run test:e2e:trace    # dengan trace untuk debugging
```

| Folder / file | Isi |
|---------------|-----|
| [`tests/workshop/intro/`](../../tests/workshop/intro/) | Latihan 1–3: page load, form, navigasi langkah |
| [`tests/workshop/01–03`](../../tests/workshop/) | Happy path, env config, network failure |

## Mapping ke slide workshop

| Sesi slide | Topik | Lab di practice doc |
|------------|-------|---------------------|
| 1 | Integration Reality & Network Fundamentals | Lab 1.1 – 1.3 |
| 2 | CORS, Env Config, Reverse Proxy | Lab 2.1 – 2.4 + Playwright config tests |
| 3 | Cross-Layer Debugging (Correlation ID & Logs) | Lab 3.1 – 3.3 |
| 4 | Systematic Debugging + Pipeline | Lab 4.1 – 4.2 + case study |

## Fasilitator — kunci jawaban (tidak di repo)

File `docs/workshop/answer-key.md` ada di `.gitignore` agar tidak ikut ter-push ke peserta.

```bash
# Salin template lalu isi dari materi internal fasilitator
cp docs/workshop/answer-key.md.example docs/workshop/answer-key.md
```

Distribusikan `answer-key.md` lewat channel internal (Drive, wiki tim, dll.), bukan lewat git publik.

> **Catatan:** Jika file pernah ter-push sebelumnya, commit berikutnya akan menghapusnya dari repo, tetapi riwayat git lama mungkin masih menyimpan isinya. Untuk konten sangat sensitif, pertimbangkan rotasi jawaban atau purge history.
