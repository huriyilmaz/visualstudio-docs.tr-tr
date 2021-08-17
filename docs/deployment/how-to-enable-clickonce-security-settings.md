---
title: ClickOnce güvenliği Ayarlar etkinleştir | Microsoft Docs
description: yayımla sihirbazının uygulamayı yayımlaması ClickOnce uygulamalar için kod erişim güvenliğini otomatik olarak nasıl etkinleştirmesine öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: b534d18deeb63cad6cb0df967915e4fde968c688
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080630"
---
# <a name="how-to-enable-clickonce-security-settings"></a>nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme
uygulamayı yayımlamak için ClickOnce uygulamalar için kod erişimi güvenliği etkinleştirilmelidir. Bu, Yayımlama Sihirbazı 'nı kullanarak bir uygulamayı yayımladığınızda otomatik olarak yapılır.

 Bazı durumlarda, uygulama derlerken veya hata ayıklarken kod erişim güvenliğini etkinleştirmek performansı etkileyebilir; Bu durumlarda, güvenlik ayarlarını geçici olarak devre dışı bırakmak isteyebilirsiniz.

 ClickOnce güvenlik ayarları **Project tasarımcısının** **güvenlik** sayfasında etkinleştirilebilir veya devre dışı bırakılabilir.

### <a name="to-enable-clickonce-security-settings"></a>ClickOnce güvenlik ayarlarını etkinleştirmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Project** menüsünde **özellikler**' e tıklayın.

2. **Güvenlik** sekmesine tıklayın.

3. **ClickOnce güvenliği etkinleştir Ayarlar** onay kutusunu seçin.

     Artık güvenlik sayfasında uygulamanızın güvenlik ayarlarını özelleştirebilirsiniz.

    > [!NOTE]
    > Bu onay kutusu, uygulamanın **Yayımlama** sihirbazıyla her yayımlanışında otomatik olarak seçilir.

### <a name="to-disable-clickonce-security-settings"></a>ClickOnce güvenlik ayarlarını devre dışı bırakmak için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Project** menüsünde **özellikler**' e tıklayın.

2. **Güvenlik** sekmesine tıklayın.

3. **ClickOnce güvenlik Ayarlar etkinleştir** onay kutusunu temizleyin.

     Uygulamanız tam güven güvenlik ayarlarıyla çalıştırılır; **güvenlik** sayfasındaki tüm ayarlar yok sayılır.

    > [!NOTE]
    > Uygulama yayımlama sihirbazıyla her yayımlandığında, bu onay kutusu işaretlenir; Her başarılı yayımladıktan sonra yeniden temizlemeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)
