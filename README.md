# MedBot
# MedBot — README, Issue List & İlk Görev Tablosu

**Proje adı:** MedBot — Eğitim amaçlı Klinik Karar Destek Chatbot (Semptom → Olası Tanılar + Tahlil Önerisi)

**Kısa açıklama:** Bu repo, tıp öğrencileri ve acil pratisyen hekimler için tasarlanmış, NLP tabanlı bir sohbet arayüzü üzerinden girilen semptomlara göre olası tanıları sıralayan ve gerektiğinde hangi tahlil/ek bilgi gerektiğini öneren eğitim-odaklı bir prototip içerir. İlk hedefimiz rule-based (kurala dayalı) MVP ve 10 eğitim vakasıyla çalışan bir demo sunmaktır.

---

## İçindekiler / Dosya yapısı (öneri)

```
medbot-project/
├─ README.md
├─ LICENSE
├─ requirements.txt
├─ app/
│  ├─ frontend/        # Streamlit veya React uygulaması
│  └─ backend/         # FastAPI/Flask + model logic
├─ data/
│  ├─ cases/           # 10 eğitim vakası (json/markdown)
│  └─ rules/           # rule-based kurallar (yaml/json)
├─ notebooks/         # Denemeler, NLP prototipleri
└─ docs/              # Proje raporu, etik, kullanım kılavuzu
```

---

## Hızlı Başlangıç (README için kullanılacak metin)

### Gereksinimler

* Python 3.10+ (tercih 3.11)
* Git

### Kurulum (örnek)

```bash
git clone <repo-url>
cd medbot-project
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

### Lokal çalıştırma (Streamlit örneği)

```bash
cd app/frontend
streamlit run app.py
```

### Disclaimer (README içinde mutlaka olsun)

> **UYARI:** Bu yazılım yalnızca eğitim amaçlıdır. Gerçek hasta tanısı veya tedavi kararı için kullanılmamalıdır. Herhangi bir klinik karar, yetkili hekim onayı gerektirir.

---

## Önerilen Teknoloji yığını

* Python, FastAPI veya Flask (backend)
* Streamlit (hızlı demo UI) veya React (daha gelişmiş UI)
* spaCy (symptom extraction), regex (basit kurallar)
* scikit-learn / transformers (opsiyonel ML iyileştirme)

---

## Kısa Proje Planı / Kilometre taşları

* Hafta 0: Repo, ortam, 10 vaka, basit rule-based motor, Streamlit "hello".
* Hafta 1: Rule-based MVP + UI integ.
* Hafta 2: NLP symptom extraction (spaCy)/dataset araştırması.
* Hafta 3: Ensemble (rule + ML) (opsiyonel).
* Hafta 4: Kullanıcı testi, sunum ve rapor.

---

## Issue Listesi (Öncelikli görevler) — İlk 14 gün

1. **Repo oluşturma ve temel README** — *Assignee: Kişi A* — Öncelik: Yüksek — Tahmini süre: 0.5 gün
2. **Geliştirme ortamı dokümantasyonu** — *A* — Öncelik: Yüksek — 0.5 gün
3. **Streamlit 'hello' UI (input form)** — *C* — Öncelik: Yüksek — 1 gün
4. **Rule-based motor (10 kural)** — *B* — Öncelik: Yüksek — 2 gün
5. **10 eğitim vakasının oluşturulması (data/cases)** — *Herkes* — Öncelik: Yüksek — 1 gün
6. **Entegrasyon: UI + motor (backend)** — *B & C* — Öncelik: Yüksek — 2 gün
7. **Kısa demo video (5 dk) + 3 slide** — *C* — Öncelik: Orta — 1 gün
8. **Temel evaluation script (top-3 doğruluk)** — *B* — Öncelik: Orta — 1 gün
9. **Etik & gizlilik metni (README/docs)** — *A* — Öncelik: Yüksek — 1 gün
10. **Kullanıcı test planı (5-10 öğrenci)** — *C* — Öncelik: Orta — 2 gün

---

## İlk Görev Tablosu (Önerilen, tarihler 23 Kasım 2025 başlangıç)

| Görev ID |                         Görev | Sorumlu    |  Başlangıç | Bitiş (hedef) | Durum     |
| -------- | ----------------------------: | ---------- | ---------: | ------------: | --------- |
| 1        |       Repo & README oluşturma | Kişi A     | 23-11-2025 |    24-11-2025 | Açık      |
| 2        | Ortam kurulumu & requirements | Kişi A     | 23-11-2025 |    24-11-2025 | Açık      |
| 3        |           Streamlit UI (form) | Kişi C     | 23-11-2025 |    25-11-2025 | Açık      |
| 4        |   Rule-based motor (10 kural) | Kişi B     | 23-11-2025 |    25-11-2025 | Açık      |
| 5        |                  10 vaka seti | Herkes     | 23-11-2025 |    24-11-2025 | Açık      |
| 6        |        UI-backend entegrasyon | Kişi B & C | 25-11-2025 |    27-11-2025 | Planlandı |

> **Hedef son teslim (MVP demo):** 06-01-2026 — Akademik teslimat/ilk haftanın sonu.

---

# 10 Eğitim Vakası (Kısa, eğitim amaçlı) — her vaka: vaka metni, beklenen top-3 tanı, önerilen tahliller

> **Not:** Aşağıdaki vakalar eğitim amaçlı hazırlanmıştır. Gerçek hasta yönetimi için yetkili hekim görüşü alınmalıdır.

### Vaka 1

**Özet:** 32 yaş, erkek. 2 günlük ateş (38.5°C), boğaz ağrısı, hafif kuru öksürük. Ateş var, yutkunma ağrısı.
**Top-3 tanı:** 1) Viral pharyngitis  2) Streptokokal faringit (strep throat)  3) Influenza
**Önerilen tahliller/işlemler:** Rapid strep test, hızlı influenza/PCR (mevsime göre), CBC (lökositoz değerlendirmesi).

### Vaka 2

**Özet:** 68 yaş, kadın. Ani başlangıçlı göğüs ağrısı (sıkıştırıcı), terleme, nefes darlığı. Risk faktörü: HT.
**Top-3 tanı:** 1) Akut koroner sendrom (MI)  2) Pulmoner emboli  3) Akut aort diseksiyonu / ciddi non-kardiyak (ör. aşırı GERD)
**Önerilen tahliller/işlemler:** 12‑lead EKG, troponin seri, PA göğüs grafisi, D‑dimer (eğer ortamdaki klinik olasılık düşükse), acil kardiyoloji konsultasyonu.

### Vaka 3

**Özet:** 25 yaş, kadın. 1 haftadır alt karın ağrısı, ateş yok, adet döngüsü düzenli, ilişki öyküsü var.
**Top-3 tanı:** 1) Pelvik inflamatuar hastalık (PID)  2) Ektopik gebelik (az olasılıkla fakat rule-out)  3) Üriner sistem enfeksiyonu
**Önerilen tahliller/işlemler:** İdrar tetkiki & kültür, beta-hCG (gebelik taraması), pelvik muayene, gerektiğinde transvajinal USG.

### Vaka 4

**Özet:** 45 yaş, erkek. 3 günlük artan öksürük, balgamlı, ateş 38°C, sigara öyküsü yok.
**Top-3 tanı:** 1) Akut bronşit (muhtemel viral)  2) Pnömoni  3) Akut ekzaserbasyon COPD (eğer öykü varsa)
**Önerilen tahliller/işlemler:** Göğüs grafisi (pnömoni ayırıcı), CBC, pulse-oksimetri, gerektiğinde sputum kültürü.

### Vaka 5

**Özet:** 22 yaş, erkek. Ani başlayan yüksek ateş, baş ağrısı, ense sertliği, ışığa hassasiyet.
**Top-3 tanı:** 1) Meningitis (bakteriyel/viral)  2) Subaraknoid kanama (baş ağrısı tipi farklı)  3) Ciddi viral ensefalit
**Önerilen tahliller/işlemler:** Acil beyin görüntülemesi (Gerektiğinde), lomber ponksiyon (LP) — nörolojik konsültasyon, CBC, kan kültürleri, acil antibiyotik protokolü (klinik yönergeye göre).

### Vaka 6

**Özet:** 55 yaş, kadın. 2 haftadır kilo kaybı, gece terlemeleri, gece öksürükleri. Sigara öyküsü yok.
**Top-3 tanı:** 1) Akciğer tüberkülozu (TB)  2) Akciğer malignitesi  3) Kronik enfeksiyon / non-spesifik bronşit
**Önerilen tahliller/işlemler:** Göğüs grafisi, göğüs BT (şüphe varsa), balgam smear / kültür / GeneXpert (TB araştırması), tam kan sayımı.

### Vaka 7

**Özet:** 28 yaş, kadın. Ateş, ürtiker tarzı döküntü ve yutkunma güçlüğü — alerjik reaksiyon şüphesi.
**Top-3 tanı:** 1) Anafilaksi / anjiyoödem  2) Alerjik reaksiyon (urtiker)  3) Viral döküntü
**Önerilen tahliller/işlemler:** Hayati bulguların takibi (tansiyon, solunum), adrenalin uygulama (şiddete göre), antihistaminik, steroid; ileri tetkik gerekirse alerji testi sonrası planlama.

### Vaka 8

**Özet:** 72 yaş, erkek. Yavaş başlangıçlı unutkanlık ve günlük aktivitelerde zorluk — son 1 yıldır giderek kötüleşme.
**Top-3 tanı:** 1) Alzheimer tip demans  2) Vasküler demans  3) Hipotiroidi / depresyon gibi reversibl nedenler
**Önerilen tahliller/işlemler:** MMSE veya MoCA benzeri bilişsel test, TSH, B12, temel laboratuvarlar, gerektiğinde beyin görüntülemesi (MR).

### Vaka 9

**Özet:** 40 yaş, kadın. Sağ alt kadranda şiddetli üst karın/alt karın ağrısı, bulantı, kusma; lokal hassasiyet.
**Top-3 tanı:** 1) Akut apendisit  2) Over torsiyonu / kistik komplikasyonlar (kadın)  3) Gastroenterit / divertikülit (yaşa göre)
**Önerilen tahliller/işlemler:** Abdominal muayene, CBC, CRP, abdominal USG (özellikle apendisit/ovaryan patoloji için), cerrahi konsültasyon gerekebilir.

### Vaka 10

**Özet:** 60 yaş, erkek. Ani başlayan solunum güçlüğü, hemoptizi, geçmişte immobilizasyon öyküsü yok.
**Top-3 tanı:** 1) Pulmoner emboli  2) Akut pankreotit veya ağır enfeksiyon ile ilişkili ARDS (daha az olası)  3) Pnömoni major diferansiyel
**Önerilen tahliller/işlemler:** Pulse oksimetri, ABG (gerekirse), D‑dimer, göğüs BT-anjiyo (PE şüphesinde), EKG, troponin (eşlik eden kardiyak hasar için), acil hekimlik/kanülasyon.

---

## Nasıl kullanılır (özet)

1. `data/cases/` içine vakaları json veya markdown olarak kaydedin (örnek format: id, yaş, cinsiyet, özet, beklenen_top3, önerilen_tahliller).
2. `app/backend/rules/` içine kural setlerini (basit if-then) koyun.
3. Streamlit UI ile kullanıcıdan alınan input `backend`'e gönderilsin; backend symptom extraction → rule-matching → top list döndürsün.

---

## Son notlar / Etik uyarı

* Projeye başlamadan önce bu README'deki disclaimer bölümünü kısaltıp repo ana sayfasına koyun.
* Gerçek hasta verisi kullanımı planlanıyorsa, kurumunuzun etik kurulundan onay ve data-use agreement alın.

---

*Hazır — Repo başlangıcı ve 10 vaka seti bu dokümanda yer alıyor. İsterseniz şimdi README dosyasını repo formatına çevirebilir veya doğrudan `app/frontend/streamlit` için minimal çalışır kod (copy-paste) hazırlayayım.*
