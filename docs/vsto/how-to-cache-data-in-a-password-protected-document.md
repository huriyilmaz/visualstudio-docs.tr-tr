---
title: 'Nasıl yapılır: parola korumalı bir belgedeki verileri önbelleğe alma'
description: Bir parola ile korunan bir belge veya çalışma kitabındaki veri önbelleğine veri eklerseniz, projenizdeki iki yöntemi geçersiz kılarak önbelleğe alınmış verideki değişiklikleri kaydedebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd7efe4aa2aa14cb94a68f0729bc7fe3535888ee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954039"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Nasıl yapılır: parola korumalı bir belgedeki verileri önbelleğe alma
  Parola ile korunan bir belge veya çalışma kitabındaki veri önbelleğine veri eklerseniz, önbelleğe alınmış verilerde yapılan değişiklikler otomatik olarak kaydedilmez. Projenizdeki iki yöntemi geçersiz kılarak önbelleğe alınmış verideki değişiklikleri kaydedebilirsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Word belgelerinde önbelleğe alma

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Parolayla korunan bir Word belgesindeki verileri önbelleğe almak için

1. `ThisDocument`Sınıfında, önbelleğe alınacak bir ortak alanı veya özelliği işaretleyin. Daha fazla bilgi için bkz. [önbelleği verileri](../vsto/caching-data.md).

2. <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>Sınıftaki yöntemi geçersiz kılın `ThisDocument` ve belgeden korumayı kaldırın.

     Belge kaydedildiğinde, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] belgenin korumasını kaldırma fırsatı vermek için bu yöntemi çağırır. Bu, önbelleğe alınan verilerde yapılan değişikliklerin kaydedilmesini sağlar.

3. <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>Sınıfında yöntemi geçersiz kılın `ThisDocument` ve korumayı belgeye yeniden uygulayın.

     Belge kaydedildikten sonra, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] belgeye korumayı yeniden uygulama fırsatı vermek için bu yöntemi çağırır.

### <a name="example"></a>Örnek
 Aşağıdaki kod örneğinde, bir parola ile korunan Word belgesinde verilerin nasıl önbelleğe alınacağını gösterilmektedir. Kod, metodun korumasını kaldırmadan önce <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> , geçerli <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> değeri kaydeder, böylece aynı koruma türü yönteme yeniden uygulanabilir <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> .

 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]

### <a name="compile-the-code"></a>Kodu derle
 Bu kodu `ThisDocument` projenizdeki sınıfa ekleyin. Bu kod, parolanın adlı bir alanda depolandığını varsayar `securelyStoredPassword` .

## <a name="cache-in-excel-workbooks"></a>Excel çalışma kitaplarında önbelleğe alma
 Excel projelerinde, bu yordam yalnızca yöntemini kullanarak çalışma kitabının tamamını parolayla koruduğunuzda gereklidir <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> . Yöntemini kullanarak yalnızca belirli bir çalışma sayfasını parolayla koruduğunuzda, bu yordam gerekli değildir <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> .

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Parola ile korunan bir Excel çalışma kitabındaki verileri önbelleğe almak için

1. `ThisWorkbook`Sınıfında veya `Sheet` *n* sınıflarından birinde, önbelleğe alınacak bir ortak alanı veya özelliği işaretleyin. Daha fazla bilgi için bkz. [önbelleği verileri](../vsto/caching-data.md).

2. <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>Sınıftaki yöntemi geçersiz kılın `ThisWorkbook` ve çalışma kitabının korumasını kaldırın.

     Çalışma kitabı kaydedildiğinde, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çalışma kitabının korumasını kaldırma fırsatı vermek için bu yöntemi çağırır. Bu, önbelleğe alınan verilerde yapılan değişikliklerin kaydedilmesini sağlar.

3. <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>Sınıfında yöntemi geçersiz kılın `ThisWorkbook` ve korumayı belgeye yeniden uygulayın.

     Çalışma kitabı kaydedildikten sonra, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çalışma kitabına korumayı yeniden uygulama fırsatı vermek için bu yöntemi çağırır.

### <a name="example"></a>Örnek
 Aşağıdaki kod örneği, bir parola ile korunan bir Excel çalışma kitabında verilerin nasıl önbelleğe alınacağını göstermektedir. Kod, metodun korumasını kaldırmadan önce <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> , geçerli <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> ve <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> değerlerini kaydeder, böylece aynı koruma türü yönteme yeniden uygulanabilir <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> .

 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]

### <a name="compile-the-code"></a>Kodu derle
 Bu kodu `ThisWorkbook` projenizdeki sınıfa ekleyin. Bu kod, parolanın adlı bir alanda depolandığını varsayar `securelyStoredPassword` .

## <a name="see-also"></a>Ayrıca bkz.
- [Önbellek verileri](../vsto/caching-data.md)
- [Nasıl yapılır: çevrimdışı veya sunucuda kullanmak üzere verileri önbelleğe alma](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Nasıl yapılır: bir Office belgesinde program aracılığıyla veri kaynağını önbelleğe alma](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
