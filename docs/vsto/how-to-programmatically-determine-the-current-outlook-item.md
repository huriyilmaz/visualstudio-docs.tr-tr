---
title: 'Nasıl Outlook: Program aracılığıyla geçerli Outlook belirleme'
description: Geçerli Microsoft uygulama öğesini program aracılığıyla nasıl Outlook öğrenin. Bu örnekte Explorer.SelectionChange olayı kullanılır.
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
ms.openlocfilehash: 4be80a5b9e07e74432aafbb357df2a989c2d596ebbe2760e8430b462a36bec66
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351856"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Nasıl Outlook: Program aracılığıyla geçerli Outlook belirleme
  Bu örnekte, `Explorer.SelectionChange` geçerli klasörün adını ve seçilen öğe hakkında bazı bilgileri görüntülemek için olayı kullanılır. Kod daha sonra seçili öğeyi görüntüler.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Örnek
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek şunları gerektirir:

- Randevu, iletişim ve e-posta öğeleri Microsoft Office Outlook.

## <a name="see-also"></a>Ayrıca bkz.
- [Outlook modeline genel bakış](../vsto/outlook-object-model-overview.md)
- [Nasıl yapılanlar: Program aracılığıyla klasör adı ile alma](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Nasıl yapılanlar: Program aracılığıyla belirli bir kişi için arama](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
