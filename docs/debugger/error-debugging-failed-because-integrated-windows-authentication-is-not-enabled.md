---
description: Hata ayıklamayı isteyen kullanıcının kimlik doğrulaması bir kimlik doğrulama hatası nedeniyle engellendi.
title: tümleşik Windows kimlik doğrulaması etkinleştirilmediğinden hata ayıklama başarısız oldu | Microsoft Docs
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
ms.openlocfilehash: ac1922c66702ba5b0e5e3d10d7057c31239dffd492243f6d2dda37eddaaa33c6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379418"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Hata: Tümleşik Windows Kimlik Doğrulaması Etkinleştirilmediğinden Hata Ayıklama Başarısız
Hata ayıklamayı isteyen kullanıcının kimlik doğrulaması bir kimlik doğrulama hatası nedeniyle engellendi. Bu durum, bir Web uygulamasına veya bir XML Web hizmetine adım adım çalışırken oluşabilir. bu hatanın bir nedeni tümleşik Windows kimlik doğrulamasının etkinleştirilmemesine neden olur. etkinleştirmek için, "tümleşik Windows kimlik doğrulamasını etkinleştirmek için" bölümündeki adımları izleyin.

 tümleşik Windows kimlik doğrulamasını etkinleştirdiyseniz, bu hata yine de görünüyorsa, **Windows etki alanı sunucuları için özet kimlik doğrulamasının** etkinleştirildiğinden bu hata meydana gelir. Bu durumda, ağ yöneticinizle iletişim kurmanız gerekir.

### <a name="to-enable-integrated-windows-authentication"></a>tümleşik Windows kimlik doğrulamasını etkinleştirmek için

1. Bir yönetici hesabı kullanarak Web sunucusunda oturum açın.

2. **Başlat** ' a ve ardından **Denetim Masası**' na tıklayın.

3. **Denetim Masası**'Nda **Yönetimsel Araçlar**' a çift tıklayın.

4. **Internet Information Services** çift tıklayın.

5. Web sunucusu düğümüne tıklayın.

     Sunucu adının altında bir **Web siteleri** klasörü açılır.

6. Tüm Web siteleri veya ayrı Web siteleri için kimlik doğrulaması yapılandırabilirsiniz. Tüm Web sitelerinin kimlik doğrulamasını yapılandırmak için, **Web siteleri** klasörüne sağ tıklayın ve ardından **Özellikler**' e tıklayın. Tek bir Web sitesinin kimlik doğrulamasını yapılandırmak için, **Web siteleri** klasörünü açın, bireysel Web sitesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

     **Özellikler** iletişim kutusu görüntülenir.

7. **Dizin Güvenliği** sekmesine tıklayın.

8. **Anonim erişim ve kimlik doğrulama denetimi** bölümünde **Düzenle**' ye tıklayın.

     **Kimlik doğrulama yöntemleri** iletişim kutusu görüntülenir.

9. **kimliği doğrulanmış erişim** altında **tümleşik Windows kimlik doğrulaması**' nı seçin.

10. **Kimlik doğrulama yöntemleri** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

11. **Özellikler** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

12. **Internet Information Services** penceresini kapatın.

### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Windows Vista/ııs 7 ' de tümleşik Windows kimlik doğrulamasını etkinleştirmek için

1. Bir yönetici hesabı kullanarak Web sunucusunda oturum açın.

2. bu işlemi daha önce yapmadıysanız aşağıdaki adımları izleyerek Windows kimlik doğrulaması ve II6 yönetim uyumluluğunu açın:

    1. **Başlat**' a, **Denetim Masası** ' na ve ardından **Programlar**' a tıklayın.

    2. **programlar ve özellikler** altında **Windows özellikleri aç veya kapat**' a tıklayın.

         Kullanıcı Access Control iletişim kutusu görünür ve devam etmek için sizden izin ister.

    3. **Devam**’a tıklayın.

         Windows özellikleri iletişim kutusu görüntülenir.

    4. özellik listesinde **Internet Information Services** düğümünü genişletin.

    5. **Internet Information Services** altında **World Wide Web hizmetleri** düğümünü genişletin.

    6. **World Wide Web Hizmetler** altında **güvenlik**' e tıklayın.

    7. **Windows kimlik doğrulaması**' na tıklayın.

    8. **Internet Information Services** altında **Web yönetim araçları** düğümünü genişletin.

    9. **Web yönetimi araçları**' nın altında, **IIS 6 Yönetim uyumluluğu** düğümünü genişletin ve **IIS 6 metatabanı ve IIS 6 yapılandırma uyumluluğu** onay kutusunu seçin.

    10. **Web yönetimi araçları** altında **IIS Yönetim Konsolu** ' nu seçin ve **Tamam** ' ı tıklatın.

    11. Bu değişikliklerin etkili olması için bilgisayarı yeniden başlatın.

3. **Başlat** ' a ve ardından **Denetim Masası**' na tıklayın.

4. **Klasik Görünüm**' e tıklayın ve ardından **Yönetimsel Araçlar**' a çift tıklayın.

5. **ad** sütununda **Internet Information Services (ııs) yöneticisi**' ne çift tıklayın.

6. **Bağlantılar** sütununda sunucunuzun düğümünü genişletin.

     Sunucu adının altında bir **Web siteleri** klasörü açılır.

7. **web siteleri** düğümünü genişletin ve tümleşik Windows kimlik doğrulamasını etkinleştirmek istediğiniz web sitesine tıklayın.

8. Orta bölmenin başlığı, seçtiğiniz web sitesinin adı olarak değişir. Bu bölmede, **IIS** başlığı altında **kimlik doğrulama**' ya çift tıklayın.

     Bölmenin başlığı, **kimlik doğrulamasında** değişir.

9. **kimlik doğrulama** bölmesindeki **ad** sütununda **kimlik doğrulama Windows** ' ye sağ tıklayın ve ardından **etkinleştir**' e tıklayın.

10. **Internet Information Services (ııs) yöneticisi** penceresini kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Microsoft Digest kimlik doğrulaması](/windows/win32/secauthn/microsoft-digest-authentication)
- [ııs 7,0 ve Visual Studio ile Windows Vista 'da Web uygulamaları çalıştırma](/previous-versions/aa964620(v=vs.140))
