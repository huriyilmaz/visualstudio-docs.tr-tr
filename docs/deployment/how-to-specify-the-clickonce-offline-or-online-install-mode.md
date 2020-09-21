---
title: Çevrimdışı veya çevrimiçi yüklemesi modunu belirtme (ClickOnce)
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
ms.openlocfilehash: 896d2218237b884d9483496e0adac157a6e26fd3
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808743"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Nasıl yapılır: ClickOnce Çevrimdışı veya çevrimiçi yüklemesi modunu belirtme
`Install Mode`Uygulama için, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanın çevrimdışı veya çevrimiçi olarak kullanılabilir olup olmayacağını belirler. **Uygulama yalnızca çevrimiçi kullanılabilir**olduğunda, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamayı çalıştırmak için kullanıcının yayımlama konumuna (bir Web sayfası veya bir dosya paylaşımında) erişimi olması gerekir. **Uygulamanın çevrimdışı kullanılabilir olduğunu**seçtiğinizde, uygulama **Başlangıç** menüsüne ve **Program Ekle veya Kaldır** iletişim kutusuna giriş ekler; Kullanıcılar bağlı olmadıkları zaman uygulamayı çalıştırabilir.

, `Install Mode` **Proje Tasarımcısı**' nın **Yayımla** sayfasında ayarlanabilir.

> [!NOTE]
> , `Install Mode` Yayımlama Sihirbazı kullanılarak da ayarlanabilir. Daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-make-a-clickonce-application-available-online-only"></a>ClickOnce uygulamasını yalnızca çevrimiçi kullanılabilir hale getirmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Install Mode and Settings** alanında, **uygulama yalnızca çevrimiçi kullanılabilir** seçenek düğmesine tıklayın.

### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>ClickOnce uygulamasını çevrimiçi veya çevrimdışı kullanılabilir hale getirmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Yüklenecek mod ve ayarlar** alanında, uygulama ' da **çevrimdışı kullanılabilir** ' ı tıklatın.

     Yüklendiğinde, uygulama **Başlangıç** menüsüne giriş ekler ve Denetim Masası 'Nda **Program Ekle/Kaldır** ' ı görüntüler.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)