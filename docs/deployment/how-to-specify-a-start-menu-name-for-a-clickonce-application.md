---
title: ClickOnce uygulama için Başlat menüsü adı belirtin
description: yayımla seçenekleri iletişim kutusunda ürün adı ' nı ayarlayarak ClickOnce uygulamanızın görünen adını değiştirmeyi öğrenin.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 18e91e0bb0ebcb6a88d6f4c197cce9dfb4a04592
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051592"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>nasıl yapılır: ClickOnce uygulaması için Başlat menüsü adı belirtme
Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama hem çevrimiçi hem de çevrimdışı kullanım için yüklendiğinde, **Başlat** menüsüne ve **Program Ekle/Kaldır** listesine bir giriş eklenir. Varsayılan olarak, görünen ad uygulama derlemesinin adıyla aynıdır, ancak **Yayımlama seçenekleri** Iletişim kutusunda **ürün adı** ' nı ayarlayarak görünen adı değiştirebilirsiniz.

 **Ürün adı** *publish.htm* sayfasında görüntülenir; yüklü bir çevrimdışı uygulama için, **Başlangıç** menüsündeki girdinin adı olacaktır ve ayrıca **Program Ekle veya Kaldır**' da gösterilen ad olur.

 **Publisher adı** , **ürün adının** üzerindeki *publish.htm* sayfasında görünür ve yüklü bir çevrimdışı uygulama için, **başlangıç** menüsünde uygulamanın simgesini içeren klasörün adı da olacaktır.

 Başlat menüsü kısayol veya uygulama başvurusu, *%appdata%\Microsoft\ Windows \start Menu\Programs \\<yayımcı adı \>*'nda oluşturulur. Kısayol veya uygulama başvurusu, ürün adı ile aynı ada sahiptir.

 **ürün adı** ve **Publisher adı** özelliklerini, **Project tasarımcısının** **yayımla** sayfasında bulunan **yayımla seçenekleri** iletişim kutusunda ayarlayabilirsiniz.

### <a name="to-specify-a-start-menu-name"></a>Başlat menüsü adı belirtmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Project** menüsünde **özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Yayımla Seçenekleri** iletişim kutusunu açmak için **Seçenekler** düğmesine tıklayın.

4. **Açıklama**' ya tıklayın.

5. **Yayımla Seçenekleri** Iletişim kutusunda **ürün adı**' nda görüntülenecek adı girin.

6. isteğe bağlı olarak, **Publisher adında** bir yayımcı adı girebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)