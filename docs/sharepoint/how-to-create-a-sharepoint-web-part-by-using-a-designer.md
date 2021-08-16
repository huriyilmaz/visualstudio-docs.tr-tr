---
title: 'nasıl yapılır: tasarımcı kullanarak SharePoint Web bölümü oluşturma | Microsoft Docs'
titleSuffix: ''
description: visual web Developer designer 'ı Visual Studio açılan SharePoint projesine ekleyerek bir web bölümü oluşturun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: ac72b8e2d023fa71e48f01c7ddd9ed662eb89fd50287bd2dd1b854d523090a14
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409671"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>nasıl yapılır: tasarımcı kullanarak SharePoint Web bölümü oluşturma

  herhangi bir SharePoint projesine **görsel bir web bölümü** öğesi ekleyerek bir web bölümü oluşturabilirsiniz. bu, web bölümüne denetimler ve kod ekleyebileceğiniz Visual Studio Visual Web Developer designer 'ı açar. Görsel Web bölümleri, Web bölümleri ile aynı şekilde çalışır. Tek fark, Visual Web Developer Designer 'da görsel Web bölümleri tasarlayamanızdır.

## <a name="to-create-a-project-for-visual-web-parts"></a>Görsel Web bölümleri için bir proje oluşturmak için

1. menü çubuğunda **dosya**  > **yeni**  >  **Project**' yi seçin.
::: moniker range="=vs-2017"

2. **yeni Project** iletişim kutusunda, **Visual C#** veya **Visual Basic** altında **Office/SharePoint** düğümünü genişletin ve ardından **SharePoint Solutions** kategorisini seçin.

3. proje şablonları listesinde **SharePoint 2013-Visual Web bölümü**' nu seçin ve ardından **tamam** düğmesini seçin.

     **SharePoint özelleştirme sihirbazı** görüntülenir.
::: moniker-end
::: moniker range=">=vs-2019"
2. **yeni Project oluştur** iletişim kutusunda, yüklemiş olduğunuz SharePoint özgü sürümü için *Visual Web bölümü * SharePoint* seçin. örneğin, SharePoint 2019 yüklemesi varsa **SharePoint 2019-Visual Web bölümü** şablonunu seçin.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. İsterseniz projenin adını değiştirin ve ardından **Oluştur** düğmesini seçin.

::: moniker-end
4. **hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, yerel bilgisayarda bir SharePoint sitesinin URL 'sini belirtin ve ardından **son** düğmesini seçin.

     **Çözüm Gezgini**, bir Web bölümü görüntülenir. Web bölümünü Visual Web Developer Designer 'da tasarladıktan sonra, belirttiğiniz sitede test edersiniz.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>mevcut bir SharePoint projesine bir görsel web bölümü eklemek için

1. menü çubuğunda **Project**  >  **yeni öğe ekle**' yi seçin.

2. **yeni öğe ekle** iletişim kutusunda **Office/SharePoint** düğümünü seçin.

3. Proje şablonları listesinde, **Visual Web Bölümü**' nu seçin, adlandırın ve ardından **Ekle** düğmesini seçin.

     **Çözüm Gezgini**, Web bölümü görüntülenir. Web bölümünü Visual Web Developer Designer 'da tasarladıktan sonra, belirttiğiniz sitede test edersiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
- [nasıl yapılır: SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [İzlenecek yol: SharePoint için bir Web Bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [izlenecek yol: tasarımcı kullanarak SharePoint için web bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
