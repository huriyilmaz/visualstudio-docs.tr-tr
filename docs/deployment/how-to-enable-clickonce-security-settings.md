---
title: ClickOnce Security Ayarlar | Microsoft Docs
description: Yayımla sihirbazının, uygulama yayımlamak için ClickOnce erişim güvenliğini otomatik olarak nasıl olanaklı olduğunu öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635281"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Nasıl yapabilirsiniz: ClickOnce ayarlarını etkinleştirme
Uygulama yayımlamak ClickOnce için kod erişimi güvenliği etkinleştirilmelidir. Bu, Yayımla sihirbazını kullanarak bir uygulama yayımlasanız otomatik olarak yapılır.

 Bazı durumlarda, kod erişimi güvenliğinin etkinleştirilmesi, uygulamanızı hazırlarken veya hata ayıklarken performansı etkileyebilir; Bu durumlarda, güvenlik ayarlarını geçici olarak devre dışı bırakmak isterseniz.

 ClickOnce ayarları, Project **Tasarımcısı'nın** Güvenlik **sayfasında etkinleştirilebilir veya devre dışı bırakılabilir.**

### <a name="to-enable-clickonce-security-settings"></a>Güvenlik ayarlarını ClickOnce için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **Project'a** **tıklayın.**

2. **Güvenlik** sekmesine tıklayın.

3. ClickOnce **Security Ayarlar** onay kutusunu seçin.

     Artık Güvenlik sayfasında uygulamanıza güvenlik ayarlarını özelleştirebilirsiniz.

    > [!NOTE]
    > Uygulama Yayımla sihirbazıyla her yayım olduğunda bu onay kutusu otomatik **olarak** seçilir.

### <a name="to-disable-clickonce-security-settings"></a>Güvenlik ayarlarını ClickOnce için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **Project'a** **tıklayın.**

2. **Güvenlik** sekmesine tıklayın.

3. ClickOnce **Security Ayarlar kutusunun** işaretini kaldırın.

     Uygulamanız tam güven güvenliği ayarlarıyla çalıştıracak; Güvenlik sayfasındaki **tüm ayarlar** yoksayılır.

    > [!NOTE]
    > Uygulama Yayımla sihirbazıyla her yayımlanıyorsa bu onay kutusu seçilir; her başarılı yayımlamadan sonra tekrar temizlemelisiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)
