---
title: 'Nasıl Outlook: Outlook bir form bölgesi görüntülemesini engelleme'
description: Belirli bir öğe için Microsoft Office Outlook bir form bölgesi görüntülemesini önlemeyi öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9ae389e4094c0cff343cf373f70ac9bd1e1d846d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634014"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Nasıl Outlook: Outlook bir form bölgesi görüntülemesini engelleme
  Belirli bir öğe için bir form Microsoft Office Outlook görüntülemek istemeyebilirsiniz. Örneğin, bir kişi öğesi bir iş adresi içeriyorsa, bir haritada işletmenin konumunu gösteren bir form bölgesi görünmesini önleyebilirsiniz.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Bir Outlook bir form bölgesi görüntülemesini önlemek için

1. Değiştirmek istediğiniz form bölgesi için kod dosyasını açın.

2. Form Bölgesi **Fabrika kod** bölgesini genişletin.

3. sınıfın özelliğini `FormRegionInitializing` true olarak ayaran olay <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> işleyiciye kod **ekleyin.**

   Bu örnekte, kişi öğesi bir adres içeriyorsa, özelliği true olarak ayarlanır <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> ve form bölgesi görünmez. 

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::


## <a name="see-also"></a>Ayrıca bkz.
- [Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Adım adım kılavuz: Form Outlook tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Nasıl Outlook Add-in projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Adım adım kılavuz: Form Outlook tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Adım adım kılavuz: Veri kaynağında tasarlanmış bir form Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
