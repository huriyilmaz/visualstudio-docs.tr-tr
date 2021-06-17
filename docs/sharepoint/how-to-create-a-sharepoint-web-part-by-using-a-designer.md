---
title: 'Nasıl kullanılır: Tasarımcı | Kullanarak SharePoint Web Bölümü Oluşturma Microsoft Docs'
titleSuffix: ''
description: Bir SharePoint projesine görsel web bölümü öğesi ekleyerek bir web bölümü oluşturun. Bu öğe, Görsel Web Geliştirici tasarımcısını Visual Studio.
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
ms.workload:
- office
ms.openlocfilehash: cbbb290af0029329910a23a71f68024ee0e5e5f4
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112380"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Nasıl kullanılır: Tasarımcı kullanarak SharePoint Web Bölümü oluşturma

  Herhangi bir SharePoint projesine Görsel **Web Bölümü öğesi** ekleyerek bir web bölümü oluşturabilirsiniz. Bu işlem Visual Web Developer tasarımcısını Visual Studio web parçasına denetimler ve kod eklebilirsiniz. Görsel web bölümleri, web bölümleriyle aynı şekilde işlev gösterir. Tek fark, Görsel Web Geliştirici tasarımcısında görsel web bölümleri tasarlamanızdır.

## <a name="to-create-a-project-for-visual-web-parts"></a>Görsel web bölümleri için proje oluşturmak için

1. Menü çubuğunda Dosya Yeni **Proje'yi**  >   >  **seçin.**
::: moniker range="=vs-2017"

2. Yeni Proje **iletişim kutusundaki** **Visual C#** veya Visual Basic **altında** **Office/SharePoint** düğümünü genişletin ve **ardından SharePoint Çözümleri kategorisini** seçin.

3. Proje şablonları listesinde **SharePoint 2013 - Görsel Web Bölümü'ne tıklayın** ve ardından Tamam **düğmesini** seçin.

     **SharePoint Özelleştirme Sihirbazı** görüntülenir.
::: moniker-end
::: moniker range=">=vs-2019"
2. Yeni **Proje Oluştur iletişim kutusunda,** yüklemiş olduğunu *SharePoint'in* belirli bir sürümü için SharePoint Görsel Web Bölümü *'ni seçin. Örneğin, SharePoint 2019 yüklemeniz varsa **SharePoint 2019 - Visual Web Bölümü şablonunu** seçin.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. 5000000000000000000000000000000000000000000000000000000000 

::: moniker-end
4. Hata **ayıklama için siteyi** ve güvenlik düzeyini belirtin sayfasında, yerel bilgisayarda bulunan bir SharePoint sitesinin URL'sini belirtin ve ardından Son **düğmesini** seçin.

     Bu **Çözüm Gezgini** bir web bölümü görüntülenir. Web bölümünü Visual Web Geliştirici tasarımcısında tasarladikten sonra, belirttiğiniz sitede test edin.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Mevcut bir SharePoint projesine görsel web bölümü eklemek için

1. Menü çubuğunda Proje Yeni Öğe  >  **Ekle'yi seçin.**

2. Yeni **Öğe Ekle iletişim** kutusunda **Office/SharePoint düğümünü** seçin.

3. Proje şablonları listesinde Görsel **Web Bölümü'leri seçin,** buna ad ve ardından Ekle **düğmesini** seçin.

     Bu **Çözüm Gezgini** bölümünde web bölümünüz görünür. Web bölümünü Visual Web Geliştirici tasarımcısında tasarladikten sonra, belirttiğiniz sitede test edin.

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint için web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Nasıl: SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Adım adım kılavuz: SharePoint için web bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Adım adım kılavuz: Tasarımcı kullanarak SharePoint için web bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
