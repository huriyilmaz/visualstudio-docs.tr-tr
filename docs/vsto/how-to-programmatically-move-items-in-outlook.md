---
title: 'Nasıl yapılır: Outlook program aracılığıyla öğeleri taşıma'
description: Microsoft Outlook 'da nasıl program aracılığıyla öğe taşıyabileceğinizi öğrenin. Bu örnek, okunmamış e-posta iletilerini gelen kutusundan test adlı bir klasöre taşır.
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
ms.openlocfilehash: c6d67712ca09fa99cd1fef00740acfda2fe34cac
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725568"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Nasıl yapılır: Outlook program aracılığıyla öğeleri taşıma
  Bu örnek, okunmamış e-posta iletilerini **gelen kutusundan** **Test** adlı bir klasöre taşır. Örnek yalnızca alan içindeki bir kelime **testine** sahip iletileri taşıdır `Subject` .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek şunları gerektirir:

- **Test** adlı Outlook posta klasörü.

- Alanda sözcük **testine** ulaşan bir e-posta iletisi `Subject` .

## <a name="see-also"></a>Ayrıca bkz.
- [Klasörlerle çalışma](../vsto/working-with-folders.md)
- [Nasıl yapılır: program aracılığıyla bir klasörü ada göre alma](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Nasıl yapılır: belirli bir klasör içinde program aracılığıyla arama](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Nasıl yapılır: e-posta iletisi alındığında program aracılığıyla eylem gerçekleştirme](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
