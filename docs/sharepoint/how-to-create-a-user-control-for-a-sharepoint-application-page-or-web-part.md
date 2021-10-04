---
title: Uygulama sayfası veya web SharePoint için kullanıcı denetimi oluşturma
titleSuffix: ''
description: SharePoint çözümünüz için özel işlevsellik sağlayan özel kullanıcı denetimleri oluşturun ve bu işlevselliği bir web bölümü veya uygulama sayfasında yeniden kullanın.
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
ms.openlocfilehash: 891f68a44087506ad2d61c3db7ead70d5a01ae70
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129430795"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Nasıl SharePoint uygulama sayfası veya web bölümü için kullanıcı denetimi oluşturma
  SharePoint çözümünüz için özel işlevsellik sağlayan özel kullanıcı denetimleri oluşturabilir ve bu işlevi projeniz içinde yeniden kullanabilirsiniz. Kullanıcı denetimlerini bir web bölümü veya uygulama sayfasına ekleyebilir, diğer ASP.NET denetimlerini ve SharePoint denetim özelliklerini ve yöntemlerini tanımlayabilirsiniz. Kullanıcı denetimleri hakkında daha fazla bilgi için bkz. [Web](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma ve Web'de Kullanıcı Denetimleri ve SharePoint.

### <a name="to-create-a-user-control-for-sharepoint"></a>SharePoint için kullanıcı denetimi oluşturmak SharePoint

1. Bu Visual Studio bir proje açın veya SharePoint oluşturun.

     Bkz. [SharePoint proje ve proje öğesi şablonları.](../sharepoint/sharepoint-project-and-project-item-templates.md)

2. Bu **Çözüm Gezgini** proje düğümünü seçin.

3. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

     Yeni **Öğe Ekle iletişim** kutusu açılır.

4. Yüklü **bölmesinde,** **Office/SharePoint** seçin.

5. Uygulama şablonları listesinde SharePoint Denetimi (Yalnızca Grup **Çözümü) 'yi seçin.**

    > [!NOTE]
    > Kullanıcı denetimleri yalnızca grup çözümlerinde çalışır.

6. Ad **kutusunda,** kullanıcı denetimi için bir ad belirtin ve ardından Ekle **düğmesini** seçin.

     Visual Studio projenize birkaç klasör ve dosya ekler. Bu dosyalar hakkında daha fazla bilgi için [bkz. Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma.](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)

     Varsayılan olarak, kullanıcı denetim dosyası Visual Web **Geliştirici tasarımcısının** Kaynak görünümünde görünür. Bu görünümde denetimin XML işaretlemesini düzenleyebilirsiniz. Denetimi Araç **Kutusundan** sürükleyerek görsel olarak tasarlamak için Tasarım görünümüne **geçebilirsiniz.** Bkz. [Tasarım Görünümü, Web Sayfası Tasarımcısı.](/previous-versions/aspnet/ms178149\(v\=vs.100\))

7. Denetimde oluşan olayları işlemek için kullanıcı denetimi kod dosyasına kod ekleyin.

     Bu dosya, **Çözüm Gezgini** denetimi dosyası altında görünür ve projenin diline bağlı olarak *.cs* veya *.vb* uzantısına sahip olur.

## <a name="see-also"></a>Ayrıca bkz.
- [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)
- [SharePoint için web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
