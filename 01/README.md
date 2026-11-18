# Materi Minggu 1: Pengenalan Sistem Terdistribusi dan Terdesentralisasi

```text
Materi Minggu 1: Pengenalan Sistem Terdistribusi dan Terdesentralisasi
AI yang digunakan: DeepSeek V4.1 Flash Free
Prompt: Rangkum materi 01--pengenalan.pdf (25 slide) menjadi catatan Markdown berbahasa Indonesia yang mencakup tujuan pembelajaran, definisi, arsitektur, karakteristik, perbandingan sistem terdistribusi vs terdesentralisasi, studi kasus, CAP theorem, konsistensi data, tantangan, dan tren.
Bagian yang disesuaikan dari keluaran prompt ada pada: struktur heading, tabel perbandingan (terdistribusi vs terdesentralisasi, AP vs CP), daftar istilah, dan perapian bahasa.
```

> **Mata kuliah:** Sistem Terdistribusi dan Terdesentralisasi (FIF25002T, 3 SKS)
> **Program studi:** Informatika — Fakultas Teknologi Informasi, UTDI
> **Dosen:** Dr. Bambang Purnomosidi D. P.
> **Sumber:** materi kuliah pertemuan 1 (`01--pengenalan.pdf`)

## Tujuan Pembelajaran

Setelah materi ini, mahasiswa mampu:

- menjelaskan konsep sistem terdistribusi dan sistem terdesentralisasi;
- membedakan keduanya;
- menyebutkan contoh penerapan nyata;
- menyebutkan tantangan serta tren terbaru di bidang ini.

## 1. Mengapa Penting?

- Pertumbuhan data dan pengguna sangat besar.
- Layanan modern menuntut **skalabilitas**.
- Sistem harus **fault-tolerant**.
- Performa dan ketersediaan 24/7.
- Tanpa sistem terdistribusi dan terdesentralisasi, layanan seperti Google, Netflix, dan Blockchain tidak mungkin ada.

**Skalabilitas** — kemampuan sistem/jaringan/proses untuk tumbuh menangani peningkatan beban kerja, pengguna, atau permintaan tanpa mengorbankan kinerja.

**Sistem fault-tolerant** — sistem yang tetap beroperasi normal meskipun sebagian komponennya (hardware/software) gagal.

## 2. Sistem Terdistribusi

> "A collection of independent computers that appears to its users as a single coherent system."
> — Andrew S. Tanenbaum & Maarten van Steen (2007)

Ciri utama:

- terdiri dari **komponen independen**;
- berkomunikasi **melalui jaringan**;
- **transparansi**: lokasi, akses, replikasi, dan kegagalan.

### Arsitektur Dasar

| Arsitektur | Ciri |
| --- | --- |
| **Client–Server** | Client meminta layanan, server menyediakan; kontrol terpusat |
| **Peer-to-Peer (P2P)** | Setiap node bisa menjadi client sekaligus server |
| **Hybrid** | Gabungan keduanya; biasanya ada server untuk koordinasi/indeks, data tersebar di peer |

### Karakteristik

1. Transparansi lokasi
2. Skalabilitas
3. Fault tolerance
4. Kinerja tinggi
5. Heterogenitas

## 3. Sistem Terdesentralisasi

- **Sentralisasi:** satu titik kontrol.
- **Desentralisasi:** kontrol terdistribusi, **tidak ada single point of failure**.
- Keputusan diambil secara kolektif melalui **konsensus**.
- Contoh: **Blockchain, DNS, BitTorrent**.

## 4. Terdistribusi vs Terdesentralisasi

- **Distribusi** berfokus pada **pembagian beban kerja**.
- **Desentralisasi** berfokus pada **pembagian kontrol**.
- Keduanya saling terkait, tetapi berbeda fokus, dan bersama-sama menjadi fondasi teknologi modern.

| Aspek | Terdistribusi | Terdesentralisasi |
| --- | --- | --- |
| Fokus | Pembagian beban kerja | Pembagian kontrol |
| Titik kontrol | Bisa tetap terpusat secara logis | Tidak ada otoritas tunggal |
| Pengambilan keputusan | Ditentukan koordinator/server | Konsensus antar node |
| Contoh | Google File System, MinIO Object Storage (kini di-fork menjadi Silo) | Blockchain, DNS, BitTorrent |

### Studi Kasus Sistem Terdistribusi

- **Google File System / HDFS** — penyimpanan data berskala besar
- **Apache Kafka, Apache Pulsar** — messaging & streaming
- **Netflix, Twitch, YouTube** — streaming media
- **Instagram, Threads, Facebook, TikTok** — media sosial

### Studi Kasus Sistem Terdesentralisasi

- **Blockchain** — Bitcoin, Ethereum, Algorand, Sui, Near, Aptos
- **DNS** (Domain Name System)
- **BitTorrent**

## 5. CAP Theorem (Brewer's Theorem, 2000)

- **Consistency** — setiap operasi baca mengembalikan penulisan terbaru atau error.
- **Availability** — setiap permintaan ke node yang tidak gagal menerima respons non-error (walau bukan data terbaru).
- **Partition Tolerance** — sistem tetap beroperasi meskipun komunikasi antar-node terputus/terfragmentasi.

Pada *distributed data store* tidak mungkin memperoleh **C + A** sekaligus, karena **partisi selalu mungkin terjadi**. Saat partisi berlangsung, perancang harus memilih **AP** atau **CP** (meski sistem dapat *auto-healing* setelah partisi selesai).

| Pilihan | Makna | Konsekuensi | Contoh |
| --- | --- | --- | --- |
| **AP** (Availability + Partition Tolerance) | Permintaan data selalu dilayani | Mengorbankan konsistensi (data bisa tidak sinkron) | MongoDB |
| **CP** (Consistency + Partition Tolerance) | Read/write ditolak saat partisi | Mengorbankan ketersediaan | Apache Cassandra |

## 6. Konsistensi Data

- **Strong consistency** — hasil baca selalu sama (selalu data terbaru). Contoh: sistem **perbankan**.
- **Eventual consistency** — pada akhirnya konsisten. Contoh: **media sosial**.

## 7. Tantangan

- **Latency & throughput** — latency: berapa lama diproses; throughput: berapa banyak diproses.
- **Keamanan** — DDoS, **Sybil attack**.
- **Kompleksitas manajemen node**.
- **Governance** (tata kelola) pada sistem terdesentralisasi.

**Sybil attack** — serangan dengan membuat banyak identitas palsu (akun/node/pseudonim, bisa ribuan) sekaligus untuk mendominasi pengaruh, suara, atau reputasi jaringan. Umum pada sistem P2P dan blockchain; penyerang dapat memanipulasi sistem, merusak integritas, dan mengakses informasi sensitif. Nama "Sybil" berasal dari buku tahun 1973 tentang seorang perempuan dengan *multiple identity disorder*.

## 8. Tren Masa Depan

- **Cloud-native** (Kubernetes, Docker)
- **Edge & Fog Computing**
- **Web3 & DeFi**
- **Federated Data & Learning** (AI terdistribusi)

## 9. Ringkasan

- Sistem terdistribusi = **berbagi beban kerja**.
- Sistem terdesentralisasi = **berbagi kontrol**.
- Keduanya saling terkait tetapi berbeda fokus.
- Keduanya menjadi fondasi teknologi modern.

## 10. Bahan Diskusi

1. Mengapa dunia semakin bergerak menuju distribusi dan desentralisasi?
2. Contoh sehari-hari apa yang paling terasa terkait hal ini?

## Daftar Istilah

| Istilah | Arti singkat |
| --- | --- |
| Skalabilitas | Kemampuan menangani beban yang meningkat tanpa penurunan kinerja |
| Fault tolerance | Tetap beroperasi meski sebagian komponen gagal |
| Transparansi | Pengguna tidak perlu tahu detail lokasi, replikasi, atau kegagalan |
| Consensus | Mekanisme kesepakatan kolektif antar node tanpa otoritas pusat |
| CAP theorem | Trade-off Consistency, Availability, Partition Tolerance |
| Sybil attack | Serangan dengan banyak identitas palsu |
