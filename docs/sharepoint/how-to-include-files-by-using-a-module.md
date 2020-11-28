---
title: 'Nasıl yapılır: modül kullanarak dosyaları Içerme | Microsoft Docs'
description: ASPX ana sayfaları, metin dosyaları veya görüntüler gibi dosyaları SharePoint 'e dağıtmanıza imkan tanıyan bir kapsayıcı olan modül kullanarak nasıl dosya ekleneceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 381cb529db3f4116a9c42041c26e0e1e242073df
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305421"
---
# <a name="how-to-include-files-by-using-a-module"></a>Nasıl yapılır: modül kullanarak dosyaları Içerme
  *Modüller* ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modüllerle KARıŞTıRıLMAMALıDıR), aspx ana sayfaları, metin dosyaları veya görüntüler gibi dosyaları SharePoint 'e dağıtmanızı sağlayan kapsayıcılardır.

 Bir dosyayı belge kitaplığı içinde veya normal bir dosya (örneğin, default. aspx) olarak belge kitaplığı dışında dağıtmayı seçebilirsiniz. Belge kitaplığına bir dosya eklemek için `Type="GhostableInLibrary"` **Dosya** öğesinde bir öznitelik olarak belirtin. Bu ayar SharePoint 'e, kitaplığa eklendiğinde dosyanıza gitmek için bir liste öğesi oluşturmasını söyler. Belge kitaplığı dışında bir dosya dağıtmak için, `Type="Ghostable"` **tür** özniteliğini belirtin veya yalnızca atlayın.

## <a name="add-a-module-to-a-sharepoint-solution"></a>SharePoint çözümüne modül ekleme

#### <a name="to-add-a-module"></a>Modül eklemek için

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , bir SharePoint projesi açın veya oluşturun.

     Daha fazla bilgi için bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. **Çözüm Gezgini**, proje düğümünü seçin ve ardından menü çubuğunda **Proje**  >  **Ekle yeni öğe**' yi seçin.

     **Yeni öğe Ekle** iletişim kutusu açılır.

3. SharePoint şablonları listesinde **Modül** şablonunu seçin ve sonra **Ekle** düğmesini seçin.

     Bu adım, projede Module1 adlı bir düğüm oluşturur.

4. Module1 altında *Sample.txt* dosyasını silin.

     Sample.txt, tüm yeni modüllerde örnek olarak dahildir ve gerekli değildir. (Dosyayı silmenin Ayrıca, girişini modülün *Elements.xml* dosyasından kaldırdığına unutmayın.)

5. Dosyalarınızın SharePoint 'te belirli bir klasör yapısına dağıtılmasını istiyorsanız, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Module1 düğümünü seçerek ve ardından menü çubuğunda **Proje**, **Yeni klasör**' i seçerek bu klasörleri Module1 içinde oluşturun.

6. Dosyayı eklemek istediğiniz klasörü seçin ve ardından menü çubuğunda **Proje**, **Varolan öğe Ekle**' yi seçin.

7. SharePoint 'e dağıtmak istediğiniz bir veya daha fazla dosya seçin ve sonra **Ekle** düğmesini seçin.

     Projeye bir dosya eklediğinizde, bu öğenin bir girişi modülün Elements.xml dosyasına otomatik olarak eklenir. Proje dağıtıldığında, dosyalar, **Dosya** öğesinin **URL** özniteliği tarafından belirtilen gibi, projenin kök dizinine göre SharePoint sunucusuna kopyalanır `Url="Module1/New Folder/SomeFile.doc` . Bir dosyanın dağıtım konumunu değiştirmek istiyorsanız, dosyayı **Çözüm Gezgini** başka bir klasöre taşıyın ya da **URL** ayarını değiştirin.

8. Bir belge kitaplığında görünmesini istediğiniz herhangi bir dosya için, `Type="GhostableInLibrary"` *Elements.xml*' deki girdisine özniteliği ekleyin. Örneğin,

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. Projeyi dağıtın.

     Dosyalar, SharePoint 'te belirtilen konumlara kopyalar.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [SharePoint Çözümleri Geliştirme](../sharepoint/developing-sharepoint-solutions.md)
