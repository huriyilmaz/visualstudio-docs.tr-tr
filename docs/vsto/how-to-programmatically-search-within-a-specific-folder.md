---
title: 'Nasıl yapılır: belirli bir klasör içinde program aracılığıyla arama'
description: Visual Studio 'Yu, belirli bir Microsoft Outlook klasörü içinde programlı bir şekilde arama yapmak için nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a9c7861698e678ca6d8332e3940c3ae49ff423f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877882"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Nasıl yapılır: belirli bir klasör içinde program aracılığıyla arama
  Bu kod örneği, `Find` `FindNext` **gelen kutusundaki** e-posta iletilerinin konu alanında metin aramak için ve yöntemlerini kullanır. Bu yöntem, metnin başlangıç harfi olarak T harfini denetlemek için bir dize filtresi kullanır `Subject` .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.
- [Klasörlerle çalışma](../vsto/working-with-folders.md)
- [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)
- [Nasıl yapılır: program aracılığıyla bir klasörü ada göre alma](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
