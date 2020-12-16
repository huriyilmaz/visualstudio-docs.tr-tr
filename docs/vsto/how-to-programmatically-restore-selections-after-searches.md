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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d396602a5d2bc0c3a90d32256bf226348abff3f3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528278"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Nasıl yapılır: aramadan sonra program aracılığıyla seçimleri geri yükleme
  Bir belgede metin bulup değiştirirseniz, arama tamamlandıktan sonra kullanıcının özgün seçimini geri yüklemek isteyebilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Örnek yordamdaki kod iki <xref:Microsoft.Office.Interop.Word.Range> nesne kullanır. Geçerli olanı depolar <xref:Microsoft.Office.Interop.Word.Selection> ve diğeri bir arama aralığı olarak kullanılacak tüm belgeyi ayarlar.

## <a name="to-restore-the-users-original-selection-after-a-search"></a>Bir aramadan sonra kullanıcının özgün seçimini geri yüklemek için

1. <xref:Microsoft.Office.Interop.Word.Range>Belge ve geçerli seçim için nesneleri oluşturun.

    [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
    [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]

2. Arama ve değiştirme işlemini gerçekleştirin.

    [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
    [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]

3. Kullanıcının özgün seçimini geri yüklemek için başlangıç aralığını seçin.

    [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
    [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]

   Aşağıdaki örnek, tüm yöntemi gösterir.

## <a name="example"></a>Örnek
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerde metni program aracılığıyla arama ve değiştirme](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Nasıl yapılır: Word 'de program aracılığıyla arama seçeneklerini ayarlama](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Nasıl yapılır: belgelerdeki bulunan öğeler aracılığıyla program aracılığıyla döngü yapma](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
