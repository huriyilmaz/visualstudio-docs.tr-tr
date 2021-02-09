---
title: 'Nasıl yapılır: bir yöntem örneği tanımlama | Microsoft Docs'
description: İş verileri bağlantısı (BDC) modelinizdeki bir yöntem için nasıl Yöntem örneği tanımlanacağını anlayın.
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
ms.workload:
- office
ms.openlocfilehash: 055193123f99825027238166d762ce54b288d716
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885670"
---
# <a name="how-to-define-a-method-instance"></a>Nasıl yapılır: Yöntem örneği tanımlama
  Modelinizdeki her yöntem için en az bir yöntem örneği tanımlamanız gerekir.

 **IVB yöntemi ayrıntıları** penceresini kullanarak bir yöntem örneği ekleyin. Yöntem örneğini eklediğinizde, Visual Studio `<MethodInstance>` projenize model dosyasının XML öğesine bir öğesi ekler. Bir öğenin öznitelikleri hakkında daha fazla bilgi için `<MethodInstance>` bkz. [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

### <a name="to-define-a-method-instance"></a>Bir yöntem örneği tanımlamak için

1. **BDC Yöntem ayrıntıları** penceresinde, bir yöntemin düğümünü genişletin ve ardından **örnekler** düğümünü genişletin.

2. **Yöntem örneği Ekle** listesinde, **Bulucu örneği oluştur**' u seçin.

     **Örnekler** düğümünün altında yeni bir yöntem örneği görüntülenir.

3. Menü çubuğunda   >  **Özellikler penceresini** görüntüle ' yi seçin.

4. **Özellikler** penceresinde, yöntem örneğinin özelliklerini ayarlayın. Her özellik hakkında daha fazla bilgi için bkz. [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

## <a name="see-also"></a>Ayrıca bkz.
- [IVB modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl yapılır: modele varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
