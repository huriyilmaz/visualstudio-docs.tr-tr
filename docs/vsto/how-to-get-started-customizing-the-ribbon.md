---
title: 'Nasıl Kullanmaya başlayın: şeridi özelleştirme'
description: Bir uygulamanın Şeridini özelleştirmeyi, Microsoft Office projesine Şerit (Görsel Tasarımcı) veya Şerit (XML) Office öğrenin.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f4042a8d68ac940df8e84ac62fb85b902879e1ff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083472"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Nasıl Kullanmaya başlayın: şeridi özelleştirme
  Bir uygulamanın Şeridini özelleştirmek Microsoft Office bir Office projesine Şerit **(Görsel Tasarımcı)** veya Şerit **(XML)** öğesi ekleyin.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Projeye şerit eklemek için

1. Yeni **Project** **Ekle'ye tıklayın.**

2. Yeni Öğe **Ekle iletişim kutusunda** Şerit (Görsel Tasarımcı) veya Şerit **(XML)** **öğesini seçin.** Bu şablonlar hakkında daha fazla bilgi için bkz. [Şerit'e genel bakış.](../vsto/ribbon-overview.md)

3. Ad **kutusuna** Şerit öğesi için bir ad yazın.

    Adlar aşağıdaki karakterleri içeremez:

   - Pound (#)

   - Yüzde (%)

   - Ve (&)

   - Yıldız işareti (*)

   - Dikey çubuk (|)

   - Ters eğik çizgi ( \\ )

   - İki nokta (:)

   - Çift tırnak işareti (")

   - Küçük ( \< )

   - Büyüktür (>)

   - Soru işareti (?)

   - Eğik çizgi (/)

   - Baştaki veya sonda boşluklar (' ')

   - Windows veya DOS için ("nul", "aux", "con", "com1", "lpt1" gibi) ayrılmış adlar

4. **Tamam**'a tıklayın.

   Şerit öğesi, öğesinde **Çözüm Gezgini.** Sonraki adımlar hakkında bilgi için bkz. [Şerit'e genel bakış.](../vsto/ribbon-overview.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Şerit'e erişme](../vsto/accessing-the-ribbon-at-run-time.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [Adım adım kılavuz: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Adım adım kılavuz: Şerit XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
