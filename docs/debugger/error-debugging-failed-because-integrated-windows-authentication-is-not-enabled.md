---
title: 'Hata: tümleşik Windows kimlik doğrulaması etkinleştirilmediğinden hata ayıklama başarısız oldu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c508951a3b54a7f84f142c5029b5305c8ef579ea
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911543"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Hata: Tümleşik Windows Kimlik Doğrulaması Etkinleştirilmediğinden Hata Ayıklama Başarısız
Hata ayıklamayı isteyen kullanıcının kimlik doğrulaması bir kimlik doğrulama hatası nedeniyle engellendi. Bu durum, bir Web uygulamasına veya bir XML Web hizmetine adım adım çalışırken oluşabilir. Bu hatanın bir nedeni tümleşik Windows kimlik doğrulamasının etkinleştirilmemesine neden olur. Etkinleştirmek için "tümleşik Windows kimlik doğrulamasını etkinleştirmek Için" bölümündeki adımları izleyin.

 Tümleşik Windows kimlik doğrulamasını etkinleştirdiyseniz, bu hata yine de görünüyorsa, **Windows etki alanı sunucuları Için Özet kimlik doğrulamasının** etkin olması nedeniyle bu hataya neden olmuş olabilir. Bu durumda, ağ yöneticinizle iletişim kurmanız gerekir.

### <a name="to-enable-integrated-windows-authentication"></a>Tümleşik Windows kimlik doğrulamasını etkinleştirmek için

1. Bir yönetici hesabı kullanarak Web sunucusunda oturum açın.

2. **Başlat** ' a ve ardından **Denetim Masası**' na tıklayın.

3. **Denetim Masası**'Nda **Yönetimsel Araçlar**' a çift tıklayın.

4. **Internet Information Services**çift tıklayın.

5. Web sunucusu düğümüne tıklayın.

     Sunucu adının altında bir **Web siteleri** klasörü açılır.

6. Tüm Web siteleri veya ayrı Web siteleri için kimlik doğrulaması yapılandırabilirsiniz. Tüm Web sitelerinin kimlik doğrulamasını yapılandırmak için, **Web siteleri** klasörüne sağ tıklayın ve ardından **Özellikler**' e tıklayın. Tek bir Web sitesinin kimlik doğrulamasını yapılandırmak için, **Web siteleri** klasörünü açın, bireysel Web sitesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

     **Özellikler** iletişim kutusu görüntülenir.

7. **Dizin Güvenliği** sekmesine tıklayın.

8. **Anonim erişim ve kimlik doğrulama denetimi** bölümünde **Düzenle**' ye tıklayın.

     **Kimlik doğrulama yöntemleri** iletişim kutusu görüntülenir.

9. **Kimliği doğrulanmış erişim**altında, **Tümleşik Windows kimlik doğrulaması**' nı seçin.

10. **Kimlik doğrulama yöntemleri** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

11. **Özellikler** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

12. **Internet Information Services** penceresini kapatın.

### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Windows Vista/IIS 7 ' de tümleşik Windows kimlik doğrulamasını etkinleştirmek için

1. Bir yönetici hesabı kullanarak Web sunucusunda oturum açın.

2. Bu işlemi daha önce yapmadıysanız aşağıdaki adımları izleyerek Windows kimlik doğrulaması ve II6 yönetim uyumluluğunu açın:

    1. **Başlat**' a, **Denetim Masası** ' na ve ardından **Programlar**' a tıklayın.

    2. **Programlar ve Özellikler**altında, **Windows özelliklerini aç veya kapat**' a tıklayın.

         Kullanıcı Access Control iletişim kutusu görünür ve devam etmek için sizden izin ister.

    3. **Devam**'a tıklayın.

         Windows özellikleri iletişim kutusu görüntülenir.

    4. Özellik listesinde **Internet Information Services** düğümünü genişletin.

    5. **Internet Information Services**altında **World Wide Web Hizmetleri** düğümünü genişletin.

    6. **World Wide Web Hizmetler**altında **güvenlik**' e tıklayın.

    7. **Windows kimlik doğrulaması**' na tıklayın.

    8. **Internet Information Services**altında **Web yönetim araçları** düğümünü genişletin.

    9. **Web yönetimi araçları**' nın altında, **IIS 6 Yönetim uyumluluğu** düğümünü genişletin ve **IIS 6 metatabanı ve IIS 6 yapılandırma uyumluluğu** onay kutusunu seçin.

    10. **Web yönetimi araçları**altında **IIS Yönetim Konsolu** ' nu seçin ve **Tamam** ' ı tıklatın.

    11. Bu değişikliklerin etkili olması için bilgisayarı yeniden başlatın.

3. **Başlat** ' a ve ardından **Denetim Masası**' na tıklayın.

4. **Klasik Görünüm**' e tıklayın ve ardından **Yönetimsel Araçlar**' a çift tıklayın.

5. **Ad** sütununda **Internet Information Services (IIS) Yöneticisi**' ne çift tıklayın.

6. **Bağlantılar** sütununda sunucunuzun düğümünü genişletin.

     Sunucu adının altında bir **Web siteleri** klasörü açılır.

7. **Web siteleri** düğümünü genişletin ve tümleşik Windows kimlik doğrulamasını etkinleştirmek istediğiniz Web sitesine tıklayın.

8. Orta bölmenin başlığı, seçtiğiniz web sitesinin adı olarak değişir. Bu bölmede, **IIS** başlığı altında **kimlik doğrulama**' ya çift tıklayın.

     Bölmenin başlığı, **kimlik doğrulamasında**değişir.

9. **Kimlik doğrulama** bölmesindeki **ad** sütununda, **Windows kimlik doğrulaması** ' na sağ tıklayın ve ardından **Etkinleştir**' e tıklayın.

10. **Internet Information Services (IIS) Yöneticisi** penceresini kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Microsoft Digest kimlik doğrulaması](/windows/win32/secauthn/microsoft-digest-authentication)
- [IIS 7,0 ve Visual Studio ile Windows Vista 'da Web uygulamaları çalıştırma](https://msdn.microsoft.com/Library/262a82ac-dd0e-4096-86c6-fb463e88be66)