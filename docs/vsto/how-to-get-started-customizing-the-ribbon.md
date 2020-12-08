---
title: 'Nasıl yapılır: Şeriti özelleştirmeye başlama'
description: Bir Microsoft Office uygulamasının şeritlerini özelleştirmeyi, bir şerit (görsel Tasarımcı) veya şerit (XML) öğesini bir Office projesine eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, adding Ribbon to project
- Ribbon [Office development in Visual Studio], adding
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, adding Ribbon to project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3974fe85a97226a920959b41256fa7e29923c9d1
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845953"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Nasıl yapılır: Şeriti özelleştirmeye başlama
  Bir Microsoft Office uygulamasının Şeridini özelleştirmek için bir Office projesine **Şerit (görsel Tasarımcı)** veya **Şerit (XML)** öğesi ekleyin.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Bir projeye Şerit eklemek için

1. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

2. **Yeni öğe Ekle** Iletişim kutusunda **Şerit (görsel Tasarımcı)** veya **Şerit (XML)** öğesini seçin. Bu şablonlar hakkında daha fazla bilgi için bkz. [Şerit 'e genel bakış](../vsto/ribbon-overview.md).

3. **Ad** kutusuna şerit öğesi için bir ad yazın.

    Adlar aşağıdaki karakterleri içeremez:

   - Sterlin (#)

   - Yüzde (%)

   - Ve işareti (&)

   - Yıldız işareti (*)

   - Dikey çubuk (|)

   - Ters eğik çizgi ( \\ )

   - İki nokta (:)

   - Çift tırnak işareti (")

   - Küçüktür ( \< )

   - Büyüktür (>)

   - Soru işareti (?)

   - Eğik çizgi (/)

   - Baştaki veya sondaki boşluklar (' ')

   - Windows veya DOS için ayrılan adlar ("nul", "AUX", "Con", "COM1", "lpt1" vb.)

4. **Tamam** düğmesine tıklayın.

   Şerit öğesi **Çözüm Gezgini** görünür. Sonraki adımlar hakkında daha fazla bilgi için bkz. [Şerite genel bakış](../vsto/ribbon-overview.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Şerite erişin](../vsto/accessing-the-ribbon-at-run-time.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [İzlenecek yol: Şerit XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
