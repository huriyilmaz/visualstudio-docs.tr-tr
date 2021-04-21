---
title: 'Nasıl yapılır: aramadan sonra program aracılığıyla seçimleri geri yükleme'
description: Bir Microsoft Word belgesinde aramadan sonra seçimleri program aracılığıyla geri yüklemek için Visual Studio 'Yu nasıl kullanabileceğinizi öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: 2a9f804e218ec9dfa0e0550501dec0c1aa8388ff
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824025"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Nasıl yapılır: aramadan sonra program aracılığıyla seçimleri geri yükleme
  Bir belgede metin bulup değiştirirseniz, arama tamamlandıktan sonra kullanıcının özgün seçimini geri yüklemek isteyebilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Örnek yordamdaki kod iki <xref:Microsoft.Office.Interop.Word.Range> nesne kullanır. Geçerli olanı depolar <xref:Microsoft.Office.Interop.Word.Selection> ve diğeri bir arama aralığı olarak kullanılacak tüm belgeyi ayarlar.

## <a name="to-restore-the-users-original-selection-after-a-search"></a>Bir aramadan sonra kullanıcının özgün seçimini geri yüklemek için

1. <xref:Microsoft.Office.Interop.Word.Range>Belge ve geçerli seçim için nesneleri oluşturun.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet83":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet83":::

2. Arama ve değiştirme işlemini gerçekleştirin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet84":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet84":::

3. Kullanıcının özgün seçimini geri yüklemek için başlangıç aralığını seçin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet85":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet85":::

   Aşağıdaki örnek, tüm yöntemi gösterir.

## <a name="example"></a>Örnek
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet82":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet82":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerde metni program aracılığıyla arama ve değiştirme](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Nasıl yapılır: Word 'de program aracılığıyla arama seçeneklerini ayarlama](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Nasıl yapılır: belgelerdeki bulunan öğeler aracılığıyla program aracılığıyla döngü yapma](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
