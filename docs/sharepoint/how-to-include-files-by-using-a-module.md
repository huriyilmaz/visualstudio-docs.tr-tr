---
title: 'Nasıl yapılır: modül kullanarak dosyaları Içerme | Microsoft Docs'
description: SharePoint için ASPX ana sayfaları, metin dosyaları veya görüntüler gibi dosyaları dağıtmanıza imkan tanıyan bir kapsayıcı olan modül kullanarak dosyaları eklemeyi öğrenin.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: d5f229d09ea5a4cceaa0f85dc89612636c072471
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130968"
---
# <a name="how-to-include-files-by-using-a-module"></a>Nasıl yapılır: modül kullanarak dosyaları Içerme
  *Modüller* ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modüllerle karıştırılmamalıdır), SharePoint için aspx ana sayfaları, metin dosyaları veya görüntüler gibi dosyaları dağıtmanıza olanak sağlayan kapsayıcılardır.

 Bir dosyayı belge kitaplığı içinde veya normal bir dosya (örneğin, default. aspx) olarak belge kitaplığı dışında dağıtmayı seçebilirsiniz. Belge kitaplığına bir dosya eklemek için `Type="GhostableInLibrary"` **Dosya** öğesinde bir öznitelik olarak belirtin. bu ayar SharePoint, kitaplığa eklendiğinde dosyanıza gitmek için bir liste öğesi oluşturmasını söyler. Belge kitaplığı dışında bir dosya dağıtmak için, `Type="Ghostable"` **tür** özniteliğini belirtin veya yalnızca atlayın.

## <a name="add-a-module-to-a-sharepoint-solution"></a>SharePoint çözümüne modül ekleme

#### <a name="to-add-a-module"></a>Modül eklemek için

1. içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , bir SharePoint projesi açın veya oluşturun.

     daha fazla bilgi için bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. **Çözüm Gezgini**, proje düğümünü seçin ve ardından menü çubuğunda, **Project**  >  **yeni öğe ekle**' yi seçin.

     **Yeni öğe Ekle** iletişim kutusu açılır.

3. SharePoint şablonları listesinde **modül** şablonunu seçin ve sonra **ekle** düğmesini seçin.

     Bu adım, projede Module1 adlı bir düğüm oluşturur.

4. Module1 altında *Sample.txt* dosyasını silin.

     Sample.txt, tüm yeni modüllerde örnek olarak dahildir ve gerekli değildir. (Dosyayı silmenin Ayrıca, girişini modülün *Elements.xml* dosyasından kaldırdığına unutmayın.)

5. dosyalarınızın SharePoint içindeki belirli bir klasör yapısına dağıtılmasını istiyorsanız, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] module1 düğümünü seçerek ve ardından menü çubuğunda **Project**, **yeni klasör**' i seçerek bu klasörleri module1 içinde oluşturun.

6. dosyayı eklemek istediğiniz klasörü seçin ve ardından menü çubuğunda **Project**, **var olan öğeyi ekle**' yi seçin.

7. SharePoint dağıtmak istediğiniz bir veya daha fazla dosyayı seçin ve sonra **Ekle** düğmesini seçin.

     Projeye bir dosya eklediğinizde, bu öğenin bir girişi modülün Elements.xml dosyasına otomatik olarak eklenir. proje dağıtıldığında, dosyalar, proje kök dizinine göre SharePoint sunucuya kopyalanır; örneğin, **dosya** öğesinin **Url** özniteliği tarafından belirtilen `Url="Module1/New Folder/SomeFile.doc` . Bir dosyanın dağıtım konumunu değiştirmek istiyorsanız, dosyayı **Çözüm Gezgini** başka bir klasöre taşıyın ya da **URL** ayarını değiştirin.

8. Bir belge kitaplığında görünmesini istediğiniz herhangi bir dosya için, `Type="GhostableInLibrary"` *Elements.xml*' deki girdisine özniteliği ekleyin. Örneğin,

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. Projeyi dağıtın.

     Dosyalar SharePoint içindeki belirtilen konumlara kopyalar.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [SharePoint Çözümleri Geliştirme](../sharepoint/developing-sharepoint-solutions.md)
