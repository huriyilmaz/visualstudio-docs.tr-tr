---
title: 'Nasıl musunuz: Program aracılığıyla çalışma kitaplarını açma'
description: Bir çalışma kitabını program aracılığıyla Visual Studio veya mevcut bir çalışma kitabıyla Microsoft Excel bir çalışma kitabını program aracılığıyla açmak için Microsoft Excel nasıl kullanabileceğiniz hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 529b957613ae954d35c2284870d6512c7357ac64
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633918"
---
# <a name="how-to-programmatically-open-workbooks"></a>Nasıl musunuz: Program aracılığıyla çalışma kitaplarını açma
  Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Workbooks> koleksiyon, tüm açık çalışma kitaplarıyla ve çalışma kitaplarını açmayı mümkün yapar.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Mevcut çalışma kitabını açmak için

1. Çalışma <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> kitabının <xref:Microsoft.Office.Interop.Excel.Workbooks> yolunu geçerek koleksiyonun yöntemini kullanın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet2":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu kod örneği için aşağıdakiler gerekir:

- adlı bir çalışma `YourWorkbook.xls` kitabı, C sürücüsünde adlı `Test` bir dizinde mevcut olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma kitaplarıyla çalışma](../vsto/working-with-workbooks.md)
- [Nasıl kullanılır: Program aracılığıyla metin dosyalarını çalışma kitapları olarak açma](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Nasıl musunuz: Program aracılığıyla yeni çalışma kitapları oluşturma](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Nasıl yapılanlar: Program aracılığıyla çalışma kitaplarını kaydetme](../vsto/how-to-programmatically-save-workbooks.md)
- [Nasıl yapılanlar: Program aracılığıyla çalışma kitaplarını kapatma](../vsto/how-to-programmatically-close-workbooks.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
