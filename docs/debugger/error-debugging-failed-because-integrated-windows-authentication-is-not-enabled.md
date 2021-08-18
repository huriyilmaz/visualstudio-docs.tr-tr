---
description: Hata ayıklamayı isteyen kullanıcının kimlik doğrulaması bir kimlik doğrulama hatası tarafından engellandı.
title: Tümleşik kimlik doğrulaması etkin Windows hata ayıklama başarısız | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 43fbfc43c44b9be73d9daf4130071c5d018ef039
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097265"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Hata: Tümleşik Windows Kimlik Doğrulaması Etkinleştirilmediğinden Hata Ayıklama Başarısız
Hata ayıklamayı isteyen kullanıcının kimlik doğrulaması bir kimlik doğrulama hatası tarafından engellandı. Bu durum, bir Web uygulamasına veya XML Web hizmetine adım atmaya çalışmanız sırasında ortaya çıkabilir. Bu hatanın nedenlerinden biri, tümleşik kimlik Windows etkinleştirilmemiş durumdadır. Etkinleştirmek için "Tümleşik kimlik doğrulamasını etkinleştirmek için" Windows izleyin.

 Tümleşik kimlik doğrulamasını Windows ve bu hata hala görünüyorsa, Etki Alanı Sunucuları için Özet Kimlik Doğrulaması etkinleştirildiğinden **Windows** bu hataya neden olabilir. Bu durumda ağ yöneticinizle iletişime geçebilirsiniz.

### <a name="to-enable-integrated-windows-authentication"></a>Tümleşik kimlik doğrulamasını Windows için

1. Yönetici hesabı kullanarak Web sunucusunda oturum açın.

2. **Başlat'a** ve ardından **Denetim Masası.**

3. 'Denetim Masası Yönetimsel Araçlar'a **çift tıklayın.** 

4. 'a çift **Internet Information Services.**

5. Web sunucusu düğümüne tıklayın.

     Sunucu **adının altında** bir Web Siteleri klasörü açılır.

6. Tüm Web siteleri veya tek tek Web siteleri için kimlik doğrulamasını yapılandırabilirsiniz. Tüm Web siteleri için kimlik doğrulamasını yapılandırmak için Web Siteleri **klasörüne** sağ tıklayın ve ardından Özellikler'e **tıklayın.** Tek bir Web sitesi için kimlik doğrulamasını yapılandırmak için **Web Siteleri** klasörünü açın, tek bir Web sitesine sağ tıklayın ve ardından Özellikler'e **tıklayın.**

     Özellikler  iletişim kutusu görüntülenir.

7. Dizin Güvenliği **sekmesine** tıklayın.

8. Anonim erişim **ve kimlik doğrulama denetimi bölümünde** Düzenle'ye **tıklayın.**

     Kimlik **Doğrulama Yöntemleri** iletişim kutusu görüntülenir.

9. Kimliği **doğrulanmış erişim altında Tümleşik** kimlik **doğrulaması'Windows seçin.**

10. Kimlik **Doğrulama** Yöntemleri iletişim **kutusunu kapatmak için Tamam'a** tıklayın.

11. Özellikler **iletişim** kutusunu kapatmak için **Tamam'a** tıklayın.

12. Yeni **Internet Information Services** kapatın.

### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Windows Vista/IIS 7 Windows tümleşik Windows kimlik doğrulamasını etkinleştirmek için

1. Yönetici hesabı kullanarak Web sunucusunda oturum açın.

2. Daha önce Windows kimlik doğrulaması ve II6 Yönetim Uyumluluğu'nda şu adımları izleyin:

    1. **Başlat'a** tıklayın, **Denetim Masası'a** ve ardından Programlar'a **tıklayın.**

    2. Programlar **ve Özellikler altında,** Özellikleri **Windows veya kapat'a tıklayın.**

         Kullanıcı Access Control iletişim kutusu açılır ve devam etmek için sizden izin istenir.

    3. **Devam**’a tıklayın.

         Windows Özellikler iletişim kutusu görüntülenir.

    4. Özellik listesinde, Internet Information Services **genişletin.**

    5. Internet Information Services altında, World Wide Web **Services düğümünü** genişletin.

    6. Hizmet **World Wide Web altında Güvenlik'e** **tıklayın.**

    7. Kimlik Doğrulaması **Windows'ye tıklayın.**

    8. Web **Internet Information Services** altında Web Yönetim **Araçları düğümünü** genişletin.

    9. **Web Yönetim Araçları altında** IIS **6 Yönetim** Uyumluluğu düğümünü genişletin ve IIS 6 Metatabanı ve IIS **6 Yapılandırma Uyumluluğu onay** kutusunu seçin.

    10. **Web Yönetim Araçları altında** IIS Yönetim **Konsolu'nu seçin ve Tamam'a** **tıklayın.**

    11. Bu değişikliklerin etkili olması için bilgisayarı yeniden başlatın.

3. **Başlat'a** ve ardından **Denetim Masası.**

4. Klasik **Görünüm'e** tıklayın ve ardından Yönetimsel **Araçlar'a çift tıklayın.**

5. Ad sütununda **Internet Information Services** **(IIS) Yöneticisi'ne çift tıklayın.**

6. Bağlantılar **sütununda,** sunucunuz için düğümü genişletin.

     Sunucu **adının altında** bir Web Siteleri klasörü açılır.

7. Web Siteleri **düğümünü** genişletin ve tümleşik kimlik doğrulamasını etkinleştirmek istediğiniz Web sitesine Windows tıklayın.

8. Orta bölmenin başlığı, seçtiğiniz Web sitesi adıyla değişir. Bu bölmede, **IIS** başlığı altında Kimlik Doğrulaması'nı çift **tıklatın.**

     Bölmenin başlığı Kimlik Doğrulaması olarak **değişir.**

9. Kimlik Doğrulaması **bölmesinde,** Ad **sütununda,** Kimlik Doğrulaması'na sağ tıklayın **Windows'a ve** ardından Etkinleştir'e **tıklayın.**

10. Internet Information Services **(IIS) Yöneticisi penceresini** kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Microsoft Digest Kimlik Doğrulaması](/windows/win32/secauthn/microsoft-digest-authentication)
- [IIS 7.0 ve Windows vista üzerinde Web Uygulamaları Visual Studio](/previous-versions/aa964620(v=vs.140))
