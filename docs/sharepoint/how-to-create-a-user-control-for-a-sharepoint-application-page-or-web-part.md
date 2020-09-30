---
title: SharePoint uygulama sayfası veya Web bölümü için Kullanıcı denetimi oluşturma
titleSuffix: ''
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b9c8a99562d937d7b10c3539888c2dd62eb1d1da
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584106"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Nasıl yapılır: SharePoint uygulama sayfası veya Web bölümü için Kullanıcı denetimi oluşturma
  SharePoint çözümünüz için özel işlevler sağlayan özel kullanıcı denetimleri oluşturabilir ve bu işlevselliği projenizde yeniden kullanabilirsiniz. Kullanıcı denetimlerini bir Web Bölümü veya uygulama sayfasına dahil edebilir, diğer ASP.NET denetimlerini ve SharePoint denetimlerini ekleyebilir ve denetimin özelliklerini ve yöntemlerini tanımlayabilirsiniz. Kullanıcı denetimleri hakkında daha fazla bilgi için bkz. [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) ve [SharePoint 'te Kullanıcı denetimleri ve sunucu denetimleri](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/)oluşturma.

### <a name="to-create-a-user-control-for-sharepoint"></a>SharePoint için Kullanıcı denetimi oluşturmak için

1. Visual Studio 'da bir SharePoint projesi açın veya oluşturun.

     Bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. **Çözüm Gezgini**, proje düğümünü seçin.

3. Menü çubuğunda, **Proje**  >  **Yeni öğe Ekle**' yi seçin.

     **Yeni öğe Ekle** iletişim kutusu açılır.

4. **Yüklü** bölmesinde **Office/SharePoint** düğümünü seçin.

5. SharePoint şablonları listesinde, Kullanıcı denetimi ' ni **(yalnızca Grup çözümü)** seçin.

    > [!NOTE]
    > Kullanıcı denetimleri yalnızca Grup çözümlerinde çalışır.

6. **Ad** kutusunda, Kullanıcı denetimi için bir ad belirtin ve ardından **Ekle** düğmesini seçin.

     Visual Studio, projenize birkaç klasör ve dosya ekler. Bu dosyalar hakkında daha fazla bilgi için bkz. [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

     Varsayılan olarak, Kullanıcı denetimi dosyası, Visual Web Developer Designer 'ın **kaynak** görünümünde görüntülenir. Bu görünümde, denetimin XML işaretlemesini düzenleyebilirsiniz. Denetimleri **araç kutusundan**sürükleyerek görsel olarak tasarlamak istiyorsanız **Tasarım** görünümüne geçebilirsiniz. Bkz. [Tasarım görünümü, Web sayfası tasarımcısı](/previous-versions/aspnet/ms178149\(v\=vs.100\)).

7. Denetimde oluşan olayları işlemek istiyorsanız, Kullanıcı denetiminin kod dosyasına kod ekleyin.

     Bu dosya, Kullanıcı denetimi dosyası altında **Çözüm Gezgini** görüntülenir ve projenin diline bağlı olarak *. cs* veya *. vb* uzantısına sahiptir.

## <a name="see-also"></a>Ayrıca bkz.
- [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)
- [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
