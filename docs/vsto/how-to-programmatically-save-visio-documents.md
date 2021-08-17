---
title: 'Nasıl kullanılır: Program aracılığıyla Visio kaydetme'
description: Microsoft'u program Visual Studio ve henüz Visio belgeleri ve yeni belgeleri kaydetmek için Visio nasıl kullanabileceğinizi öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 676281c289d565e4e8ffc07e68c6ced0199b10d0c3f5270e60b43fea222de025
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351687"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Nasıl kullanılır: Program aracılığıyla Visio kaydetme
  Bu belgeleri kaydetmenin çeşitli Microsoft Office Visio vardır:

- Değişiklikleri mevcut bir belgeye kaydedin.

- Yeni bir belge kaydedin veya yeni bir adla bir belgeyi kaydedin.

- Belirtilen bağımsız değişkenlerle bir belgeyi kaydedin.

  Daha fazla bilgi için,Microsoft.Office.Interop.Visio.Document için VBA [ başvuru belgelerine bakın. Save](/office/vba/api/Visio.Document.Save) method, [Microsoft.Office.Interop.Visio.Document. SaveAs](/office/vba/api/Visio.Document.SaveAs) yöntemi ve [Microsoft.Office.Interop.Visio.Doc. SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx) yöntemi.

## <a name="save-an-existing-document"></a>Mevcut bir belgeyi kaydetme

### <a name="to-save-a-document"></a>Belgeyi kaydetmek için

- Daha `Microsoft.Office.Interop.Visio.Document.Save` önce kaydedilmiş `Microsoft.Office.Tools.Visio.Document` bir belgenin sınıfının yöntemini çağırma.

     Bu kod örneğini kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

    > [!NOTE]
    > yöntemi, `Microsoft.Office.Interop.Visio.Document.Save` yeni bir belge Visio henüz kaydedilene bir özel durum oluşturur.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet11":::

## <a name="save-a-document-with-a-new-name"></a>Yeni bir adla belge kaydetme
 Yeni `Microsoft.Office.Interop.Visio.Document.SaveAs` bir belgeyi veya yeni adı olan bir belgeyi kaydetmek için yöntemini kullanın. Bu yöntem, yeni dosya adını belirtmenizi gerektirir.

### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Etkin çalışma Visio yeni bir adla kaydetmek için

- Bir `Microsoft.Office.Interop.Visio.Document.SaveAs` dosya adı `Microsoft.Office.Tools.Visio.Document` içeren tam yol kullanarak kaydetmek istediğiniz yöntemini çağırabilirsiniz. Bu adla bir dosya bu klasörde zaten varsa, bu dosyanın üzerine sessizce yazılır.

     Bu kod örneğini kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet10":::

## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Yeni bir ad ve belirtilen bağımsız değişkenlerle belgeyi kaydetme
 Yeni `Microsoft.Office.Interop.Visio.Document.SaveAsEx` bir adla belgeyi kaydetmek ve belgeye uygulanacak geçerli bağımsız değişkenleri belirtmek için yöntemini kullanın.

### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Belgeyi yeni bir ad ve belirtilen bağımsız değişkenlerle kaydetmek için

- Bir `Microsoft.Office.Interop.Visio.Document.SaveAsEx` dosya adı `Microsoft.Office.Tools.Visio.Document` içeren tam yol kullanarak kaydetmek istediğiniz yöntemini çağırabilirsiniz. Bu klasörde bu adla bir dosya zaten varsa, bir özel durum oluşturur.

     Aşağıdaki kod örneği etkin belgeyi yeni bir adla kaydeder, belgeyi salt okunur olarak işaretler ve belgeyi En Son Kullanılan belge listesinde gösterir. Bu kod örneğini kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet12":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu kod örneği için aşağıdakiler gerekir:

- Yeni bir adı olan bir belgeyi kaydetmek için, Adlı bir dizinin Belgelerim klasöründe (Windows XP ve önceki sürümler için) veya Belgeler klasöründe `Test` (Windows Vista için)  olması gerekir. 

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Nasıl kullanılır: Program aracılığıyla yeni Visio oluşturma](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Nasıl Visio: Program aracılığıyla Visio açma](../vsto/how-to-programmatically-open-visio-documents.md)
- [Nasıl kullanılır: Program aracılığıyla Visio kapatma](../vsto/how-to-programmatically-close-visio-documents.md)
- [Nasıl kullanılır: Program aracılığıyla Visio yazdırma](../vsto/how-to-programmatically-print-visio-documents.md)
