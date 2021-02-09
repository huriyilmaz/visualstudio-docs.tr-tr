---
title: "Nasıl yapılır: Outlook 'un form bölgesini görüntülemesini engelleme"
description: Microsoft Office Outlook 'un belirli bir öğe için form bölgesi görüntülemesini nasıl engelleyebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f6e6b00e8e26d261aac18dd48af1d912bd6ffad1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899546"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Nasıl yapılır: Outlook 'un form bölgesini görüntülemesini engelleme
  Outlook Microsoft Office belirli bir öğe için bir form bölgesi görüntülemesini istemediğiniz durumlar olabilir. Örneğin, bir kişi öğesi iş adresi içermiyorsa, bir haritadaki işin konumunu gösteren bir form bölgesinin görüntülenmesini engelleyebilirsiniz.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Outlook 'un form bölgesi görüntülemesini engellemek için

1. Değiştirmek istediğiniz form bölgesinin kod dosyasını açın.

2. **Form bölgesi fabrikası** kod bölgesini genişletin.

3. `FormRegionInitializing` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> Sınıfının özelliğini **true** olarak ayarlayan olay işleyicisine kod ekleyin.

   Bu örnekte, kişi öğesi bir adres içermiyorsa, <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliği **true** olarak ayarlanır ve form bölgesi görünmez.

## <a name="example"></a>Örnek
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [İzlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [İzlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [İzlenecek yol: Outlook 'ta tasarlanan form bölgesini Içeri aktarma](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
