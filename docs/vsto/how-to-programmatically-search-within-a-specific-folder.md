---
title: 'Nasıl yapılır: belirli bir klasör içinde program aracılığıyla arama'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f33b56da08fcd05706ac7681740cea04574d0070
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584748"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Nasıl yapılır: belirli bir klasör içinde program aracılığıyla arama
  Bu kod örneği, `Find` `FindNext` **gelen kutusundaki**e-posta iletilerinin konu alanında metin aramak için ve yöntemlerini kullanır. Bu yöntem, metnin başlangıç harfi olarak T harfini denetlemek için bir dize filtresi kullanır `Subject` .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.
- [Klasörlerle çalışma](../vsto/working-with-folders.md)
- [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)
- [Nasıl yapılır: program aracılığıyla bir klasörü ada göre alma](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
