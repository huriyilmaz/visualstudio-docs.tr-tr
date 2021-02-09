---
title: Office çözümlerinde geç bağlama
description: Microsoft Office uygulamalar içindeki nesne modellerindeki bazı türlerin, geç bağlama özellikleri aracılığıyla kullanılabilen işlevselliği nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 455816b2e23a25ad5ef83c726b2a78e4245ed99a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927658"
---
# <a name="late-binding-in-office-solutions"></a>Office çözümlerinde geç bağlama
  Office uygulamalarının nesne modellerindeki bazı türler, geç bağlama özellikleri aracılığıyla kullanılabilen işlevselliği sağlar. Örneğin, bazı yöntemler ve özellikler Office uygulamasının bağlamına bağlı olarak farklı nesne türleri döndürebilir ve bazı türler farklı bağlamlarda farklı yöntemler veya özellikler sunabilir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 **Option Strict** 'in kapalı olduğu ve veya ' i hedefleyen Visual C# projelerinin, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] Bu geç bağlama özelliklerini kullanan türlerle doğrudan çalıştığı projeler Visual Basic.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Nesne dönüş değerlerini örtük ve açık olarak dönüştürme
 Microsoft Office birincil birlikte çalışma derlemelerindeki (PIA 'lar) birçok yöntem ve özellik <xref:System.Object> , birden çok farklı nesne türleri döndürebildiğinden değerler döndürür. Örneğin, özelliği, <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> <xref:System.Object> <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Chart> etkin sayfanın ne olduğuna bağlı olarak dönüş değeri bir veya nesne olabilir.

 Bir yöntem veya özellik bir döndürdüğünde <xref:System.Object> , nesneyi açık olarak **Option** Visual Basic projelerinde doğru türe (Visual Basic) açıkça dönüştürmeniz gerekir. <xref:System.Object> **Seçenek Strict** kapalı olduğunda Visual Basic projelerinde dönüş değerlerini açıkça dönüştürmek zorunda değilsiniz.

 Çoğu durumda, başvuru belgeleri, döndüren bir üye için dönüş değeri olası türlerini listeler <xref:System.Object> . Nesne dönüştürme veya atama, kod düzenleyicideki nesne için IntelliSense 'i etkinleştirilir.

 Visual Basic dönüştürme hakkında daha fazla bilgi için bkz. [örtük ve açık dönüştürmeler &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) ve [ctype işlevi &#40;](/dotnet/visual-basic/language-reference/functions/ctype-function)Visual Basic&#41;.

### <a name="examples"></a>Örnekler
 Aşağıdaki kod örneği, **seçeneğinin Strict** açık olduğu Visual Basic bir projede belirli bir türe nasıl bir nesne ekleneceğini gösterir. Bu tür projede, <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> özelliği açıkça bir öğesine atamalısınız <xref:Microsoft.Office.Interop.Excel.Range> . Bu örnek, adlı bir çalışma sayfası sınıfı olan belge düzeyi Excel projesi gerektirir `Sheet1` .

 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]

 Aşağıdaki kod **örneği, bir** nesneyi örtük bir şekilde bir Visual Basic projesindeki belirli bir türe veya öğesini hedefleyen bir Visual C# projesinde dolaylı bir şekilde dönüştürmeyi gösterir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Bu tür projelerde, <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> özelliği örtülü olarak bir olarak bir olarak ayarlanır <xref:Microsoft.Office.Interop.Excel.Range> . Bu örnek, adlı bir çalışma sayfası sınıfı olan belge düzeyi Excel projesi gerektirir `Sheet1` .

 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]

## <a name="access-members-that-are-available-only-through-late-binding"></a>Yalnızca geç bağlama aracılığıyla kullanılabilen üyelere erişin
 Office PIA 'leri içindeki bazı özellikler ve yöntemler yalnızca geç bağlama aracılığıyla kullanılabilir. **Option Strict** 'in kapalı olduğu veya veya ' i hedefleyen Visual C# projelerindeki Visual Basic projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , geç bağlanan üyelere erişmek için bu dillerdeki geç bağlama özelliklerini kullanabilirsiniz. **Option Strict** açık olan Visual Basic projelerinde, bu üyelere erişmek için yansıma kullanmanız gerekir.

### <a name="examples"></a>Örnekler
 Aşağıdaki kod örneği, **Option Strict** 'in kapalı olduğu bir Visual Basic projesindeki veya ' i hedefleyen bir Visual C# projesinde, geç bağlanan üyelere nasıl erişebileceğinizi gösterir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Bu örnek, Word 'de **Dosya Aç** iletişim kutusunun geç bağlantılı **ad** özelliğine erişir. Bu örneği kullanmak için, `ThisDocument` `ThisAddIn` bir Word projesindeki veya sınıfından çalıştırın.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 Aşağıdaki kod örneği, **seçeneğinin katı** olan bir Visual Basic projesinde aynı görevi gerçekleştirmek için yansıma kullanımını gösterir.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Tür dinamik &#40;C&#35; programlama kılavuzunu kullanın&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Option Strict ekstresi](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Yansıma (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Yansıma (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
