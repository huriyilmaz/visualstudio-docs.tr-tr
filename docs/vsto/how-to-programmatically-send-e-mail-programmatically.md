---
title: 'Nasıl yapılır: program aracılığıyla e-posta gönderme'
description: Microsoft Outlook 'den programlı bir e-posta göndermek için Visual Studio kullanın. Bu örnek, example.com etki alanı adına sahip kişilere bir e-posta iletisi gönderir.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c1a8f2fb5843ccb39808250ef847e8e5b4355960
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115245"
---
# <a name="how-to-programmatically-send-email"></a>Nasıl yapılır: program aracılığıyla e-posta gönderme
  Bu örnek, e-posta adreslerinde **example.com** etki alanı adına sahip kişilere bir e-posta iletisi gönderir.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek şunları gerektirir:

- **Example.com** etki alanı adına sahip kişiler, e-posta adresleridir.

## <a name="robust-programming"></a>Güçlü programlama
 **Example.com** etki alanı adını arayan filtre kodunu kaldırmayın. Filtreyi kaldırırsanız çözümünüz tüm kişilerinize e-posta iletileri gönderir.

## <a name="see-also"></a>Ayrıca bkz.
- [Posta öğeleriyle çalışma](../vsto/working-with-mail-items.md)
- [Nasıl yapılır: program aracılığıyla e-posta öğesi oluşturma](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [nasıl yapılır: program aracılığıyla Outlook kişilere erişme](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Nasıl yapılır: e-posta iletisi alındığında program aracılığıyla eylem gerçekleştirme](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
