---
title: Office çözümlerinde isteğe bağlı parametreler
description: Varsayılan değerler her eksik parametre için otomatik olarak kullanıldığından, isteğe bağlı parametreler için değer geçmenin nasıl gerek olmadığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ab02913bb165f6f3ca7c240a27ee838fa5cf8e3b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633830"
---
# <a name="optional-parameters-in-office-solutions"></a>Office çözümlerinde isteğe bağlı parametreler
  Microsoft Office uygulamalarının nesne modellerinde kullanılan yöntemlerin çoğu isteğe bağlı parametreleri kabul eder. Visual Studio'de Visual Basic çözüm geliştirmek için Office kullanırsanız, varsayılan değerler her eksik parametre için otomatik olarak kullanıldığından isteğe bağlı parametreler için bir değer geçmeniz gerekli değildir. Çoğu durumda, Visual C# projelerinde isteğe bağlı parametreleri de atlarsiniz. Ancak, belge düzeyi Word **projelerinde sınıfının** isteğe bağlı `ThisDocument` başvuru parametrelerini atamazsınız.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual C# ve Visual Basic projelerinde isteğe bağlı parametrelerle çalışma hakkında daha fazla bilgi için bkz. C &#40;[C&#35;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) programlama kılavuzunda adlandırılmış ve isteğe bağlı bağımsız değişkenler&#41;ve &#40;Visual Basic&#41;. [ ](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)

> [!NOTE]
> Önceki visual Visual Studio Visual C# projelerinde isteğe bağlı her parametre için bir değer geçmelisiniz. Kolaylık olması için bu projeler, parametresinin varsayılan değerini kullanmak istediğiniz zaman isteğe bağlı bir parametreye geçilen adlı `missing` genel bir değişken içerir. Visual Studio'de Office için Visual C# projeleri hala değişkenlerini içerir, ancak Word için belge düzeyi projelerde sınıfında isteğe bağlı başvuru parametrelerine sahip yöntemleri çağırma dışında, genellikle içinde Office çözümleri geliştirirken bunu kullanmak zorunda `missing` [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]  `ThisDocument` olmazsınız.

## <a name="example-in-excel"></a>Excel'de örnek
 Yöntemin <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> birçok isteğe bağlı parametresi vardır. Bazı parametreler için değerler belirtebilirsiniz ve aşağıdaki kod örneğinde gösterildiği gibi diğerlerinin varsayılan değerini kabul edersiniz. Bu örnek, adlı çalışma sayfası sınıfına sahip bir belge düzeyi proje `Sheet1` gerektirir.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb" id="Snippet1":::

## <a name="example-in-word"></a>Word'de örnek
 Yöntemin <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> birçok isteğe bağlı parametresi vardır. Bazı parametreler için değerler belirtebilirsiniz ve aşağıdaki kod örneğinde gösterildiği gibi diğerlerinin varsayılan değerini kabul edersiniz.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet1":::

## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Word için Visual C# belge düzeyi projelerinde ThisDocument sınıfındaki yöntemlerin isteğe bağlı parametrelerini kullanma
 Word nesne modeli, değerleri kabul eden isteğe bağlı **başvuru parametrelerine** sahip birçok yöntem <xref:System.Object> içerir. Ancak Word için Visual C# **belge** düzeyi projelerinde oluşturulan sınıfın yöntemlerinin isteğe `ThisDocument` bağlı başvuru parametrelerini atamazsınız. Visual C#, isteğe bağlı **başvuru parametrelerini** sınıf değil yalnızca arabirim yöntemleri için atlar. Örneğin, sınıfının yönteminin isteğe bağlı başvuru parametrelerini  atlayamayabilirsiniz, çünkü aşağıdaki kod <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> örneği `ThisDocument` derlanmaz.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet3":::

 sınıfının yöntemlerini çağırarak `ThisDocument` şu yönergeleri izleyin:

- İsteğe bağlı başvuru parametresinin varsayılan **değerini kabul** etmek için `missing` değişkeni parametresine iletir. değişkeni, Visual C# Office otomatik olarak tanımlanır ve oluşturulan `missing` proje <xref:System.Type.Missing> kodundaki değere atanır.

- İsteğe bağlı bir **başvuru** parametresi için kendi değerinizi belirtmek için, belirtmek istediğiniz değere atanmış bir nesne belirtin ve ardından nesneyi parametresine iletir.

  Aşağıdaki kod örneğinde ignoreUppercase parametresi için bir değer belirterek ve diğer parametreler için varsayılan değeri kabul etme yöntemi nasıl <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> çağrılabilir? 

  :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet4":::

  sınıfındaki bir yöntemin isteğe bağlı **başvuru** parametrelerini atlayarak kod yazmak için, alternatif olarak özelliği tarafından döndürülen nesnede aynı yöntemi çağırabilir ve bu yöntemden parametreleri `ThisDocument` <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> atabilirsiniz. Bunu, sınıf yerine <xref:Microsoft.Office.Interop.Word.Document> bir arabirim olduğu için bunu yapabiliriz.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet5":::

  Değer ve başvuru türü parametreleri hakkında daha fazla bilgi için bkz. Bağımsız değişkenleri değere ve başvuru değerlerine göre [&#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (Visual Basic için) ve Parametre geçişi [&#40;C&#35; programlama kılavuzu&#41;. ](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni Office geliştirme](../vsto/developing-office-solutions.md)
- [Kod yazma Office yazma](../vsto/writing-code-in-office-solutions.md)
