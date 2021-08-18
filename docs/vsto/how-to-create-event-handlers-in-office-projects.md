---
title: 'Nasıl Office: Projelerde olay Office oluşturma'
description: Visual Basic ve C# içinde denetimler için varsayılan olay işleyicileri oluşturmanın çeşitli yollarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 6a3ef99f7032f3112ec65a110259a2ad7b3af6ba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122845"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Nasıl Office: Projelerde olay Office oluşturma
  Visual Basic ve C# ile olay işleyicileri oluşturmanın birkaç yolu vardır. Tasarım görünümünde, denetime çift tıklayarak denetimler için varsayılan olay işleyicileri oluşturabilir veya  denetimde herhangi bir olay için işleyiciler oluşturmak üzere Özellikler penceresinin olaylar bölmesini kullanabilirsiniz. Ancak, Kod görünümündeysiniz, olay işleyicisi oluşturmak için Tasarım görünümü'ye geçmek istemeyebilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>İşleyicide olay işleyicisi Visual Basic

1. Kod **Düzenleyicisi'nin** üst kısmında yer alan Sınıf Adı açılan listesinden, olay işleyicisi oluşturmak istediğiniz nesneyi seçin.

    > [!NOTE]
    > veya için olay işleyicileri oluşturmak için Sınıf Adı açılan `ThisDocument` `ThisWorkbook` **listesinden (ThisDocument Olayları)** veya **(ThisWorkbook Olayları)** öğesini seçmeniz gerekir 

2. Kod **Düzenleyicisi'nin** üst kısmında yer alan Yöntem Adı açılan listesinden olayı seçin.

     Visual Studio işleyiciyi oluşturur ve ekleme noktasını yeni oluşturulan olay işleyiciye taşır. Olay işleyicisi zaten varsa, ekleme noktası mevcut olay işleyiciye taşınır.

### <a name="to-create-an-event-handler-in-c"></a>C'de olay işleyicisi oluşturmak için\#

1. Sınıfın Başlangıç olayında, uygun **olay** adını ve ardından bir boşluk yazarak ve ardından boşluk yazmadan olay **+=** temsilcisini oluşturun. Örnek:

     `this.<object name>.<event name> +=`

2. Kod satırı sonunda SEKME tuşuna iki kez basın.

     Visual Studio kod satırı otomatik olarak tamamlanır, olay işleyicisi oluşturulur ve ekleme noktasını yeni oluşturulan olay işleyiciye taşır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kod yazma Office yazma](../vsto/writing-code-in-office-solutions.md)
- [Adım adım kılavuz: NamedRange denetimi olaylarına karşı programla](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Yeni Office oluşturma](../vsto/building-office-solutions.md)
