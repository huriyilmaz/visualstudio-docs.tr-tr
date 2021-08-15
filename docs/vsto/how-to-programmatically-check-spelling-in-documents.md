---
title: 'Nasıl kullanılır: Belgelerde program aracılığıyla yazım denetimi yapma'
description: Program aracılığıyla bir belgede yazım denetimi yapmak için CheckSpelling yöntemini kullanabileceğiniz hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a2f03c61a1d35e9c66e1e660a3d2fdb56c2bac9ba6f25cd41cd795d2f172ee51
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121268085"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Nasıl kullanılır: Belgelerde program aracılığıyla yazım denetimi yapma
  Belgede yazım denetimi yapmak için yöntemini <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> kullanın. Bu yöntem, sağlanan parametrenin doğru yaz olup olmadığını belirten bir Boole değeri döndürür.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Bir ileti kutusunda yazım denetimi yapmak ve sonuçları görüntülemek için

1. yöntemini <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> çağırma ve yazım hatalarını denetlemesi için bir metin aralığı iletir. Bu kod örneğini kullanmak için projenizin `ThisDocument` or `ThisAddIn` sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet113":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet113":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
