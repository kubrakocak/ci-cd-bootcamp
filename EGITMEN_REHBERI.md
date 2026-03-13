# 🎓 Eğitmen Rehberi — NEXUS Portal Serüveni CI/CD Bootcamp

## Konsept Özeti

Bu bootcamp, CI/CD kavramlarını **sıfır kodlama gerektiren** bir portal
macerası oyunuyla öğretir. Katılımcılar 10 farklı bulmacayı (Polybius
ızgarası, matris+işlem, 8-bit binary, gizli dosya+tuzak, yol izleme,
Vigenère şifresi, filtrelenmiş akrostiş, Mors+parazit, çoklu mantık
eleme ve meta-bulmaca) çözer ve cevaplarını basit bir dosyaya yazar.
Her commit otomatik testleri tetikler. Tüm cevaplar doğru olduğunda
site otomatik deploy olur.

**Neden bu format?**
- Kod yazmak bilmeyenler de katılabilir (sadece bulmaca çöz + cevap yaz)
- Yapay zekaya yapıştırarak çözmek zor (gizli dosya, tuzaklar, repo keşfi)
- CI/CD döngüsünü gerçekten deneyimliyorlar (commit → test → deploy)
- Hikaye ve rekabet motivasyonu yüksek tutuyor

## Hikaye

**NEXUS Core Crew** — ALKÜ'nün 7 efsanevi mühendisi:
- **Kaya** (Takım Lideri), **İrem** (Şifre Uzmanı), **Mehmet** (Sistem Mimarı),
  **Okan** (Güvenlik Uzmanı), **Serhat** (Veri Analisti), **Nigina** (YZ Araştırmacısı),
  **Gülşah** (Topluluk Yöneticisi)

ALKÜ'deki zamanları dolmak üzere, LIFE görevleri onları yeni ufuklara
çağırıyor. Ayrılmadan önce yerlerini alacak yeni NEXUS koruyucularını
bulmak için 10 portal tasarlamışlardır.

## Cevap Anahtarı (Sadece Eğitmen İçin!)

```
Portal 1  — MERHABA    (Polybius: 33=M, 15=E, 42=R, 23=H, 11=A, 12=B, 11=A)
Portal 2  — ALKÜ       (6×6 Matris: (1,B)=4-3=1→A, (2,D)=15-3=12→L,
                         (4,C)=14-3=11→K, (5,E)=24-3=21→U)
Portal 3  — CESARET    (8-bit Binary: 00000011=3→C, 00000101=5→E,
                         00010011=19→S, 00000001=1→A, 00010010=18→R,
                         00000101=5→E, 00010100=20→T)
Portal 4  — EVREN      (vakalar/gizli-portal/bolum-3-guvenlik/kasalar/kasa-7/icerik.txt
                         Labirentte 4 sahte şifre var: YILDIZ (raf-A),
                         COSMOS (alarm kaydı), GALAKSI (kasa-3), ve boş kasa-5.
                         İpucu zinciri: mesajlar.txt → sohbet-okan.txt →
                         okan-profil.txt → kasa-7)
Portal 5  — ROTA       (Yol izleme: (1,1)→sağa3→(1,4)=R, aşağı2→(3,4)=O,
                         sola1→(3,3)=T, aşağı1→(4,3)=A)
Portal 6  — ANAHTAR    (Vigenère, anahtar=NEXUS:
                         N→N=A, R→E=N, X→X=A, B→U=H, L→S=T, N→N=A, V→E=R)
Portal 7  — LABİRENT   (Filtrelenmiş akrostiş: 3 şekil grubu (◆ ■ ●),
                         ◆ satırları → L-A-B-İ-R-E-N-T (doğru cevap),
                         ■ satırları → K-A-Y-B-O-L-M-A (tuzak kelime!)
                         Bilmece: "düz duran=■ aldatır, eğik duran=◆ aydınlatır")
Portal 8  — ARAYIŞ     (Parazitli Mors: tek sıra sinyaller →
                         .-=A, .-.=R, .-=A, -.--=Y, ..=I, ...=S)
Portal 9  — REHBER     (10 muhafız, 5 koşul:
                         Güç>6: REHBER,USTA,MENTOR,ŞÖVALYE,KOMUTAN,SAVAŞÇI →
                         Yaş<200: REHBER,USTA,ŞÖVALYE,SAVAŞÇI →
                         Seviye≠5: REHBER,USTA,SAVAŞÇI →
                         Bölge=Kuzey/Güney: REHBER,SAVAŞÇI →
                         Ad<7 harf: REHBER)
Portal 10 — MACERALAR  (İlk harfler: M+A+C+E+R+A+L+A+R)
```

### Core Crew'un Gizli Mesajı
Her doğru cevap bir kelime açar:
```
Portal  1 → "Her"          Portal  6 → "adımla"
Portal  2 → "büyük"        Portal  7 → "başlar"
Portal  3 → "miras"        Portal  8 → "NEXUS"
Portal  4 → "cesur"        Portal  9 → "sizinle"
Portal  5 → "bir"          Portal 10 → "büyür"

→ "Her büyük miras cesur bir adımla başlar, NEXUS sizinle büyür."
```

Son reveal: "Core Crew'un aradığı yeni koruyucular... SİZSİNİZ!"

## Ön Hazırlık (1 gün önce)

### Template Repo
1. GitHub'da `bootcamp` adlı public repo oluşturun
2. Dosyaları yükleyin, `cevaplar.py`'deki cevapları boşaltın
3. **Settings → Actions → General** → "Allow all actions" etkin olmalı
4. Kendiniz fork edip tüm akışı test edin

### Katılımcılara Gönderin
- GitHub hesabı açsınlar (https://github.com)
- Tarayıcıdan çalışacaklar, başka kurulum gerekmez!

## Bootcamp Planı (~90 dk)

### 🕐 Bölüm 1 — Giriş + Kurulum (30 dk)

| Süre | Aktivite |
|------|----------|
| 00-10 | **CI/CD Nedir?** Günlük hayattan benzetme: "Yemek tarifi yazdın, her değişiklikte otomatik tadım yapılıyor. Lezzetliyse otomatik servise çıkıyor." |
| 10-18 | **Canlı Demo:** Template repo'yu göster, bilerek yanlış cevap yaz, Commit changes ile kaydet, pipeline'ın KIRMIZI olduğunu göster. Sonra doğru cevabı yaz, YEŞİL pipeline + deploy |
| 18-25 | **Herkes Fork Etsin:** Adım adım ekranı paylaşarak fork → Settings → Pages → GitHub Actions |
| 25-30 | **İlk Portal Birlikte:** Portal 1'i birlikte açın, Polybius ızgarasını anlatın, çözün, cevaplar.py'yi ✏️ ile düzenleyin, Commit changes |

### 🕐 Bölüm 2 — Portal Çözme (45 dk)

| Süre | Aktivite |
|------|----------|
| 00-05 | **Kurallar:** Her portal bağımsız, istediğinden başla. Her commit'te Actions sekmesini kontrol et |
| 05-40 | **Serbest Çalışma:** Katılımcılar kendi hızlarında çözer |
| 40-45 | **Durum Kontrolü:** Kim kaçıncı portalda? Scoreboard güncelleme |

**Eğitmen Stratejisi:**
- Sınıfta dolaşın, tıkananlara ipucu verin (çözümü DEĞİL!)
- 5. dakikada: "Portal 4'te `gizli-portal/` labirentini keşfedin, dosyaları sadece açmayın — kimin yazdığına dikkat edin!" genel ipucu
- 10. dakikada: "Portal 6'daki Vigenère tablosunu satır satır takip edin" ipucu
- 15. dakikada: "Portal 7'de ◆ ve ■ şekillerine dikkat — Kaya'nın bilmecesi hangisini seçeceğinizi söylüyor!" hatırlatma
- 20. dakikada: "Portal 9'da 5 koşulu sırayla uygulayın, acele etmeyin" ipucu
- Hızlı çözenleri yavaş olanlara eşleyin (pair çalışma)
- **Canlı scoreboard** tutun (aşağıdaki şablona bakın)

**Beklenen İlerleme (~20-25 dk toplam çözüm süresi):**
- Portal 1-2: Herkes 3-5 dk'da çözer
- Portal 3-5: 5-10 dk, binary ve yol izleme biraz zaman alır
- Portal 6-8: 8-12 dk, Vigenère ve filtreleme en zorları
- Portal 9: 5-8 dk, dikkatli eleme gerektirir
- Portal 10: Diğer 9'u çözmüş olanlar 1-2 dk'da çözer

### 🕐 Bölüm 3 — Deploy + Kapanış (15 dk)

| Süre | Aktivite |
|------|----------|
| 00-05 | **GitHub Pages Kontrolü:** Pages zaten Bölüm 1'de kuruldu, deploy durumunu kontrol edin |
| 05-10 | **İlk Deploy!** Tüm portalları çözmüş birinin sitesini canlı gösterin |
| 10-15 | **Kapanış:** Deploy URL'lerini paylaşın, NEXUS'a hoş geldiniz! |

## Olası Sorunlar

| Sorun | Çözüm |
|-------|-------|
| Fork edemiyor | Email doğrulaması gerekli olabilir |
| Dosya düzenlenemiyor | Fork ettiğinden emin olsun, orijinal repoda düzenleme yapılamaz |
| Commit yapamıyor | GitHub hesabında email doğrulaması gerekli olabilir |
| Actions çalışmıyor | Settings → Actions → "Allow all" kontrol |
| Pages deploy olmuyor | Settings → Pages → Source: "GitHub Actions" seçili mi? |
| Portal 4: Anahtarı bulamıyor | `gizli-portal/` klasöründe 3 bölüm var. İletişim bölümündeki yazışmaları okusunlar — Okan kasasından bahsediyor. Güvenlik birimi → personel → Okan'ın profili → atanmış kasa numarasını bulsunlar |
| Portal 6: Vigenère anlaşılmıyor | Tabloyu satır satır takip etmelerini söyleyin. Anahtar satırında şifreli harfi bul, sütun başlığı cevap |
| Portal 7: Yanlış şekli takip ediyor | "Kaya'nın bilmecesini tekrar oku — ◆ ve ■ arasındaki fark ne? Hangisi 'eğik duruyor'?" ipucu verin. KAYBOLMA çıktıysa ■ takip etmişler — ◆ denesinler! |
| Portal 8: Parazit ayıklayamıyor | "Tek sıradaki sinyaller gerçek!" hatırlatın |
| Portal 9: Çok muhafız var | Adım adım tahtada birlikte eleyin |
| Türkçe karakter sorunu | Test normalizer var, büyük/küçük + Türkçe fark etmez |

## Canlı Scoreboard Şablonu

Tahtaya veya Google Sheet'e:

```
╔═══════════════╦══╦══╦══╦══╦══╦══╦══╦══╦══╦═══╦════════╗
║ Katılımcı     ║1 ║2 ║3 ║4 ║5 ║6 ║7 ║8 ║9 ║10 ║Deploy? ║
╠═══════════════╬══╬══╬══╬══╬══╬══╬══╬══╬══╬═══╬════════╣
║ Grup Alfa     ║✅║✅║✅║✅║✅║⬜║⬜║⬜║⬜║ ⬜ ║  ❌    ║
║ Grup Beta     ║✅║✅║✅║✅║✅║✅║✅║⬜║⬜║ ⬜ ║  ❌    ║
║ Grup Gamma    ║✅║✅║✅║✅║✅║✅║✅║✅║✅║ ✅ ║  ✅ 🎉 ║
╚═══════════════╩══╩══╩══╩══╩══╩══╩══╩══╩══╩═══╩════════╝
```

> 💡 Katılımcıları 3-4 kişilik gruplara ayırmanızı öneriyoruz.

## YZ İle Kopya Çekme Önlemleri

Bu format, yapay zekaya yapıştırarak çözmeyi zorlaştırır çünkü:

1. **Portal 4** repo içinde klasör labirentini keşfetmeyi + tuzak ayıklamayı gerektirir
2. **Portal 10** diğer 9 cevabı bilmeyi gerektirir (tek seferde çözülemez)
3. Bulmacalar bağlam gerektirir (matrisler, tablolar, dosya yapısı)
4. **Vigenère** ve **filtrelenmiş akrostiş** çok adımlı düşünme gerektirir
5. **Parazit ayıklama** dikkat ve eleme becerisi ister

Ek önlem olarak:
- Zaman sınırı koyun (ilk bitiren gruba ödül)
- Ekranlarda dolaşarak süreci gözlemleyin
- "Nasıl çözdün?" diye sorun, süreci anlatamayan kopya çekmiştir

## Bootcamp Sonrası Kaynaklar

- GitHub Actions Docs: https://docs.github.com/en/actions
- GitHub Skills: https://skills.github.com
- CI/CD Nedir?: https://www.redhat.com/en/topics/devops/what-is-ci-cd
