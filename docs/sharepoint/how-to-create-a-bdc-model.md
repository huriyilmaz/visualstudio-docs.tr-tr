---
title: 'Nasıl |: BDC Model | Microsoft Docs'
description: Bu tür bir öğe için Visual Studio şablonunu kullanarak bir İş Verileri Bağlantısı (BDC) modeli oluşturun ve ardından modeli herhangi bir SharePoint ekleme.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 4180821b1b37c2d9f0e9e2fcd5cadb8780c0a86c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106840"
---
# <a name="how-to-create-a-bdc-model"></a>Nasıl: BDC modeli oluşturma

  Bu tür bir öğenin şablonunu kullanarak bir İş Verileri Bağlantısı (BDC) modeli oluşturabilir ve ardından modeli herhangi bir uygulama projesine SharePoint oluşturabilirsiniz. Daha fazla bilgi için [bkz. İş verileri bağlantı modeli oluşturma.](../sharepoint/creating-a-business-data-connectivity-model.md) Modeli tasarlama hakkında daha fazla bilgi için [bkz. İş verileri bağlantı modeli tasarlama.](../sharepoint/designing-a-business-data-connectivity-model.md)

## <a name="to-create-a-bdc-project"></a>BDC projesi oluşturmak için

1. Menü çubuğunda Dosya Yeni **dosya'Project.**  >    >  
::: moniker range="=vs-2017"
   > [!NOTE]
   > IDE'niz geliştirme ayarlarını kullanmak Visual Basic, Dosya Yeni **dosya'Project.**  >  

  Yeni **Project** iletişim kutusu açılır.

2. Visual Basic  **veya Visual C#** altında, **Office/SharePoint**, SharePoint **Çözüm'SharePoint seçin.**

3. Şablonlar **bölmesinde** SharePoint **2013 - Boş Project** öğesini seçin ve ardından Tamam **düğmesini** seçin.

     SharePoint **Özelleştirme Sihirbazı** açılır.
::: moniker-end
::: moniker range=">=vs-2019"
2. Yeni **Sürüm Oluştur Project** iletişim kutusunda, *SharePoint sürümünün* Project * boş SharePoint seçin. Örneğin, 2019 yüklemesi SharePoint **2019 - Boş** SharePoint şablonunu Project seçin.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. 5000000000000000000000000000000000000000000000000000000000 

::: moniker-end
4. Hata **ayıklama için siteyi** ve güvenlik düzeyini belirtin sayfasında, yerel bilgisayardaki bir SharePoint sitesinin  URL'sini belirtin, Grup çözümü olarak dağıt seçeneğini belirleyin ve ardından Son **düğmesini** seçin.

     Modeli, belirttiğiniz SharePoint sitesinde test edin.

    > [!IMPORTANT]
    > BDC modelleri yalnızca grup çözümlerini desteklemesi nedeniyle projeyi bir grup çözümü olarak dağıtmalısiniz.

     Boş bir SharePoint projesi oluşturulur.

5. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

6. Yeni **Öğe Ekle iletişim** kutusunda, **Office/SharePoint** seçin.

7. Uygulama şablonları listesinde SharePoint Veri Bağlantısı Modeli (Yalnızca Grup **Çözümü) 'yi seçin.**

8. Ad **kutusunda,** BDC modeli için bir ad belirtin ve ardından Ekle **düğmesini** seçin.

     Projeye **bir İş** Verileri Bağlantı Modeli öğesi eklenir. Varsayılan olarak, model BDC tasarımcısında görünür. Daha fazla bilgi için [bkz. İş verileri bağlantı modeli oluşturma.](../sharepoint/creating-a-business-data-connectivity-model.md)

## <a name="see-also"></a>Ayrıca bkz.

- [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Nasıl olur: Mevcut bir BDC model dosyasını SharePoint ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Nasıl kullanılır: Yerelleştirilmiş adları, özellikleri ve izinleri belirtmek için kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Nasıl kurulur: Bir BDC özelliğine özel derleme dahil](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [İş verilerini iş verileriyle SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
