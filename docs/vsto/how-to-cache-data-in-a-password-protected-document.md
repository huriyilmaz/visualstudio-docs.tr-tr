---
title: 'Nasıl kullanılır: Parola korumalı bir belgede verileri önbelleğe ekleme'
description: Parolayla korunan bir belge veya çalışma kitabındaki veri önbelleğine veri eklerseniz, projenizin iki yöntemini geçersiz karak önbelleğe alınan verilerde yapılan değişiklikleri kaydedebilirsiniz.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 4f2db608c826dd4b589ea2ed1f53bd504f209369
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100107"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Nasıl kullanılır: Parola korumalı bir belgede verileri önbelleğe ekleme
  Parolayla korunan bir belge veya çalışma kitabındaki veri önbelleğine veri eklerseniz, önbelleğe alınan verilerde yapılan değişiklikler otomatik olarak kaydedlanmaz. Projenizin iki yöntemini geçersiz karak önbelleğe alınan verilerde yapılan değişiklikleri kaydedebilirsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Önbelleğe Alma Word belgelerde kullanma

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Parolayla korunan bir Word belgesinde verileri önbelleğe alan

1. sınıfında, `ThisDocument` önbelleğe alınarak ortak bir alanı veya özelliği işaretle. Daha fazla bilgi için [bkz. Verileri önbelleğe alın.](../vsto/caching-data.md)

2. sınıfında yöntemini <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> geçersiz kılın `ThisDocument` ve belgeden korumayı kaldırın.

     Belge kaydedilirken, size belgenin korumasını geri alıma fırsatı [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vermek için bu yöntemi arar. Bu, önbelleğe alınan verilerde yapılan değişikliklerin kaydedilebilir.

3. sınıfında <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> yöntemini geçersiz kılın `ThisDocument` ve belgeye korumayı yeniden kullanın.

     Belge kaydedildikten sonra, size belgeye yeniden koruma [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] uygulama fırsatı vermek için bu yöntemi arar.

### <a name="example"></a>Örnek
 Aşağıdaki kod örneği, parolayla korunan bir Word belgesinde verileri önbelleğe nasıl alasınız? Kod yönteminde korumayı kaldırmadan önce geçerli değeri kaydeder, böylece yöntemde aynı koruma türü <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> yeniden geçerli <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> olabilir.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb" id="Snippet1":::

### <a name="compile-the-code"></a>Kodu derleme
 Bu kodu projenizin `ThisDocument` sınıfına ekleyin. Bu kod, parolanın adlı bir alanda depolandığı `securelyStoredPassword` varsayıyor.

## <a name="cache-in-excel-workbooks"></a>Çalışma kitaplarında Excel önbellek
 Bu Excel, bu yordam yalnızca yöntemini kullanarak çalışma kitabının tamamını parolayla korurken <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> gereklidir. yöntemini kullanarak yalnızca belirli bir çalışma sayfasını parolayla koruyorsanız bu yordam <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> gerekli değildir.

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Parola ile korunan Excel çalışma kitabındaki verileri önbelleğe alan

1. sınıfında `ThisWorkbook` veya n sınıftan `Sheet`  biri, önbelleğe alınarak ortak bir alanı veya özelliği işaretle. Daha fazla bilgi için [bkz. Verileri önbelleğe alın.](../vsto/caching-data.md)

2. sınıfında yöntemini <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> geçersiz kılın ve çalışma `ThisWorkbook` kitabından korumayı kaldırın.

     Çalışma kitabı kaydedilirken, çalışma [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] kitabının korumasını kaldırma fırsatı vermek için bu yöntemi kullanır. Bu, önbelleğe alınan verilerde yapılan değişikliklerin kaydedilebilir.

3. sınıfında <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> yöntemini geçersiz kılın `ThisWorkbook` ve belgeye korumayı yeniden kullanın.

     Çalışma kitabı kaydedildikten sonra bu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yöntemi çağırarak çalışma kitabına yeniden koruma uygulama fırsatı sağlar.

### <a name="example"></a>Örnek
 Aşağıdaki kod örneği, parolayla korunan bir Excel çalışma kitabındaki verilerin nasıl önbelleğe alınarak önbelleğe alınarak alına bir örnektir. Kod yönteminde korumayı kaldırmadan önce, yönteminde aynı koruma türünün yeniden geçerli ve değerlerini kaydedecek şekilde <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> kaydeder.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs" id="Snippet1":::

### <a name="compile-the-code"></a>Kodu derleme
 Bu kodu projenizin `ThisWorkbook` sınıfına ekleyin. Bu kod, parolanın adlı bir alanda depolandığı `securelyStoredPassword` varsayıyor.

## <a name="see-also"></a>Ayrıca bkz.
- [Önbellek verileri](../vsto/caching-data.md)
- [Nasıl kullanılır: Verileri çevrimdışı veya sunucuda kullanmak üzere önbelleğe alın](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Nasıl kullanılır: Bir veri kaynağını program aracılığıyla bir veri Office önbelleğe ekleme](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
