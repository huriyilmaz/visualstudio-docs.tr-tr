---
title: Çözümlerde Office bağlama
description: Uygulama içinde nesne modellerinde bulunan bazı türlerin Microsoft Office bağlama özellikleriyle kullanılabilen işlevleri nasıl sağladığını öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0a68aafed5cc4bb42ba9b8d1c4b05d4167e32f68
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032621"
---
# <a name="late-binding-in-office-solutions"></a>Çözümlerde Office bağlama
  Office uygulamalarının nesne modellerinde bulunan bazı türler, geç bağlama özellikleriyle kullanılabilen işlevler sağlar. Örneğin, bazı yöntemler ve özellikler uygulamanın bağlamına bağlı olarak farklı nesne Office ve bazı türler farklı bağlamlarda farklı yöntemleri veya özellikleri ortaya çıkarabilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual Basic **Katı** seçeneğinin kapalı olduğu ve veya hedefini hedef alan Visual C# projelerinin doğrudan bu geç bağlama özelliklerini uygulayan [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] türlerle çalışa bir projedir.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Nesne dönüş değerlerinin örtülü ve açık olarak atması
 Birincil birlikte çalışma derlemeleri (PIA) Microsoft Office birçok yöntem ve özellik, birkaç farklı nesne türü getireyene kadar <xref:System.Object> değerlere sahiptir. Örneğin, etkin sayfa ne olduğu bağlı olarak dönüş değeri bir veya nesnesi olduğundan <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> <xref:System.Object> özelliği bir <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Chart> döndürür.

 Bir yöntem veya özellik döndürecek olduğunda, nesne açıkça (Visual Basic), Option Strict'nin açık olduğu Visual Basic projelerinde doğru <xref:System.Object> türe dönüştürmeniz  gerekir. Option Strict'nin kapalı olduğu tüm <xref:System.Object> projelerde Visual Basic **açıkça değerlerin dökümlerini yapmak** zorunda değildir.

 Çoğu durumda başvuru belgeleri, bir döndüren üye için dönüş değerinin olası türlerini <xref:System.Object> listeler. Nesnesini dönüştürmek veya dönüştürmek, Kod Düzenleyicisi'nde nesnesi için IntelliSense'i sağlar.

 'de dönüştürme hakkında bilgi Visual Basic [](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) için bkz. CType işlevi &#40;Visual Basic&#41;ve [açık dönüştürmeler &#40;Visual Basic&#41;. ](/dotnet/visual-basic/language-reference/functions/ctype-function)

### <a name="examples"></a>Örnekler
 Aşağıdaki kod örneği, Bir nesneyi Option Strict'nin açık olduğu bir Visual Basic türüne nasıl **attırabilirsiniz?** Bu tür bir projede, özelliğini açıkça bir <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> türüne atması <xref:Microsoft.Office.Interop.Excel.Range> gerekir. Bu örnek, adlı bir çalışma Excel belge düzeyi bir proje `Sheet1` gerektirir.

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet9":::

 Aşağıdaki kod örneği, Bir nesneyi, **Option Strict'nin** kapalı olduğu bir Visual Basic projesinde veya hedefini hedef alan bir Visual C# projesinde örtülü olarak belirli bir türe nasıl türe göre [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] gösterebilirsiniz. Bu tür <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> projelerde, özelliği örtülü olarak bir 'ye türe türetir. <xref:Microsoft.Office.Interop.Excel.Range> Bu örnek, adlı bir çalışma Excel belge düzeyi bir proje `Sheet1` gerektirir.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet10":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="access-members-that-are-available-only-through-late-binding"></a>Yalnızca geç bağlama aracılığıyla kullanılabilen üyelere erişme
 Farklı PIA'lar Office bazı özellikler ve yöntemler yalnızca geç bağlama aracılığıyla kullanılabilir. Option **Strict** Visual Basic veya veya hedefini kullanan Visual C# projelerinde yer alan tüm projelerde, geç bağlanmış üyelere erişmek için bu dillerdeki geç bağlama [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] özelliklerini [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] kullanabilirsiniz. Option Visual Basic'nin **açık** olduğu projelerde, bu üyelere erişmek için yansımayı kullansanız gerekir.

### <a name="examples"></a>Örnekler
 Aşağıdaki kod örneği, Option Strict'nin kapalı olduğu bir Visual Basic **veya** hedefini hedef alan bir Visual C# projesinde bir Visual Basic geç bağlı üyelere nasıl erişilenleri [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] gösteriyor. Bu örnek, Word'de Dosya Aç **iletişim** kutusunun **geç bağlanmış Name** özelliğine erişmektedir. Bu örneği kullanmak için word projesinde `ThisDocument` or `ThisAddIn` sınıfından çalıştırın.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 Aşağıdaki kod örneği, Option Strict'nin açık olduğu bir Visual Basic yansıtmayı kullanarak aynı görevi **gerçekleştirmeyi** gösterir.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## <a name="see-also"></a>Ayrıca bkz.
- [Kod yazma Office yazma](../vsto/writing-code-in-office-solutions.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [C programlama kılavuzu &#40;C&#35; Tür dinamik&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Option Strict deyimi](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Yansıma (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Yansıma (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
