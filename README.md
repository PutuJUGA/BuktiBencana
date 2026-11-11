# BuktiBencana

Aplikasi mobile untuk **peringatan dini bencana** dan **dokumentasi kerusakan
anti-manipulasi** berbasis komunitas. Proyek Tugas Besar Pemrograman Mobile,
mendukung **SDG 11 (Sustainable Cities and Communities)**.

## Latar Belakang

Saat bencana, tanda bahaya awal sering terlambat diketahui, dan setelahnya
korban kesulitan membuktikan kerusakan untuk mengajukan bantuan. BuktiBencana
menjawab dua masalah itu dalam satu aplikasi.

## Fitur Utama

### Sebelum / saat bencana (peringatan dini)

- Pelaporan tanda bahaya (retakan, tanggul bocor, genangan naik) dengan foto
  ber-watermark koordinat dan waktu
- Peta interaktif laporan warga (`react-native-maps`)
- Penggabungan laporan berdekatan menjadi zona rawan dan level waspada
  (Haversine + RxJS)
- Geofencing: peringatan saat pengguna memasuki zona rawan

### Sesudah bencana (dokumentasi bukti)

- Pengambilan foto langsung dari kamera dengan watermark koordinat dan waktu
- Hash integritas untuk mendeteksi perubahan file setelah diambil
- Penyimpanan paket bukti di Scoped Storage Document Vault (`expo-file-system`)
- Kunci dan data sensitif terenkripsi (`expo-secure-store`)

### Verifikasi

- Peran Verifikator (RT/relawan) untuk memvalidasi laporan warga

## Teknologi

| Kategori         | Library                                       |
| ---------------- | --------------------------------------------- |
| Framework        | React Native 0.88 (Expo SDK 58) + Expo Router |
| State management | Zustand (Unidirectional Data Flow)            |
| Reaktif          | RxJS                                          |
| Peta & lokasi    | `react-native-maps`, `expo-location`          |
| Keamanan         | `expo-secure-store`, `expo-crypto`            |
| Penyimpanan      | `expo-file-system`                            |
| Animasi          | `react-native-reanimated`                     |

## Arsitektur

- **State management:** Zustand dengan Unidirectional Data Flow
- **Separation of Concerns:** custom hooks terpisah dari UI screen
- **Pipeline reaktif:** RxJS (`debounceTime`, `distinctUntilChanged`, `switchMap`)
- **Offline-first** dengan graceful fallback

## Menjalankan Proyek

```bash
git clone https://github.com/PutuJUGA/BuktiBencana.git
cd BuktiBencana
npm install
npx expo start
```

Perintah pengembangan lainnya:

```bash
npx expo lint       # linting
npx tsc --noEmit    # type check
npx expo-doctor     # diagnosis dependensi & konfigurasi
```

> **Catatan:** Library dengan kode native yang tidak dibundel di Expo Go
> memerlukan development build:
> `npx expo run:android` / `npx expo run:ios`, atau
> `npx eas-cli@latest build --profile development`.

## Catatan

Data pada demo bersifat simulasi. Hash membuktikan file tidak diubah setelah
diambil, bukan keabsahan hukum suatu klaim.

## Tim

| Nama                         | NIM             |
| ---------------------------- | --------------- |
| Putu Bawa Givrant Januarta   | 202410370110474 |
| Muhamad Michael Zaim Al Izzy | 202410370110447 |
