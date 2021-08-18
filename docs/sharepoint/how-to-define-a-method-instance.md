---
title: 'Nasıl: Yöntem Örneği Tanımlama | Microsoft Docs'
description: İş verileri bağlantısı (BDC) modelinize bir yöntem için yöntem örneği tanımlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 1b01a254283befcd790b0e2ecbb0a35084c5b944
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026959"
---
# <a name="how-to-define-a-method-instance"></a>Nasıl yapılacaklar: Yöntem örneği tanımlama
  Modelinizin her yöntemi için en az bir yöntem örneği tanımlamanız gerekir.

 **BDC** Yöntem Ayrıntıları penceresini kullanarak bir yöntem örneği ekleyin. Yöntem örneğini eklerken, Visual Studio projenizin model dosyasının `<MethodInstance>` XML'ine bir öğe ekler. Bir öğenin öznitelikleri hakkında daha fazla bilgi `<MethodInstance>` için bkz. [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

### <a name="to-define-a-method-instance"></a>Yöntem örneği tanımlamak için

1. **BDC Yöntem Ayrıntıları** penceresinde bir yöntemin düğümünü ve ardından Örnekler **düğümünü** genişletin.

2. Yöntem **Örneği Ekle listesinde Bulıcı** Örneği **Oluştur'a tıklayın.**

     Örnekler düğümünün altında yeni bir **yöntem örneği** görünür.

3. Menü çubuğunda Özellikler Penceresini **Görüntüle'yi**  >  **seçin.**

4. Özellikler **penceresinde** yöntem örneğinin özelliklerini ayarlayın. Her özellik hakkında daha fazla bilgi için bkz. [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

## <a name="see-also"></a>Ayrıca bkz.
- [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl kullanılır: Modele varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Nasıl: Yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl: Bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
