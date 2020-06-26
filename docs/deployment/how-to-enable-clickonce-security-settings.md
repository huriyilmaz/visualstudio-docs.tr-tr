---
title: ClickOnce güvenlik ayarlarını etkinleştirme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d673edac957e9625f7d948fbe766ee08b23b6b52
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382438"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme
Uygulamayı yayımlamak için ClickOnce uygulamaları için kod erişimi güvenliği etkinleştirilmelidir. Bu, Yayımlama Sihirbazı 'nı kullanarak bir uygulamayı yayımladığınızda otomatik olarak yapılır.

 Bazı durumlarda, uygulama derlerken veya hata ayıklarken kod erişim güvenliğini etkinleştirmek performansı etkileyebilir; Bu durumlarda, güvenlik ayarlarını geçici olarak devre dışı bırakmak isteyebilirsiniz.

 ClickOnce güvenlik ayarları, **Proje Tasarımcısı**'nın **güvenlik** sayfasında etkinleştirilebilir veya devre dışı bırakılabilir.

### <a name="to-enable-clickonce-security-settings"></a>ClickOnce güvenlik ayarlarını etkinleştirmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Güvenlik** sekmesine tıklayın.

3. **ClickOnce güvenlik ayarlarını etkinleştir** onay kutusunu seçin.

     Artık güvenlik sayfasında uygulamanızın güvenlik ayarlarını özelleştirebilirsiniz.

    > [!NOTE]
    > Bu onay kutusu, uygulamanın **Yayımlama** sihirbazıyla her yayımlanışında otomatik olarak seçilir.

### <a name="to-disable-clickonce-security-settings"></a>ClickOnce güvenlik ayarlarını devre dışı bırakmak için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Güvenlik** sekmesine tıklayın.

3. **ClickOnce güvenlik ayarlarını etkinleştir** onay kutusunu temizleyin.

     Uygulamanız tam güven güvenlik ayarlarıyla çalıştırılır; **güvenlik** sayfasındaki tüm ayarlar yok sayılır.

    > [!NOTE]
    > Uygulama yayımlama sihirbazıyla her yayımlandığında, bu onay kutusu işaretlenir; Her başarılı yayımladıktan sonra yeniden temizlemeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)
