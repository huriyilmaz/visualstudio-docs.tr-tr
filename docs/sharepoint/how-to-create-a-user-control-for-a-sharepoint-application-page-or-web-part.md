---
title: SharePoint uygulama sayfası veya web bölümü için kullanıcı denetimi oluşturma
titleSuffix: ''
description: SharePoint çözümünüz için özel işlevsellik sağlayan özel kullanıcı denetimleri oluşturun ve bu işlevselliği bir web bölümü veya uygulama sayfası içinde yeniden kullanın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 9a622fa1d85ed916a393d7ea4cac56a335d550f3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115596"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>nasıl yapılır: SharePoint uygulama sayfası veya web bölümü için kullanıcı denetimi oluşturma
  SharePoint çözümünüz için özel işlevler sağlayan özel kullanıcı denetimleri oluşturabilir ve bu işlevselliği projenizde yeniden kullanabilirsiniz. kullanıcı denetimlerini bir web bölümü veya uygulama sayfasına dahil edebilir, diğer ASP.NET denetimleri ve SharePoint denetimleri ekleyebilir ve denetimin özelliklerini ve yöntemlerini tanımlayabilirsiniz. Kullanıcı denetimleri hakkında daha fazla bilgi için bkz. SharePoint [Web bölümleri veya uygulama sayfaları](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) ve [Kullanıcı denetimleri ve sunucu denetimleri](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/)Için yeniden kullanılabilir denetimler oluşturma.

### <a name="to-create-a-user-control-for-sharepoint"></a>SharePoint için Kullanıcı denetimi oluşturmak için

1. Visual Studio, bir SharePoint projesi açın veya oluşturun.

     bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. **Çözüm Gezgini**, proje düğümünü seçin.

3. menü çubuğunda **Project**  >  **yeni öğe ekle**' yi seçin.

     **Yeni öğe Ekle** iletişim kutusu açılır.

4. **yüklü** bölmede **Office/SharePoint** düğümünü seçin.

5. SharePoint şablonları listesinde, kullanıcı denetimi ' ni **(yalnızca grup çözümü)** seçin.

    > [!NOTE]
    > Kullanıcı denetimleri yalnızca Grup çözümlerinde çalışır.

6. **Ad** kutusunda, Kullanıcı denetimi için bir ad belirtin ve ardından **Ekle** düğmesini seçin.

     Visual Studio projenize birkaç klasör ve dosya ekler. Bu dosyalar hakkında daha fazla bilgi için bkz. [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

     Varsayılan olarak, Kullanıcı denetimi dosyası, Visual Web Developer Designer 'ın **kaynak** görünümünde görüntülenir. Bu görünümde, denetimin XML işaretlemesini düzenleyebilirsiniz. Denetimleri **araç kutusundan** sürükleyerek görsel olarak tasarlamak istiyorsanız **Tasarım** görünümüne geçebilirsiniz. Bkz. [Tasarım görünümü, Web sayfası tasarımcısı](/previous-versions/aspnet/ms178149\(v\=vs.100\)).

7. Denetimde oluşan olayları işlemek istiyorsanız, Kullanıcı denetiminin kod dosyasına kod ekleyin.

     Bu dosya, Kullanıcı denetimi dosyası altında **Çözüm Gezgini** görüntülenir ve projenin diline bağlı olarak *. cs* veya *. vb* uzantısına sahiptir.

## <a name="see-also"></a>Ayrıca bkz.
- [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)
- [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
