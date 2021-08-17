---
title: ekleri Outlook e-posta öğelerinden program aracılığıyla kaydetme
description: Microsoft Outlook e-posta öğelerinden ekleri programlı bir şekilde kaydetmek için Visual Studio nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0099f06210dc7164df28a3e3b3f3e3e3ef7cb54865a7ead0585fdccf21d1cf0d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394270"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>nasıl yapılır: Outlook e-posta öğelerinden program aracılığıyla ekleri kaydetme

Bu örnek, e-posta eki, posta gelen kutusuna alındığında belirtilen klasöre kaydedilir.

> [!IMPORTANT]
> Bu örnek yalnızca C dizininin köküne **TestFileSave** adlı bir klasör eklerseniz geçerlidir.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek

:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Ayrıca bkz.

- [Posta öğeleriyle çalışma](../vsto/working-with-mail-items.md)
- [Nasıl yapılır: program aracılığıyla bir klasörü ada göre alma](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Nasıl yapılır: e-posta iletisi alındığında program aracılığıyla eylem gerçekleştirme](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Nasıl yapılır: belirli bir klasör içinde program aracılığıyla arama](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
