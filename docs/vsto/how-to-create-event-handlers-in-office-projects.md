---
title: 'Nasıl yapılır: Office projelerinde olay işleyicileri oluşturma'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee85d89dcb990cebd595dadbd7b28add4a7b371a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538313"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Nasıl yapılır: Office projelerinde olay işleyicileri oluşturma
  Visual Basic ve C# ' de olay işleyicileri oluşturmanın birkaç yolu vardır. Tasarım görünümünde, denetime çift tıklayarak denetimler için varsayılan olay işleyicilerini oluşturabilir veya denetimdeki herhangi bir olay için işleyiciler oluşturmak üzere **Özellikler** penceresinin Olaylar bölmesini kullanabilirsiniz. Ancak, kod görünümünde çalışıyorsanız, bir olay işleyicisi oluşturmak için Tasarım görünümü geçiş yapmak istemeyebilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>Visual Basic bir olay işleyicisi oluşturmak için

1. Kod düzenleyicisinin en üstündeki **sınıf adı** açılan listesinden, için bir olay işleyicisi oluşturmak istediğiniz nesneyi seçin.

    > [!NOTE]
    > Veya için olay işleyicileri oluşturmak istiyorsanız `ThisDocument` `ThisWorkbook` , **sınıf adı** açılır listesinde **(ThisDocument olayları)** veya **(ThisWorkbook olayları)** öğesini seçmeniz gerekir

2. Kod düzenleyicisinin en üstündeki **Yöntem adı** açılır listesinden olayı seçin.

     Visual Studio olay işleyicisini oluşturur ve ekleme noktasını yeni oluşturulan olay işleyicisine taşımaktadır. Olay işleyicisi zaten varsa, ekleme noktası var olan olay işleyicisine gider.

### <a name="to-create-an-event-handler-in-c"></a>C 'de bir olay işleyicisi oluşturmak için\#

1. Tam olay adını yazıp bir boşluk ve ardından boşluk olmadan yazarak, sınıfının **Başlangıç** olayında olay temsilcisini oluşturun **+=** . Örneğin:

     `this.<object name>.<event name> +=`

2. Kod satırının sonunda TAB tuşuna iki kez basın.

     Visual Studio kod satırını otomatik olarak tamamlar, olay işleyicisini oluşturur ve ekleme noktasını yeni oluşturulan olay işleyicisine taşımaktadır.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
- [İzlenecek yol: NamedRange denetimi olaylarına karşı programlama](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Office çözümleri oluşturma](../vsto/building-office-solutions.md)
