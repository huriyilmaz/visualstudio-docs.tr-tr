---
title: Belge ve belge parçalarını programlama yoluyla koruma
description: kullanıcıların belgede herhangi bir düzenleme yapmasını engellemek için Microsoft Word belgelerine koruma nasıl ekleyebileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d984fb947a4f782fe2a292dd0f28befc50db2f64234e07ecd542d7c092c098e8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366231"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Nasıl yapılır: program aracılığıyla belgeleri ve belge parçalarını koruma
  kullanıcıların belgede herhangi bir düzenleme yapmasını engellemek için, Microsoft Office Word belgelerine koruma ekleyebilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Ayrıca, belirtilen kullanıcıların yalnızca belgenin bu bölgelerini düzenleyebilmeleri için belgenin belirli bölümlerini özel durumlar olarak işaretleyebilirsiniz. Örneğin, belirli bir yer işareti hariç tüm belgeyi korumak isteyebilirsiniz. Parolayı bilediklerinde kullanıcıların belge korumasını kaldıramaması için isteğe bağlı olarak bir parola ekleyebilirsiniz.

> [!NOTE]
> Aşağıdaki örnek parola korumasını kullanmaz; Ancak, belge koruması eklerken bir parola kullanmayı düşünmek isteyebilirsiniz. daha fazla bilgi için [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)'daki belge koruyucu örneğine bakın.

 Ayrıca, belge parçalarını korumak için içerik denetimlerini de kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: içerik denetimlerini kullanarak belge bölümlerini koruma](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>Belge düzeyinde özelleştirmenin parçası olan bir belgeyi koruma

### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Belge düzeyinde özelleştirmenin parçası olan bir belgeyi korumak için

1. <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> `ThisDocument` Projenizdeki sınıfının yöntemini çağırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet111":::

### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Bir yer işareti denetimini belge korumadan dışlamak için

1. Yöntemini kullanarak tüm belgeyi koruyun <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet111":::

2. `Bookmark1`Belge korumasından hariç tutun.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet112":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet112":::

### <a name="compile-the-code"></a>Kodu derle
 Bu kod örneklerini kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın. Bu kod örnekleri <xref:Microsoft.Office.Tools.Word.Bookmark> `Bookmark1` , bu kodun göründüğü belge üzerinde adında var olan bir denetiminiz olduğunu varsayar.

## <a name="protect-a-document-by-using-a-vsto-add-in"></a>VSTO eklentisi kullanarak bir belgeyi koruma

### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>uygulama düzeyi VSTO eklentisi kullanarak bir belgeyi korumak için

1. Korumak istediğiniz <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> öğesinin yöntemini çağırın <xref:Microsoft.Office.Interop.Word.Document> .

     Aşağıdaki kod örneği etkin belgeyi korur. Bu kod örneğini kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet111":::

## <a name="see-also"></a>Ayrıca bkz.
- [Belge düzeyi çözümlerde Belge koruması](../vsto/document-protection-in-document-level-solutions.md)
- [Office belgelerde parola koruması](../vsto/password-protection-on-office-documents.md)
- [Nasıl yapılır: kodun, kısıtlı izinlerle belgelerin arkasında çalışmasına Izin verme](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Nasıl yapılır: Word belgelerine yer Işareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
