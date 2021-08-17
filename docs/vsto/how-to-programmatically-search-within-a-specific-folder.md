---
title: 'Nasıl yapılanlar: Belirli bir klasör içinde program aracılığıyla arama'
description: Belirli bir Microsoft Visual Studio klasöründe program aracılığıyla arama yapmak için Outlook öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 35c54fff165f06af2bd1943682dc3ad21babc410
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099730"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Nasıl yapılanlar: Belirli bir klasör içinde program aracılığıyla arama
  Bu kod örneği, gelen kutusunda yer alan e-posta iletilerinin konu alanında metin aramak `Find` için ve `FindNext` yöntemlerini **kullanır.** Bu yöntem, T harfinin metnin başlangıç harfi olarak kontrol etmek için bir dize filtresi `Subject` kullanır.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Ayrıca bkz.
- [Klasörlerle çalışma](../vsto/working-with-folders.md)
- [Outlook modeline genel bakış](../vsto/outlook-object-model-overview.md)
- [Nasıl yapılanlar: Program aracılığıyla klasör adı ile alma](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
