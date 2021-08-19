---
title: Belgeleri ve belgelerin bölümlerini program aracılığıyla koruma
description: Kullanıcıların belgede herhangi bir düzenleme Microsoft Word için bu belgelere nasıl koruma ekleyebilirsiniz?
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
ms.openlocfilehash: 65d869fa7ff797e0144f08e7f15e822ba1c7f25d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046457"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Nasıl kullanılır: Belgeleri ve belgelerin parçalarını program aracılığıyla koruma
  Kullanıcıların belgede herhangi bir Microsoft Office yapmalarını önlemek için Word belgelerine koruma ekleyebilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Ayrıca, belirtilen kullanıcıların belgenin yalnızca bu alanlarını düzenlemesi için belgenin belirli alanlarını özel durum olarak işaretlebilirsiniz. Örneğin, belirli bir yer işareti dışında belgenin tamamını korumak isteyebilirsiniz. İsteğe bağlı olarak, kullanıcıların parolayı bilmiyor olmadıkça belge korumasını kaldıramalarını için bir parola ekleyebilirsiniz.

> [!NOTE]
> Aşağıdaki örnekte parola koruması kullanmaz; ancak, belge koruması eklerken parola kullanmayı göz önünde bulundurabilirsiniz. Daha fazla bilgi için, geliştirme örnekleri ve [izlenecek yollar Office Belge Koruyucusu Örneği'ne bakın.](../vsto/office-development-samples-and-walkthroughs.md)

 Belgelerin bölümlerini korumak için içerik denetimlerini de kullanabilirsiniz. Daha fazla bilgi için, [bkz. How to: Protect parts of documents by using content controls](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>Belge düzeyinde özelleştirmenin parçası olan bir belgeyi koruma

### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Belge düzeyinde özelleştirmenin parçası olan bir belgeyi korumak için

1. Projeniz <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> içinde `ThisDocument` sınıfının yöntemini çağırma.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet111":::

### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Yer işareti denetimlerini belge korumasının dışında tutmak için

1. yöntemini kullanarak belgenin tamamını <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> koruyun.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet111":::

2. Belge `Bookmark1` korumasının dışında tutul.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet112":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet112":::

### <a name="compile-the-code"></a>Kodu derleme
 Bu kod örneklerini kullanmak için projenizin `ThisDocument` sınıfından çalıştırın. Bu kod örnekleri, bu kodun <xref:Microsoft.Office.Tools.Word.Bookmark> göründüğü belgede adlı bir `Bookmark1` denetiminiz olduğunu varsayabilir.

## <a name="protect-a-document-by-using-a-vsto-add-in"></a>VSTO Eklenti kullanarak belgeyi koruma

### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Bir belgeyi uygulama düzeyinde bir eklenti kullanarak VSTO için

1. Korumak <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> istediğiniz <xref:Microsoft.Office.Interop.Word.Document> yöntemini çağırma.

     Aşağıdaki kod örneği etkin belgeyi korur. Bu kod örneğini kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet111":::

## <a name="see-also"></a>Ayrıca bkz.
- [Belge düzeyi çözümlerde belge koruması](../vsto/document-protection-in-document-level-solutions.md)
- [Office belgelerde parola koruması](../vsto/password-protection-on-office-documents.md)
- [Nasıl kullanılır: Kodun kısıtlı izinlerle belgelerin arkasında çalışmasına izin verme](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Nasıl kullanılır: Word belgelerine Yer İşareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
