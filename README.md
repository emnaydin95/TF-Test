# astrony-testflight-check

Minimal **tek butonlu** Flutter uygulaması. Tek amacı: TestFlight pipeline'ının
uçtan uca çalışıp çalışmadığını doğrulamak. AdMob, IAP, asset vb. **hiçbir şey yok**.

- Bundle id: `com.astrony.test`
- Görünen ad: `TF Test`
- İçerik: ekranda bir sayaç + "Tıkla" butonu

## Codemagic ile build alma

1. GitHub'da bu repoyu Codemagic'e bağla.
2. Codemagic'te App Store Connect API key entegrasyonu oluştur, adını
   `codemagic.yaml` içindeki `ASC_KEY` yerine yaz.
3. Apple tarafında ön koşullar:
   - Developer hesabında `com.astrony.test` App ID'sini kaydet.
   - App Store Connect'te bu bundle id ile yeni bir uygulama kaydı oluştur.
4. `ios-testflight` workflow'unu çalıştır. Build bitince otomatik TestFlight'a yüklenir.

## Beklenen sonuç

- Bu uygulama TestFlight'tan **kuruluyorsa** → pipeline/hesap sağlam, sorun
  asıl Tabu uygulamasının kodunda/asset'lerinde/bağımlılıklarında.
- Bu uygulama da **kurulmuyorsa** → sorun App Store Connect / hesap / TestFlight
  yapılandırmasında; kodla ilgisi yok.
