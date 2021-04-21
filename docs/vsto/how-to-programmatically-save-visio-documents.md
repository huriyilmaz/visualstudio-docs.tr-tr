---
title: 'Nasıl yapılır: program aracılığıyla Visio belgelerini kaydetme'
description: Visual Studio 'Yu kullanarak Microsoft Visio mevcut belgelerini ve henüz kaydedilmemiş yeni belgeleri program aracılığıyla nasıl kaydedebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 340d813a19c0c0dc5c347d3cfe4c7b29ff1bd049
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107829001"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Nasıl yapılır: program aracılığıyla Visio belgelerini kaydetme
  Microsoft Office Visio belgelerini kaydetmek için çeşitli yollar vardır:

- Mevcut bir belgedeki değişiklikleri kaydedin.

- Yeni bir belge kaydedin veya belgeyi yeni bir adla kaydedin.

- Belirtilen bağımsız değişkenlerle bir belge kaydedin.

  Daha fazla bilgi için,Microsoft.Office.Interop.Visio.Document için VBA başvuru belgelerine bakın [ . Save](/office/vba/api/Visio.Document.Save) yöntemi, [Microsoft.Office.Interop.Visio.Document. SaveAs](/office/vba/api/Visio.Document.SaveAs) yöntemi ve [Microsoft.Office.Interop.Visio.Document. SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx) yöntemi.

## <a name="save-an-existing-document"></a>Mevcut bir belgeyi Kaydet

### <a name="to-save-a-document"></a>Bir belgeyi kaydetmek için

- `Microsoft.Office.Interop.Visio.Document.Save` `Microsoft.Office.Tools.Visio.Document` Daha önce kaydedilmiş bir belge sınıfının yöntemini çağırın.

     Bu kod örneğini kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

    > [!NOTE]
    > `Microsoft.Office.Interop.Visio.Document.Save`Yeni bir Visio belgesi henüz kaydedilmediyse Yöntem bir özel durum oluşturur.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet11":::

## <a name="save-a-document-with-a-new-name"></a>Belgeyi yeni bir adla kaydetme
 Yeni bir `Microsoft.Office.Interop.Visio.Document.SaveAs` belgeyi veya yeni bir ada sahip bir belgeyi kaydetmek için yöntemini kullanın. Bu yöntem, yeni dosya adını belirtmenizi gerektirir.

### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Etkin Visio belgesini yeni bir adla kaydetmek için

- `Microsoft.Office.Interop.Visio.Document.SaveAs` `Microsoft.Office.Tools.Visio.Document` Bir dosya adı da dahil olmak üzere tam olarak nitelenmiş bir yol kullanarak kaydetmek istediğiniz yöntemini çağırın. Bu adda bir dosya zaten varsa, bu klasörde sessizce üzerine yazılır.

     Bu kod örneğini kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet10":::

## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Belgeyi yeni bir adla ve belirtilen bağımsız değişkenlerle Kaydet
 Yeni bir `Microsoft.Office.Interop.Visio.Document.SaveAsEx` ada sahip bir belgeyi kaydetmek ve belgeye uygulanacak uygun bağımsız değişkenleri belirtmek için yöntemini kullanın.

### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Belgeyi yeni bir adla ve belirtilen bağımsız değişkenlerle kaydetmek için

- `Microsoft.Office.Interop.Visio.Document.SaveAsEx` `Microsoft.Office.Tools.Visio.Document` Bir dosya adı da dahil olmak üzere tam olarak nitelenmiş bir yol kullanarak kaydetmek istediğiniz yöntemini çağırın. Bu klasörde bu ada sahip bir dosya zaten varsa, bir özel durum oluşturulur.

     Aşağıdaki kod örneği, etkin belgeyi yeni bir adla kaydeder, belgeyi salt okunurdur olarak işaretler ve belgeyi en son kullanılan belge listesinde gösterir. Bu kod örneğini kullanmak için `ThisAddIn` projenizdeki sınıftan çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet12":::

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği şunları gerektirir:

- Yeni bir ada sahip bir belgeyi kaydetmek için, adlı bir dizin Belgelerim `Test` klasöründe (WINDOWS XP ve  önceki sürümler Için) veya *Belgeler* klasöründe (Windows Vista için) bulunmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Nasıl yapılır: program aracılığıyla yeni Visio belgeleri oluşturma](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini açma](../vsto/how-to-programmatically-open-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini kapatma](../vsto/how-to-programmatically-close-visio-documents.md)
- [Nasıl yapılır: program aracılığıyla Visio belgelerini yazdırma](../vsto/how-to-programmatically-print-visio-documents.md)
