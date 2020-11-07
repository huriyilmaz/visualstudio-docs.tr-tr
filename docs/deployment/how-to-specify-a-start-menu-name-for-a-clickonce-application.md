---
title: ClickOnce uygulaması için Başlat menüsü adı belirtme
description: Yayımla Seçenekleri iletişim kutusunda ürün adı ' nı ayarlayarak ClickOnce uygulamanız için görünen adı nasıl değiştireceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12a6ebce0ff3bb7c3040765c1a82f876d0055c4d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349678"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulaması için Başlat menüsü adı belirtme
Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama hem çevrimiçi hem de çevrimdışı kullanım için yüklendiğinde, **Başlat** menüsüne ve **Program Ekle/Kaldır** listesine bir giriş eklenir. Varsayılan olarak, görünen ad uygulama derlemesinin adıyla aynıdır, ancak **Yayımlama seçenekleri** Iletişim kutusunda **ürün adı** ' nı ayarlayarak görünen adı değiştirebilirsiniz.

 **Ürün adı** *publish.htm* sayfasında görüntülenir; yüklü bir çevrimdışı uygulama için, **Başlangıç** menüsündeki girdinin adı olacaktır ve ayrıca **Program Ekle veya Kaldır** ' da gösterilen ad olur.

 **Yayımcı adı** , **ürün adının** üzerindeki *publish.htm* sayfasında görünür ve yüklü bir çevrimdışı uygulama için, **Başlangıç** menüsünde uygulamanın simgesini içeren klasörün adı da olacaktır.

 Başlat menüsü kısayolu veya uygulama başvurusu, *%APPDATA%\Microsoft\Windows\Start Menu\Programs \\<yayımcı adı \>* ' nda oluşturulur. Kısayol veya uygulama başvurusu, ürün adı ile aynı ada sahiptir.

 **Ürün adı** ve **Yayımcı adı** özelliklerini, **Proje Tasarımcısı** ' nın **Yayımla** sayfasında bulunan **Yayımla Seçenekleri** iletişim kutusunda ayarlayabilirsiniz.

### <a name="to-specify-a-start-menu-name"></a>Başlangıç menüsü adı belirtmek için

1. **Çözüm Gezgini** ' de bir proje seçiliyken, **Proje** menüsünde **Özellikler** ' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Yayımla Seçenekleri** iletişim kutusunu açmak için **Seçenekler** düğmesine tıklayın.

4. **Açıklama** ' ya tıklayın.

5. **Yayımla Seçenekleri** Iletişim kutusunda **ürün adı** ' nda görüntülenecek adı girin.

6. İsteğe bağlı olarak, **Yayımcı adı** ' na bir yayımcı adı girebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)