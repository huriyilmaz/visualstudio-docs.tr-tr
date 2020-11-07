---
title: Özel izinleri ayarlama (ClickOnce uygulaması)
description: Varsayılan izinleri kullanan bir ClickOnce uygulamasını dağıtmayı veya uygulamanın ihtiyaç duyacağı belirli izinler için özel bir bölge oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5d0348b882a3327c02fca6db0628822c0deffeb
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351004"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Internet veya yerel Intranet bölgeleri için varsayılan izinleri kullanan bir uygulamayı dağıtabilirsiniz. Alternatif olarak, uygulamanın ihtiyacı olan özel izinler için özel bir bölge oluşturabilirsiniz. Bunu, **Proje Tasarımcısı** 'nın **güvenlik** sayfasında güvenlik izinlerini özelleştirerek yapabilirsiniz.

### <a name="to-customize-a-permission"></a>Bir izni özelleştirmek için

1. **Çözüm Gezgini** ' de bir proje seçiliyken, **Proje** menüsünde **Özellikler** ' e tıklayın.

2. **Güvenlik** sekmesine tıklayın.

3. **ClickOnce güvenlik ayarlarını etkinleştir** onay kutusunu seçin.

4. **Bu bir kısmi güven uygulaması** seçenek düğmesini seçin.

     **ClickOnce güvenlik izinleri** bölümündeki denetimler etkindir.

5. Uygulamanızın açılan listeden **yüklenecek bölge** listesinden **(özel)** seçeneğine tıklayın.

6. **Izinleri Düzenle XML** ' ye tıklayın.

     *App. manifest* dosyası XML düzenleyicisinde açılır.

7. Öğesinden önce `</applicationRequestMinimum>` , uygulamanız için gereken izinler IÇIN XML kodu ekleyin.

    > [!NOTE]
    > `ToXml`Uygulama bildirimi IÇIN XML kodu oluşturmak üzere bir izin kümesi yöntemini kullanabilirsiniz. Örneğin, izin kümesi için XML oluşturmak üzere <xref:System.Security.Permissions.EnvironmentPermission> <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli ClickOnce uygulamaları](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)
