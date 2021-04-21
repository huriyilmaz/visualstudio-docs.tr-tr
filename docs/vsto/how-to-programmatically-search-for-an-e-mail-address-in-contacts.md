---
title: Kişilerde program aracılığıyla e-posta adresi bulma
description: Microsoft Outlook kişilerinizde bir e-posta adresini programlı bir şekilde bulmak için Visual Studio 'Yu nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd977840cd75081d87011540ca00675fb84cee36
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828949"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Nasıl yapılır: kişilerde program aracılığıyla e-posta adresi arama
  Bu örnek, e-posta adreslerinde **example.com** etki alanı adına sahip kişiler için bir iletişim klasörü arar.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek şunları gerektirir:

- **Example.com** etki alanı adına sahip kişiler, e-posta adreslerinde (örneğin, `somebody@example.com` ) ve ad ve soyadlarına sahiptir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kişi öğeleriyle çalışma](../vsto/working-with-contact-items.md)
- [Nasıl yapılır: program aracılığıyla e-posta gönderme](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Nasıl yapılır: program aracılığıyla Outlook kişilerine erişme](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Nasıl yapılır: Outlook Kişilerine Program aracılığıyla giriş ekleme](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
