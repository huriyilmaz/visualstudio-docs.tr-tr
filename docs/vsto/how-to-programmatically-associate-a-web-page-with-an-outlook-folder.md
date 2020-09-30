---
title: Bir Web sayfasını Outlook klasörüyle ilişkilendirme
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 35eb2dc3b1b595a4bf960af67ac5006cd9839c6e
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585346"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Bir Web sayfasını Outlook klasörüyle ilişkilendirme

  Bu örnek Outlook Microsoft Office adında bir klasör olup olmadığını denetler `HtmlView` . Klasör yoksa, kod klasörü oluşturur ve ona bir Web sayfası atar. Klasör varsa, kod klasör içeriğini görüntüler.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.
- [Klasörlerle çalışma](../vsto/working-with-folders.md)
- [Nasıl yapılır: program aracılığıyla bir klasörü ada göre alma](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Nasıl yapılır: program aracılığıyla özel klasör öğeleri oluşturma](../vsto/how-to-programmatically-create-custom-folder-items.md)
