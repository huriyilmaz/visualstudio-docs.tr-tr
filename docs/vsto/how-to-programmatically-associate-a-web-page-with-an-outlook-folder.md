---
title: Bir Web sayfasını Outlook klasörüyle ilişkilendirme
description: Bir Web sayfasını Microsoft Office Outlook klasörüyle nasıl ilişkilendirebileceğinizi öğrenin. Bu örnek Outlook 'ta HtmlView adlı bir klasör olup olmadığını denetler.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3f022deca9b8cd1b8f00bf847ab0bfdc7882a45f
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828273"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Bir Web sayfasını Outlook klasörüyle ilişkilendirme

  Bu örnek Outlook Microsoft Office adında bir klasör olup olmadığını denetler `HtmlView` . Klasör yoksa, kod klasörü oluşturur ve ona bir Web sayfası atar. Klasör varsa, kod klasör içeriğini görüntüler.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Ayrıca bkz.
- [Klasörlerle çalışma](../vsto/working-with-folders.md)
- [Nasıl yapılır: program aracılığıyla bir klasörü ada göre alma](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Nasıl yapılır: program aracılığıyla özel klasör öğeleri oluşturma](../vsto/how-to-programmatically-create-custom-folder-items.md)
