---
title: 'Nasıl |: BDC Model | Microsoft Docs'
description: Bu tür bir öğe için Visual Studio şablonunu kullanarak bir İş Verileri Bağlantısı (BDC) modeli oluşturun ve ardından modeli herhangi bir SharePoint projesine ekler.
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
ms.workload:
- office
ms.openlocfilehash: fd5184f87cf3895e1519a91e6f7e6661702f1181
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112415"
---
# <a name="how-to-create-a-bdc-model"></a>Nasıl: BDC modeli oluşturma

  Bu tür bir öğenin şablonunu kullanarak ve ardından modeli herhangi bir SharePoint projesine ekleyerek bir İş Verileri Bağlantısı (BDC) modeli oluşturabilirsiniz. Daha fazla bilgi için [bkz. İş verileri bağlantı modeli oluşturma.](../sharepoint/creating-a-business-data-connectivity-model.md) Modeli tasarlama hakkında daha fazla bilgi için [bkz. İş verileri bağlantı modeli tasarlama.](../sharepoint/designing-a-business-data-connectivity-model.md)

## <a name="to-create-a-bdc-project"></a>BDC projesi oluşturmak için

1. Menü çubuğunda Dosya Yeni **Proje'yi**  >    >  **seçin.**
::: moniker range="=vs-2017"
   > [!NOTE]
   > IDE'niz geliştirme ayarlarını kullanmak Visual Basic, Dosya Yeni **Proje'yi**  >  **seçin.**

  Yeni **Proje iletişim** kutusu açılır.

2. Visual **C#** **Visual Basic** altında **Office/SharePoint**, **SharePoint Çözümleri'ni seçin.**

3. Şablonlar **bölmesinde** **SharePoint 2013 - Boş** Proje öğesini ve ardından Tamam **düğmesini** seçin.

     **SharePoint Özelleştirme Sihirbazı** açılır.
::: moniker-end
::: moniker range=">=vs-2019"
2. Yeni **Proje Oluştur iletişim kutusunda,** yüklemiş olduğu *SharePoint'in* belirli bir sürümü için SharePoint Boş Projesi *'ni seçin. Örneğin, SharePoint 2019 yüklemeniz varsa **SharePoint 2019 - Boş Proje şablonunu** seçin.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. 5000000000000000000000000000000000000000000000000000000000 

::: moniker-end
4. Hata **ayıklama için siteyi** ve güvenlik düzeyini belirtin sayfasında, yerel bilgisayardaki bir SharePoint  sitesinin URL'sini belirtin, Grup çözümü olarak dağıt seçeneğini belirleyin ve ardından Son **düğmesini** seçin.

     Modeli belirttiğiniz SharePoint sitesinde test edebilirsiniz.

    > [!IMPORTANT]
    > BDC modelleri yalnızca grup çözümlerini desteklemesi nedeniyle projeyi bir grup çözümü olarak dağıtmalısiniz.

     Boş bir SharePoint projesi oluşturulur.

5. Menü çubuğunda Proje Yeni Öğe  >  **Ekle'yi seçin.**

6. Yeni **Öğe Ekle iletişim** kutusunda **Office/SharePoint düğümünü** seçin.

7. SharePoint şablonları listesinde İş Verileri Bağlantı Modeli **(Yalnızca Grup Çözümü) 'yi seçin.**

8. Ad **kutusunda,** BDC modeli için bir ad belirtin ve ardından Ekle **düğmesini** seçin.

     Projeye **bir İş** Verileri Bağlantı Modeli öğesi eklenir. Varsayılan olarak, model BDC tasarımcısında görünür. Daha fazla bilgi için [bkz. İş verileri bağlantı modeli oluşturma.](../sharepoint/creating-a-business-data-connectivity-model.md)

## <a name="see-also"></a>Ayrıca bkz.

- [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Nasıl olur: Bir SharePoint projesine var olan bir BDC model dosyası ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Nasıl kullanılır: Yerelleştirilmiş adları, özellikleri ve izinleri belirtmek için kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Nasıl kurulur: Bir BDC özelliğine özel derleme dahil](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)
