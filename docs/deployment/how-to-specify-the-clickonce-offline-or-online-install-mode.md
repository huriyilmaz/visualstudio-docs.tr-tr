---
title: Çevrimdışı veya çevrimiçi yüklemesi modunu belirtin (ClickOnce)
description: uygulamanın çevrimdışı veya çevrimiçi olarak kullanılabilir olup olmadığını belirleyen bir ClickOnce uygulaması için yük modunu belirtmeyi öğrenin.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 68d51ae558c6bc40c632c680a76248b7ac1b4cb1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080526"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>nasıl yapılır: ClickOnce çevrimdışı veya çevrimiçi olarak yüklemeyi belirtme
`Install Mode`Uygulama için, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanın çevrimdışı veya çevrimiçi olarak kullanılabilir olup olmayacağını belirler. **Uygulama yalnızca çevrimiçi kullanılabilir** olduğunda, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamayı çalıştırmak için kullanıcının yayımlama konumuna (bir Web sayfası veya bir dosya paylaşımında) erişimi olması gerekir. **Uygulamanın çevrimdışı kullanılabilir olduğunu** seçtiğinizde, uygulama **Başlangıç** menüsüne ve **Program Ekle veya Kaldır** iletişim kutusuna giriş ekler; Kullanıcılar bağlı olmadıkları zaman uygulamayı çalıştırabilir.

, `Install Mode` **Project tasarımcısının** **yayımla** sayfasında ayarlanabilir.

> [!NOTE]
> , `Install Mode` Yayımlama Sihirbazı kullanılarak da ayarlanabilir. daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulama yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-make-a-clickonce-application-available-online-only"></a>ClickOnce bir uygulamayı yalnızca çevrimiçi kullanılabilir hale getirmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Project** menüsünde **özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. uygulama **ve Ayarlar** alanında, **uygulama yalnızca çevrimiçi kullanılabilir** seçenek düğmesine tıklayın.

### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>ClickOnce bir uygulamayı çevrimiçi veya çevrimdışı kullanılabilir hale getirmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Project** menüsünde **özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **yüklemeyi mod ve Ayarlar** alanında, uygulama ' da **çevrimdışı kullanılabilir** ' ı tıklatın.

     Yüklendiğinde, uygulama **Başlangıç** menüsüne giriş ekler ve Denetim Masası 'Nda **Program Ekle/Kaldır** ' ı görüntüler.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)