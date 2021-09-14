---
title: bir web sayfasını Outlook klasörüyle ilişkilendir
description: bir web sayfasını Microsoft Office Outlook klasörüyle nasıl ilişkilendirebileceğinizi öğrenin. Bu örnek, Outlook içinde HtmlView adlı bir klasör olup olmadığını denetler.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5a24e2ca3942d2c122421151a3f9a96b640b2ebb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633993"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>bir web sayfasını Outlook klasörüyle ilişkilendir

  Bu örnek, Microsoft Office Outlook adlı bir klasörü denetler `HtmlView` . Klasör yoksa, kod klasörü oluşturur ve ona bir Web sayfası atar. Klasör varsa, kod klasör içeriğini görüntüler.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Ayrıca bkz.
- [Klasörlerle çalışma](../vsto/working-with-folders.md)
- [Nasıl yapılır: program aracılığıyla bir klasörü ada göre alma](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Nasıl yapılır: program aracılığıyla özel klasör öğeleri oluşturma](../vsto/how-to-programmatically-create-custom-folder-items.md)
