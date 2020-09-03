---
title: Outlook e-posta öğelerinden ekleri program aracılığıyla Kaydet
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9fbe6099a8928397a7d885ac72c4f34da2da6af0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545892"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Nasıl yapılır: Outlook e-posta öğelerinden program aracılığıyla ekleri kaydetme

Bu örnek, e-posta eki, posta gelen kutusuna alındığında belirtilen klasöre kaydedilir.

> [!IMPORTANT]
> Bu örnek yalnızca C dizininin köküne **TestFileSave** adlı bir klasör eklerseniz geçerlidir.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek

[!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [Posta öğeleriyle çalışma](../vsto/working-with-mail-items.md)
- [Nasıl yapılır: program aracılığıyla bir klasörü ada göre alma](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Nasıl yapılır: e-posta iletisi alındığında program aracılığıyla eylem gerçekleştirme](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Nasıl yapılır: belirli bir klasör içinde program aracılığıyla arama](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
