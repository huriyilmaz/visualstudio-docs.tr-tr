---
title: Belge ve belge parçalarını programlama yoluyla koruma
description: Kullanıcıların belgede herhangi bir düzenleme yapmasını engellemek için Microsoft Word belgelerine nasıl koruma ekleyebileceğiniz hakkında bilgi edinin.
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
ms.workload:
- office
ms.openlocfilehash: a3301abf4807c02e1ed3e330e27c609a721bf48d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946156"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Nasıl yapılır: program aracılığıyla belgeleri ve belge parçalarını koruma
  Kullanıcıların belgede herhangi bir düzenleme yapmasını engellemek için, Microsoft Office Word belgelerine koruma ekleyebilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Ayrıca, belirtilen kullanıcıların yalnızca belgenin bu bölgelerini düzenleyebilmeleri için belgenin belirli bölümlerini özel durumlar olarak işaretleyebilirsiniz. Örneğin, belirli bir yer işareti hariç tüm belgeyi korumak isteyebilirsiniz. Parolayı bilediklerinde kullanıcıların belge korumasını kaldıramaması için isteğe bağlı olarak bir parola ekleyebilirsiniz.

> [!NOTE]
> Aşağıdaki örnek parola korumasını kullanmaz; Ancak, belge koruması eklerken bir parola kullanmayı düşünmek isteyebilirsiniz. Daha fazla bilgi için bkz. [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)hakkında belge koruyucu örneği.

 Ayrıca, belge parçalarını korumak için içerik denetimlerini de kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: içerik denetimlerini kullanarak belge bölümlerini koruma](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>Belge düzeyinde özelleştirmenin parçası olan bir belgeyi koruma

### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Belge düzeyinde özelleştirmenin parçası olan bir belgeyi korumak için

1. <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> `ThisDocument` Projenizdeki sınıfının yöntemini çağırın.

     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]

### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Bir yer işareti denetimini belge korumadan dışlamak için

1. Yöntemini kullanarak tüm belgeyi koruyun <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> .

     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]

2. `Bookmark1`Belge korumasından hariç tutun.

     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]

### <a name="compile-the-code"></a>Kodu derle
 Bu kod örneklerini kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın. Bu kod örnekleri <xref:Microsoft.Office.Tools.Word.Bookmark> `Bookmark1` , bu kodun göründüğü belge üzerinde adında var olan bir denetiminiz olduğunu varsayar.

## <a name="protect-a-document-by-using-a-vsto-add-in"></a>VSTO eklentisini kullanarak bir belgeyi koruma

### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Uygulama düzeyi VSTO eklentisini kullanarak bir belgeyi korumak için

1. Korumak istediğiniz <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> öğesinin yöntemini çağırın <xref:Microsoft.Office.Interop.Word.Document> .

     Aşağıdaki kod örneği etkin belgeyi korur. Bu kod örneğini kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]

## <a name="see-also"></a>Ayrıca bkz.
- [Belge düzeyi çözümlerde Belge koruması](../vsto/document-protection-in-document-level-solutions.md)
- [Office belgelerinde parola koruması](../vsto/password-protection-on-office-documents.md)
- [Nasıl yapılır: kodun, kısıtlı izinlerle belgelerin arkasında çalışmasına Izin verme](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Nasıl yapılır: Word belgelerine yer Işareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
