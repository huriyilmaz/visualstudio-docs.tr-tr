---
title: Program aracılığıyla Office veri kaynağını önbelleğe alın
description: Bir konak öğesinin StartCaching yöntemini çağırarak program aracılığıyla bir veri nesnesini bir belgede veri önbelleğine nasıl ekleyebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2737cd7ff10ffff4623fa50a2382d8887293b6ab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148096"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Nasıl kullanılır: Bir veri kaynağını program aracılığıyla bir veri Office önbelleğe ekleme
  , veya gibi bir konak öğesinin yöntemini çağırarak program aracılığıyla bir veri nesnesini bir belgede `StartCaching` veri önbelleğine <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Excel.Workbook> <xref:Microsoft.Office.Tools.Excel.Worksheet> ekleyebilirsiniz. Bir konak öğesinin yöntemini çağırarak veri `StopCaching` önbelleğinden bir veri nesnesini kaldırın.

 hem `StartCaching` yöntemi hem de yöntemi `StopCaching` özeldir, ancak IntelliSense'te görünür.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Veri `StartCaching` önbelleğine bir veri nesnesi eklemek için yöntemini kullanırken, veri nesnesinin özniteliğiyle bildirilene gerek <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> olmaz. Ancak, veri nesnesinin veri önbelleğine eklenmek üzere belirli gereksinimleri karşılaması gerekir. Daha fazla bilgi için [bkz. Verileri önbelleğe alın.](../vsto/caching-data.md)

## <a name="to-programmatically-cache-a-data-object"></a>Program aracılığıyla bir veri nesnesini önbelleğe etmek için

1. Veri nesnesini bir yöntemin içinde değil sınıf düzeyinde bildirin. Bu örnekte, program aracılığıyla önbelleğe almak istediğiniz <xref:System.Data.DataSet> `dataSet1` adlı bir bildirimde bulundurarak varsayabilirsiniz.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet12":::

2. Veri nesnesinin örneğini oluşturun, sonra belge veya çalışma sayfası örneğinin yöntemini `StartCaching` çağırarak veri nesnesinin adını iletin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet13":::

## <a name="to-stop-caching-a-data-object"></a>Veri nesnesini önbelleğe almayı durdurmak için

1. Belge `StopCaching` veya çalışma sayfası örneğinin yöntemini çağırarak veri nesnesinin adını girin. Bu örnekte, önbelleğe almayı durdurmak <xref:System.Data.DataSet> istediğiniz adlı bir adlı bir olduğunu `dataSet1` varsayır.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet14":::

    > [!NOTE]
    > Bir belge veya `StopCaching` çalışma sayfası olayı için olay `Shutdown` işleyiciden çağrısı yapma. Olay `Shutdown` 2014'e kadar, veri önbelleğini değiştirmek için çok geç. Olay hakkında daha fazla `Shutdown` bilgi için [bkz. Office Projelerinde Olaylar.](../vsto/events-in-office-projects.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Önbellek verileri](../vsto/caching-data.md)
- [Nasıl kullanılır: Verileri çevrimdışı veya sunucuda kullanmak üzere önbelleğe alın](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Nasıl kullanılır: Parola korumalı bir belgede verileri önbelleğe ekleme](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Sunucu belgelerde verilere erişme](../vsto/accessing-data-in-documents-on-the-server.md)
- [Verileri kaydetme](../data-tools/save-data-back-to-the-database.md)
