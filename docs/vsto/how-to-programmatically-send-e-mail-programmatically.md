---
title: 'Nasıl yapılır: program aracılığıyla e-posta gönderme'
description: Microsoft Outlook 'tan programlı bir şekilde e-posta göndermek için Visual Studio 'Yu kullanın. Bu örnek, example.com etki alanı adına sahip kişilere bir e-posta iletisi gönderir.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5f31fdb92a5acff16b1d6e8001ea88931a9a22ab
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525381"
---
# <a name="how-to-programmatically-send-email"></a>Nasıl yapılır: program aracılığıyla e-posta gönderme
  Bu örnek, e-posta adreslerinde **example.com** etki alanı adına sahip kişilere bir e-posta iletisi gönderir.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>Örnek
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek şunları gerektirir:

- **Example.com** etki alanı adına sahip kişiler, e-posta adresleridir.

## <a name="robust-programming"></a>Güçlü programlama
 **Example.com** etki alanı adını arayan filtre kodunu kaldırmayın. Filtreyi kaldırırsanız çözümünüz tüm kişilerinize e-posta iletileri gönderir.

## <a name="see-also"></a>Ayrıca bkz.
- [Posta öğeleriyle çalışma](../vsto/working-with-mail-items.md)
- [Nasıl yapılır: program aracılığıyla e-posta öğesi oluşturma](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Nasıl yapılır: program aracılığıyla Outlook kişilerine erişme](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Nasıl yapılır: e-posta iletisi alındığında program aracılığıyla eylem gerçekleştirme](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
