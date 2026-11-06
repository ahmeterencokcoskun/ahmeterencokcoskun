<div align="center">

# **Ahmet Eren Çokcoşkun (Eren)**
**Elektrik-Elektronik Mühendisliği Araştırmacısı** · **A Sınıfı Amatör Telsizci (`TA7CAE`)** · **Demiryolu Sinyalizasyon ve Kontrol**

[![Çağrı İşareti](https://img.shields.io/badge/Çağrı_İşareti-TA7CAE%20%7C%20YM7XNN-critical?style=flat-square&logo=rss&logoColor=white)](#)
[![Zamir](https://img.shields.io/badge/Zamir-lokomotif%20%2F%20lokomotifler-blue?style=flat-square)](#)
[![Ortam](https://img.shields.io/badge/Ortam-WSL2%20Ubuntu%2026.04%20%7C%20CachyOS-1793D1?style=flat-square&logo=linux&logoColor=white)](#)
[![Topluluk](https://img.shields.io/badge/Reddit-r%2FtransitTurkey%20Mod-FF4500?style=flat-square&logo=reddit&logoColor=white)](https://www.reddit.com/r/transitTurkey/)
[![Konum](https://img.shields.io/badge/QTH-Kayseri%20%2F%20İstanbul%20(KM78)-success?style=flat-square)](#)

</div>

---

### `whoami` // Akademik ve Teknik Kimlik

```yaml
Araştırmacı     : Ahmet Eren Çokcoşkun ("Eren")
Kurum & Bölüm   : Nuh Naci Yazgan Üniversitesi — Elektrik-Elektronik Mühendisliği (Lisans, 4. Sınıf)
Çağrı İşaretleri: TA7CAE (Kişisel - A Sınıfı) | YM7XNN (Kulüp İstasyonu Yöneticisi)
QTH / Grid      : Talas, Kayseri (38.72°N, 35.48°E — KM78) & İstanbul
Araştırma Odağı : [ "Hesaplamalı Elektromanyetik ve İyonosferik Plazma Fiziği",
                    "İstatistiki Sinyal İşleme (DSP) ve Parametre Kestirimi",
                    "Emniyet-Kritik Demiryolu Sinyalizasyonu (ETCS / SIL-4 Formal Doğrulama)",
                    "Havacılık Gözetimi ve Fiziksel Katman (PHY) Güvenliği" ]
```

---

### Akademik Araştırma Sütunları ve Mühendislik Çıktıları

#### 1. İyonosferik Plazma Fiziği, Elektromanyetik Yayılım ve SDR Tabanlı Sondaj
* **Lisans Bitirme Tezi (Capstone Research):** **HF Sayısal Modları (FT8/WSPR) ve SDR Kullanılarak Çok-Bantlı Fırsatçı İyonosferik Algılama: $`\text{D}, \text{E}, \text{E}_s, \text{F}_1, \text{F}_2`$ Katman Dinamikleri ve Mikro-Doppler Kestirimi.**
* **Magneto-İyonik Ortam Modellemesi:** Orta enlem iyonosferinde Dünya'nın jeomanyetik alanı $`\mathbf{B}_0`$ ve elektron-nötr çarpışma frekansı $`\nu(h)`$ altında yayılan elektromanyetik dalgaların **Appleton-Hartree** ve kinetik **Sen-Wyller** formülasyonları ile incelenmesi; Sıradan (O-Mode) ve Olağanüstü (X-Mode) dalga kırılma indislerinin $`\tilde{n}`$ ve sapmalı/sapmasız sönümleme katsayılarının $`\alpha = -\operatorname{Im}(k)`$ sayısal analizi:

```math
\tilde{n}^2 = (\mu - j\chi)^2 = 1 - \frac{X}{1 - jZ - \frac{Y_T^2}{2(1 - X - jZ)} \pm \sqrt{\frac{Y_T^4}{4(1 - X - jZ)^2} + Y_L^2}}
```

* **Zamanla Değişen Kanal Karakterizasyonu (Watterson Modeli — ITU-R F.1487):** Çok-yollu (multipath) gökyüzü dalgası yayılımında kanal dürtü yanıtı $`h(\tau, t)`$ ve **Kanal Saçılma Fonksiyonu (Scattering Function)** $`S(\tau, f_d)`$ kestirimi; Gezinen İyonosferik Düzensizlikler (TID) ve Ani İyonosferik Bozulmaların (SID / Solar Flare) alt-paketsel faz türevi üzerinden tespiti:

```math
h(\tau, t) = \sum_{m=1}^{M} G_m(t) \, e^{j 2\pi f_{d,m}(t) t} \, \delta(\tau - \tau_m(t)), \qquad f_d(t) = \frac{1}{2\pi} \frac{d}{dt}\left[\operatorname{unwrap}\left(\arctan\frac{Q(t)}{I(t)}\right)\right]
```

* **Geliştirilen Modüller & Mühendislik Çıktıları (Artifacts):**
  * `iono-sense-ta7cae` (`plasma_physics.py`, `watterson_simulator.py`, `sdr_hardware.py`): Kayseri ($`38.72^\circ\text{N}, 35.48^\circ\text{E}`$, $`B_0 = 48.2\ \mu\text{T}`$, $`f_H \approx 1.35\text{ MHz}`$) merkezli Chapman çok-katmanlı elektron yoğunluğu çözücüsü, Appleton-Hartree vs. sapmasız $`1/f^2`$ yaklaşımı hata bütçesi (dB Discrepancy) simülatörü ve `SoapySDR` tabanlı RSPdx zaman bölüşümlü bant atlama ($`3.5, 7, 14, 28, 50\text{ MHz}`$) motoru.

---

#### 2. İstatistiki Sinyal İşleme (DSP), Haberleşme Teorisi ve Telemetri
* **Fiziksel Katman (PHY) Demodülasyon ve Kod Çözme:** Düşük $`\text{SNR}`$ ($`-20\text{ dB}`$ altı AWGN ve Middleton Class-A darbeli gürültü) rejimlerinde çalışan `8-GFSK` (FT8), `4-FSK` (WSPR / DMR Tier II), `dPMR`, `NXDN48` ve `STANAG 4285` dalga şekillerinin incelenmesi.
* **Kanal Kodlama ve Gökyüzü BER Analizi:** $`(174, 91)`$ LDPC (Sum-Product / Belief Propagation) ve evrişimsel (Viterbi / Sequential) kod çözücülerde yeniden kodlama (re-encoding) tekniğiyle canlı gökyüzü sinyallerinden **Pre-FEC / Post-FEC Bit Hata Oranı (BER)** ve **EVM** eğrilerinin çıkarılması; Costas dizileriyle 2B zaman-frekans uyumlu filtreleme (Matched Filtering).
* **Havacılık Gözetimi (Mode-S / ADS-B):** $`1090\text{ MHz}`$ bandında Varış Zamanı Farkı (**TDoA / MLAT**), Cramér-Rao Alt Sınırı (CRLB) konum doğrulaması ve RF ön kat kusurlarına dayalı fiziksel katman güvenliği.
* **Geliştirilen Modüller & Laboratuvar Çıktıları (Artifacts):**
  * `dsp_core.py` & `ber_engine.py`: $`12\text{ kHz}`$ sayısal aşağı çevirici (DDC) ve FIR seyreltme hattı, $`7 \times 7`$ Costas 2B çapraz korelasyon senkronizatörü, ortak-mod TCXO termal kayma kalibratörü ve Savitzky-Golay türev tabanlı anlık mikro-Doppler çıkarıcı.
  * **Aktif RF Gözetim Düğümü:** SDRplay RSPdx (14-bit ADC), RTL-SDR Blog V4, $`1.8\text{--}52\text{ MHz}`$ $`H`$-alanı aktif ekranlı manyetik loop anten ve Raspberry Pi üzerinde 7/24 çalışan `readsb`, `PiAware`, `adsbexchange-feed`, `fr24feed` telemetri altyapısı.

---

#### 3. Demiryolu Sinyalizasyon, Kontrol Teorisi ve Emniyet-Kritik Sistemler
* **Avrupa Tren Kontrol Sistemi (ETCS Seviye 1/2/3 — UNISIG SUBSET-026):** Hareket Yetkisi (Movement Authority - MA), dinamik hız-mesafe frenleme eğrileri (Braking Curves) ve **Eurobalise (BTM — SUBSET-036)** $`27.095\text{ MHz}`$ manyetik kuplaj / $`4.23\text{ MHz}`$ FSK uplink sinyal modellemesi.
* **SIL-4 Elektronik Anklaşman (CENELEC EN 50128 / EN 50129):** İstasyon makas ve sinyal topolojilerinin yönlü çizgeler (Directed Graphs), Sonlu Durum Makineleri (FSM) ve **Petri Ağları (Petri Nets)** ile modellenmesi; kilitlenme (deadlock) ve tezat rota çakışmalarının formal yöntemlerle (Model Checking) doğrulanması.
* **Çok-Sensörlü Tren Odometrisi ve Durum Kestirimi:** Tekerlek kayması/patinajı (slip/slide) ve tünel içi GNSS kesintileri altında tekerlek enkoderi, IMU ve sanal balise verilerinin **Genişletilmiş Kalman Filtresi (EKF)** ile füzyonu:

```math
\hat{\mathbf{x}}_{k \mid k} = \hat{\mathbf{x}}_{k \mid k-1} + \mathbf{K}_k \left( \mathbf{z}_k - h(\hat{\mathbf{x}}_{k \mid k-1}) \right), \qquad \mathbf{K}_k = \mathbf{P}_{k \mid k-1}\mathbf{H}_k^T\left(\mathbf{H}_k\mathbf{P}_{k \mid k-1}\mathbf{H}_k^T + \mathbf{R}_k\right)^{-1}
```

* **Geliştirilen Modüller & Sektörel Çalışmalar (Artifacts):**
  * İstasyon makas sahaları için çizge teorisi tabanlı rota kilitleme/yan koruma (flank protection) mantık doğrulayıcısı, $`25\text{ kV } 50\text{ Hz}`$ AC kataner empedans/EMI analizleri ve TCDD / AYGM / UHDGM / UÇİM şebeke araştırmaları. Türkiye ulaşım ve raylı sistemler topluluğu **[r/transitTurkey](https://www.reddit.com/r/transitTurkey/)** moderatörü.

---

### Çalışılan Uluslararası Standartlar ve Protokoller Matrisi

| Disiplin | Matematiksel / Algoritmik Odak | Referans Standartlar & Protokoller |
| :--- | :--- | :--- |
| **İyonosfer & RF Yayılımı** | Appleton-Hartree, Sen-Wyller, 2D Ray-Tracing, Watterson Kanalı | `ITU-R P.533`, `ITU-R F.1487`, `IRI-2020` |
| **Sayısal Haberleşme & DSP** | Costas Matched Filter, LDPC $`(174,91)`$, Faz Açma, Hilbert, STFT | `FT8`, `WSPR`, `STANAG 4285`, `MIL-STD-188-141 (ALE)`, `DMR Tier II` |
| **Demiryolu Sinyalizasyon** | Petri Nets, Formal Verification, EKF Odometri, Ray Devresi RLC | `CENELEC EN 50126/50128/50129 (SIL-4)`, `ETCS SUBSET-026/036`, `GSM-R / FRMCS` |
| **Havacılık & Telemetri** | TDoA Multilaterasyon (MLAT), CRLB, PPM Sembol Çözümleme | `ICAO Annex 10`, `RTCA DO-260B (1090ES ADS-B / Mode-S)` |

---

### Hesaplama ve Donanım Altyapısı

| Sistem | Ortam & Donanım Spesifikasyonu |
| :--- | :--- |
| **Ana İş İstasyonu (`erenix@DESKTOP-LLPQDR9`)** | Windows 11 & **WSL2 (`Ubuntu 26.04.1 LTS`, Kernel 6.18, WSLg Wayland)** · Intel Core i7-13700F (24 Threads) · NVIDIA GeForce RTX 4070 Ti (12 GB VRAM) · 27" 1440p + 24" 1080p (Dikey) |
| **Mobil Saha Terminali (`host: lokomotif`)** | Acer Spin · **CachyOS Linux (Arch Base)** · Wayland · Openbox · Zen Browser |
| **CAS & Sembolik Hesaplama** | **TI-Nspire CX II-T CAS (`Ndless` SDK)** · Sembolik cebir, diferansiyel denklem çözümü ve devre/sinyal analizi |
| **Yazılım, Simülasyon & Dizgi** | Python (`NumPy`, `SciPy`, `PyTorch`, `SoapySDR`), MATLAB, C/C++, **Typst** (`.typ`), **LaTeX** (`.tex`) |

<div align="center">

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![MATLAB](https://img.shields.io/badge/MATLAB-0076A8?style=for-the-badge&logo=mathworks&logoColor=white)
![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
![Ubuntu](https://img.shields.io/badge/WSL2_Ubuntu_26.04-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Arch](https://img.shields.io/badge/CachyOS_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white)
![LaTeX](https://img.shields.io/badge/LaTeX-008080?style=for-the-badge&logo=latex&logoColor=white)
![Typst](https://img.shields.io/badge/Typst-239DAD?style=for-the-badge&logo=typst&logoColor=white)
![Raspberry Pi](https://img.shields.io/badge/Raspberry_Pi-A22846?style=for-the-badge&logo=raspberry-pi&logoColor=white)

</div>

---

<details>
<summary><b>🎧 Alt-Taşıyıcı Telemetrisi (Mesai Dışı İlgi Alanları, Simülasyon & Akustik)</b></summary>
<br>

* **Kimlik & Zamirler:** `lokomotif / lokomotifler` (`he/lokomotif`)
* **Strateji & Endüstriyel Simülasyon:** *Hearts of Iron IV* (+1000 saat, 1936 Türkiye stratejik-endüstriyel analizleri), *Minecraft* (`GregTech: New Horizons` & `Railcraft` lojistik/otomasyon ağları), *League of Legends* (Support: Leona, Bard, Thresh, Nami, Yuumi, Aurelion Sol, Kindred), *Vampire Survivors*.
* **Frekans & Akustik (Hi-Fi):** Yüksek çözünürlüklü ses ekipmanları ile Türkçe Underground Hip-Hop / Boom-Bap (Farazi, Kayra, Şam, Sansar Salvo, Sorgu, Da Poet, Kodes Kahra, Karaçalı, Ceg, Motive, Ais Ezhel, Şehinşah, GRi, Se7en of 34, Orchi) & Eminem, Dido, Rihanna.

</details>

---

<div align="center">

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=ahmeterencokcoskun&show_icons=true&theme=tokyonight&hide_border=true" height="165" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=ahmeterencokcoskun&layout=compact&theme=tokyonight&hide_border=true" height="165" />
</p>

**73 de `TA7CAE` / `YM7XNN`** — *İyi sinyaller ve açık makaslar!*

</div>
