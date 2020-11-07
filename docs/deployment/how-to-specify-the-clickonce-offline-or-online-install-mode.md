---
title: Çevrimdışı veya çevrimiçi yüklemesi modunu belirtme (ClickOnce)
description: Uygulamanın çevrimdışı veya çevrimiçi olarak kullanılabilir olup olmadığını belirleyen bir ClickOnce uygulaması için yük modunu belirtmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5236d73bb965d4f25634ad9e61a52608c9030146
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350939"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Nasıl yapılır: ClickOnce Çevrimdışı veya çevrimiçi yüklemesi modunu belirtme
`Install Mode`Uygulama için, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanın çevrimdışı veya çevrimiçi olarak kullanılabilir olup olmayacağını belirler. **Uygulama yalnızca çevrimiçi kullanılabilir** olduğunda, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamayı çalıştırmak için kullanıcının yayımlama konumuna (bir Web sayfası veya bir dosya paylaşımında) erişimi olması gerekir. **Uygulamanın çevrimdışı kullanılabilir olduğunu** seçtiğinizde, uygulama **Başlangıç** menüsüne ve **Program Ekle veya Kaldır** iletişim kutusuna giriş ekler; Kullanıcılar bağlı olmadıkları zaman uygulamayı çalıştırabilir.

, `Install Mode` **Proje Tasarımcısı** ' nın **Yayımla** sayfasında ayarlanabilir.

> [!NOTE]
> , `Install Mode` Yayımlama Sihirbazı kullanılarak da ayarlanabilir. Daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-make-a-clickonce-application-available-online-only"></a>ClickOnce uygulamasını yalnızca çevrimiçi kullanılabilir hale getirmek için

1. **Çözüm Gezgini** ' de bir proje seçiliyken, **Proje** menüsünde **Özellikler** ' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Install Mode and Settings** alanında, **uygulama yalnızca çevrimiçi kullanılabilir** seçenek düğmesine tıklayın.

### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>ClickOnce uygulamasını çevrimiçi veya çevrimdışı kullanılabilir hale getirmek için

1. **Çözüm Gezgini** ' de bir proje seçiliyken, **Proje** menüsünde **Özellikler** ' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Yüklenecek mod ve ayarlar** alanında, uygulama ' da **çevrimdışı kullanılabilir** ' ı tıklatın.

     Yüklendiğinde, uygulama **Başlangıç** menüsüne giriş ekler ve Denetim Masası 'Nda **Program Ekle/Kaldır** ' ı görüntüler.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)