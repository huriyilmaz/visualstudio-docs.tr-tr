---
title: 'Nasıl yapılır: program aracılığıyla Outlook kişilerine erişme'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2f6d64512af660392c10082e3bcd3c26b6bc6885
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520112"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Nasıl yapılır: program aracılığıyla Outlook kişilerine erişme
  Bu örnek, son adları belirtilen arama dizesini içeren tüm kişileri bulur.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek şunları gerektirir:

- Son adları **kişiler** klasöründeki "**na"** dizesini (örneğin, Tzipi Butnaru) içeren kişiler.

## <a name="see-also"></a>Ayrıca bkz.
- [Kişi öğeleriyle çalışma](../vsto/working-with-contact-items.md)
- [Nasıl yapılır: Outlook Kişilerine Program aracılığıyla giriş ekleme](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Nasıl yapılır: program aracılığıyla belirli bir kişi arama](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Nasıl yapılır: kişilerde program aracılığıyla e-posta adresi arama](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [Nasıl yapılır: Outlook kişilerini program aracılığıyla silme](../vsto/how-to-programmatically-delete-outlook-contacts.md)
