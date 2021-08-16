---
title: 'Nasıl kurulur: BDC Özellik Özelliklerine Özel Bir Derleme | Microsoft Docs'
description: Projenizin aynı çözümdeki diğer projelerden derlemelere başvuramalarını için bir iş veri bağlantısı (BDC) özelliğine özel derlemeler ekleyin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: c45867e769f14323b10c3d42fb5bf52a9560823da1eb3b62246297e19dd69396
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409559"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Nasıl kurulur: Bir BDC özelliğine özel derleme dahil
  Projeniz aynı çözümdeki diğer projelerden derlemelere başvurur. Ancak, Başvurulan derlemeleri **LobSystems'a** ata iletişim kutusunu kullanarak bu derlemeleri projenin özellik dosyasına eklemeniz gerekir.

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Bir iş verileri bağlantısı (BDC) özelliğine özel bir derleme eklemek için

1. Bu **Çözüm Gezgini,** BDC modelini içeren klasörü seçin.

2. Görünüm menüsünde **Özellikler** **Penceresi'ne tıklayın.**

3. Özellikler **penceresinde** Derlemeler özelliğini **seçin ve** ardından üç nokta düğmesini ( ASP.NET Mobil Tasarımcı üç nokta ![) seçin.](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcı üç nokta")

     **Başvurulan derlemeleri LobSystems'a ata** iletişim kutusu görüntülenir.

4. Bir **Derleme Seçin listesinde** özel derlemeyi seçin.

    > [!NOTE]
    > Derlemeler yalnızca derlemeyi içeren projeye bir başvuru eklediyebilirsiniz, Başvurulan derlemeleri **LobSystems'a** ata iletişim kutusunda görünür. Daha fazla bilgi için, [bkz. How to: Add References By Using The References (Başvuru](/previous-versions/wkze6zky(v=vs.140))Ekle İletişim Kutusunu Kullanarak Başvuru Ekleme veya Kaldırma).

5. Başvuru **Özellikleri grubunda** **LobSystem Scope** özelliği için görüntülenen listeyi açın, özel derlemeyi kullanan yöntemlerin LOB Sistemi'ne tıklayın ve ardından **Tamam düğmesini** seçin.

    > [!NOTE]
    > Özel derlemede kodda hata ayıklamak için derlemeyi çözüm paketine eklemeniz gerekir. Daha fazla bilgi için, [bkz. How to: Add and remove additional assemblies](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Yerelleştirilmiş adları, özellikleri ve izinleri belirtmek için kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Nasıl olur: Mevcut bir BDC modeli dosyasını SharePoint ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Nasıl: BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md)
- [İş verilerini iş verileriyle SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)