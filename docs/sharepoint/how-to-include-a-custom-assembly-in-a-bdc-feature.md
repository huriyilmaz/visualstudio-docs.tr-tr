---
title: 'Nasıl yapılır: bir BDC özelliğine özel derleme ekleme | Microsoft Docs'
description: Bir iş verileri bağlantısı (BDC) özelliğine özel derlemeler ekleyin, böylece projenizin aynı çözümdeki diğer projelerdeki derlemelere başvurabilmesi sağlanır.
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
ms.openlocfilehash: 14026e6de7a376e4548723b4b540d314e499bbf1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093001"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Nasıl yapılır: bir BDC özelliğine özel bütünleştirilmiş kod ekleme
  Projeniz aynı çözümdeki diğer projelerden derlemelere başvurabilir. Ancak, **başvurulan derlemeleri LobSystems 'A ata** iletişim kutusunu kullanarak bu derlemeleri projenin özellik dosyasına eklemeniz gerekir.

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Bir iş verileri bağlantısı (BDC) özelliğine özel bir derleme eklemek için

1. **Çözüm Gezgini**, İVB modelini içeren klasörü seçin.

2. **Görünüm** menüsünde **Özellikler penceresi**' ne tıklayın.

3. **özellikler** penceresinde **derlemeler** özelliğini ve ardından üç nokta düğmesini (![ASP.NET Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil tasarımcı elips")) seçin.

     **Başvurulan derlemeleri LobSystems 'A ata** iletişim kutusu görüntülenir.

4. **Bir derleme seçin** listesinde özel derlemeyi seçin.

    > [!NOTE]
    > Derlemeler, derlemeyi içeren projeye bir başvuru eklediyseniz, yalnızca **başvurulan derlemeleri LobSystems 'A ata** iletişim kutusunda görünür. Daha fazla bilgi için bkz. [nasıl yapılır: Başvuru Ekle Iletişim kutusunu kullanarak başvuru ekleme veya kaldırma](/previous-versions/wkze6zky(v=vs.140)).

5. **Başvuru özellikleri** grubunda, **LobSystem Scope** özelliği için görüntülenen listeyi açın, özel derlemeyi kullanan yöntemlerin lob sistemini seçin ve **Tamam** düğmesini seçin.

    > [!NOTE]
    > Özel derlemedeki kodun hatalarını ayıklamak için, derlemeyi çözüm paketine eklemeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: ek derlemeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: yerelleştirilmiş adları, özellikleri ve izinleri belirtmek için kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [nasıl yapılır: SharePoint projesine mevcut bir BDC modeli dosyası ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Nasıl yapılır: BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md)
- [İş verilerini SharePoint olarak tümleştirin](../sharepoint/integrating-business-data-into-sharepoint.md)