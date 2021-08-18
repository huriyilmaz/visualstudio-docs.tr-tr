---
title: 'nasıl yapılır: program aracılığıyla geçerli Outlook öğeyi belirleme'
description: geçerli Microsoft Outlook öğesini programlı bir şekilde nasıl belirleyebileceğinizi öğrenin. Bu örnek Explorer. SelectionChange olayını kullanır.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9d2f6ba1230ce306f742468d96c47dfdcf17b8d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083244"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>nasıl yapılır: program aracılığıyla geçerli Outlook öğeyi belirleme
  Bu örnek, `Explorer.SelectionChange` geçerli klasörün adını ve seçili öğe hakkında bazı bilgileri göstermek için olayını kullanır. Kod daha sonra seçili öğeyi görüntüler.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek şunları gerektirir:

- Microsoft Office Outlook içindeki randevu, iletişim ve e-posta öğeleri.

## <a name="see-also"></a>Ayrıca bkz.
- [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)
- [Nasıl yapılır: program aracılığıyla bir klasörü ada göre alma](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Nasıl yapılır: program aracılığıyla belirli bir kişi arama](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
