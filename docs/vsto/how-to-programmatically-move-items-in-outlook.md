---
title: 'Nasıl kullanılır: Öğeleri program aracılığıyla Outlook'
description: Microsoft'ta öğeleri program aracılığıyla nasıl taşıyabilirsiniz Outlook. Bu örnek okunmamış e-posta iletilerini Gelen Kutusundan Test adlı bir klasöre taşır.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 38804ef26d96dc7db8c69742632187c097c89553f7bb314333953f052f93e558
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394413"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Nasıl kullanılır: Öğeleri program aracılığıyla Outlook
  Bu örnek okunmamış e-posta iletilerini Gelen **Kutusundan** Test adlı bir klasöre **taşır.** Örnek yalnızca alanında **Test** sözcüğü olan iletileri `Subject` taşır.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek şunları gerektirir:

- Test Outlook adlı bir posta **klasörü.**

- Alanda Test sözcüğüyle birlikte gelen **bir e-posta** `Subject` iletisi.

## <a name="see-also"></a>Ayrıca bkz.
- [Klasörlerle çalışma](../vsto/working-with-folders.md)
- [Nasıl yapılanlar: Program aracılığıyla klasör adı ile alma](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Nasıl yapılanlar: Belirli bir klasör içinde program aracılığıyla arama](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Nasıl yapacaksınız: E-posta iletisi alınca program aracılığıyla eylemler gerçekleştirme](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
