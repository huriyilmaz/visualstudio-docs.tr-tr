---
title: ClickOnce uygulaması için özel Izinleri ayarlama | Microsoft Docs
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
ms.openlocfilehash: 17cd398468bd1640e50f6a58004905cfdf6c2ff0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382152"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Internet veya yerel Intranet bölgeleri için varsayılan izinleri kullanan bir uygulamayı dağıtabilirsiniz. Alternatif olarak, uygulamanın ihtiyacı olan özel izinler için özel bir bölge oluşturabilirsiniz. Bunu, **Proje Tasarımcısı**'nın **güvenlik** sayfasında güvenlik izinlerini özelleştirerek yapabilirsiniz.

### <a name="to-customize-a-permission"></a>Bir izni özelleştirmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Güvenlik** sekmesine tıklayın.

3. **ClickOnce güvenlik ayarlarını etkinleştir** onay kutusunu seçin.

4. **Bu bir kısmi güven uygulaması** seçenek düğmesini seçin.

     **ClickOnce güvenlik izinleri** bölümündeki denetimler etkindir.

5. Uygulamanızın açılan listeden **yüklenecek bölge** listesinden **(özel)** seçeneğine tıklayın.

6. **Izinleri Düzenle XML**' ye tıklayın.

     *App. manifest* dosyası XML düzenleyicisinde açılır.

7. Öğesinden önce `</applicationRequestMinimum>` , uygulamanız için gereken izinler IÇIN XML kodu ekleyin.

    > [!NOTE]
    > `ToXml`Uygulama bildirimi IÇIN XML kodu oluşturmak üzere bir izin kümesi yöntemini kullanabilirsiniz. Örneğin, izin kümesi için XML oluşturmak üzere <xref:System.Security.Permissions.EnvironmentPermission> <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli ClickOnce uygulamaları](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)
