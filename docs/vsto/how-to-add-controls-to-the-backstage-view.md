---
title: 'Nasıl olur: Backstage görünümüne denetimler ekleme '
description: Dosya sekmesine tıklarsanız açılan menüye denetim eklemek için Şerit Tasarımcısı'nın nasıl kullanabileceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f667011410938af59bf0f50f3ac5ece833157557
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725592"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Nasıl olur: Backstage görünümüne denetimler ekleme
  Dosya sekmesine tıklarsanız açılan menüye denetim eklemek için Şerit **Tasarımcısı'nın kullanabilirsiniz.** Uygulamayı çalıştırsanız, Dosya sekmesine ekley **istediğiniz denetimler** Eklentiler adlı **bir grup görünür.**

 Şerit tasarımcısını kullanarak yerleşik denetimler öncesinde veya sonrasında denetimleri Visual Studio. Yerleşik denetim, Backstage görünümünde zaten görünen bir denetimdir. Denetimleri yerleşik denetimler öncesinde veya sonrasında konumlandırmak için Şerit XML'i kullansanız iyi olur. Şerit **(XML) hakkında daha fazla bilgi için** bkz. Şerit [XML](../vsto/ribbon-xml.md). Backstage görünümünü özelleştirme hakkında daha fazla bilgi için bkz. Geliştiriciler için [Office 2010 Backstage](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) görünümüne giriş ve Geliştiriciler için [Office 2010 Backstage görünümünü özelleştirme.](/previous-versions/office/developer/office-2010/ee815851(v=office.14))

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Backstage görünümüne denetim eklemek için

1. Şerit öğesini Tasarım görünümü.

     Projenize Şerit **(Görsel Tasarımcı)** öğesi ekleme hakkında bilgi için bkz. Nasıl Kullanmaya başlayın [şeridini özelleştirme.](../vsto/how-to-get-started-customizing-the-ribbon.md)

2. Şerit Tasarımcısı'nda Dosya **sekmesine** tıklayın.

     Bir menü tasarımcısı görüntülenir. Bu tasarım yüzeyi herhangi bir denetim içermez.

3. Araç **Office Şerit Denetimleri** sekmesinden, aşağıdaki denetimlerden herhangi birini menü tasarımcısına sürükleyin:

    - Düğme

    - CheckBox

    - Galeri

    - Menü

    - Ayırıcı

    - Splitbutton

    - ToggleButton

4. Denetimleri sürükleyerek menüyü yeni konumlara getirin.

## <a name="see-also"></a>Ayrıca bkz.
- [Şerit'e genel bakış](../vsto/ribbon-overview.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [Nasıl Kullanmaya başlayın: Şeridi özelleştirme](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Adım adım kılavuz: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
