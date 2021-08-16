---
title: 'Nasıl Outlook: Outlook bir form bölgesi görüntülemesini engelleme'
description: Belirli bir öğe için Microsoft Office Outlook bir form bölgesi görüntülemesini nasıl önleyebilirsiniz?
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
ms.openlocfilehash: 331667013d5591f57d96b9f1bfa5f7542042ecc072c2eb650bf2ae5bbd0292a0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408805"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Nasıl Outlook: Outlook bir form bölgesi görüntülemesini engelleme
  Belirli bir öğe için bir form Microsoft Office Outlook görüntülemek istemeyebilirsiniz. Örneğin, bir kişi öğesi bir iş adresi içeriyorsa, bir haritada işletmenin konumunu gösteren bir form bölgesi görünmesini önleyebilirsiniz.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Bir Outlook bir form bölgesi görüntülemesini önlemek için

1. Değiştirmek istediğiniz form bölgesi için kod dosyasını açın.

2. Form Bölgesi **Fabrika kod** bölgesini genişletin.

3. sınıfın özelliğini `FormRegionInitializing` true olarak ayaran olay <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> işleyiciye kod **ekleyin.**

   Bu örnekte, kişi öğesi bir adres içeriyorsa, özellik true olarak ayarlanır <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> ve form bölgesi görünmez. 

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::


## <a name="see-also"></a>Ayrıca bkz.
- [Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Adım adım kılavuz: Form Outlook tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Nasıl yapılanlar: Eklenti projesine Outlook bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Adım adım kılavuz: Form Outlook tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Adım adım kılavuz: Veri kaynağında tasarlanmış bir form Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
