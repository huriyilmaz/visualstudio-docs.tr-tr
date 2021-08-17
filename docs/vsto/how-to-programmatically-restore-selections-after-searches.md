---
title: 'Nasıl kurulur: Arama sonrasındaki seçimleri program aracılığıyla geri yükleme'
description: Visual Studio belgesinde yapılan aramaların ardından seçimleri program aracılığıyla geri yüklemek için Microsoft Word öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 57f71cad1335c29f4e92bb760de251f6100f51a1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026180"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Nasıl kurulur: Arama sonrasındaki seçimleri program aracılığıyla geri yükleme
  Belgede metin bulup değiştirirsanız, arama tamamlandıktan sonra kullanıcının özgün seçimini geri yüklemek iyi olabilir.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Örnek yordamdaki kod iki nesne <xref:Microsoft.Office.Interop.Word.Range> kullanır. Biri geçerli olan <xref:Microsoft.Office.Interop.Word.Selection> 'i depolar, biri ise belgenin tamamını arama aralığı olarak kullanmak üzere ayarlar.

## <a name="to-restore-the-users-original-selection-after-a-search"></a>Bir aramadan sonra kullanıcının özgün seçimini geri yüklemek için

1. Belge <xref:Microsoft.Office.Interop.Word.Range> ve geçerli seçim için nesneleri oluşturun.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet83":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet83":::

2. Arama ve değiştirme işlemini gerçekleştirin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet84":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet84":::

3. Kullanıcının özgün seçimini geri yüklemek için başlangıç aralığını seçin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet85":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet85":::

   Aşağıdaki örnek, tam yöntemini gösterir.

## <a name="example"></a>Örnek
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet82":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet82":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Belgelerde program aracılığıyla metin arama ve değiştirme](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Nasıl yapabilirsiniz: Word'de arama seçeneklerini program aracılığıyla ayarlama](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Nasıl kullanılır: Belgelerde bulunan öğelerde program aracılığıyla döngü](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
