---
title: 'Nasıl yapılır: Yerleşik sekmeyi özelleştirme'
description: Yerleşik bir sekmeye grup ve denetim ekleme hakkında bilgi. Yerleşik sekme, bir uygulamanın Şeridinde zaten yer alan bir Microsoft Office sekmedir.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c97f4b3ff73c0a41495832930611a483ec073872
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129430808"
---
# <a name="how-to-customize-a-built-in-tab"></a>Nasıl yapılır: Yerleşik sekmeyi özelleştirme
  Yerleşik bir sekmeye grup ve denetim ekleyebilirsiniz. Yerleşik sekme, bir uygulamanın Şeridinde zaten yer alan bir Microsoft Office sekmedir. Örneğin Veri **sekmesi,** veri sekmesindeki yerleşik bir Excel. Özel bir grup oluşturma, sekmede en son görüntülenir, ancak grubu sekmenin herhangi bir yerine taşıyabilirsiniz.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> Yerleşik bir sekmeye grup ekleyebilirsiniz, ancak yerleşik grupları yerleşik bir sekmeden kaldıramazsiniz.

### <a name="to-add-groups-to-a-built-in-tab"></a>Yerleşik sekmeye grup eklemek için

1. içinde Şerit kod dosyasına sağ tıklayın ve **Çözüm Gezgini'a** Görünüm Tasarımcısı.

    > [!NOTE]
    > Şerit kodu dosyası dosyanın içinde **görünmüyorsa Çözüm Gezgini** projenize **bir Şerit öğesi** eklemeniz gerekir. Bkz. [Nasıl Kullanmaya başlayın: şeridi özelleştirme.](../vsto/how-to-get-started-customizing-the-ribbon.md)

2. Şerit tasarımcısında herhangi bir sekmeye sağ tıklayın ve ardından Özellikler'e **tıklayın.**

3. Özellikler **penceresinde ControlId** özelliğini genişletin ve **ControlIdType** özelliğini **Office.** 

4. **OfficeId özelliğini** özelleştirmek *istediğiniz yerleşik* sekmenin denetim kimliğine ayarlayın.

     Denetim kimliği, uygulama uygulamalarında yerleşik olarak yer alan sekmeleri, grupları ve denetimleri benzersiz Microsoft Office adıdır.

     Denetim kimliklerinin listesi için bkz. [Office 2010 yardım dosyaları: Office akıcı kullanıcı arabirimi denetim tanımlayıcıları.](https://www.microsoft.com/download/details.aspx?id=50745)

5. Araç **Office Şerit Denetimleri** **sekmesinden** grupları sekmeye sürükleyin.

    > [!NOTE]
    > Yerleşik gruplar tasarımcıda görünmez. Bu nedenle, yerleşik bir sekmeyle çalışıp çalışmama konusunda karara varmanın tek yolu sekmenin **ControlId** özelliğini incelemektir.

### <a name="to-position-groups-on-a-built-in-tab"></a>Yerleşik bir sekmede grupları konumlandırmak için

1. Şerit Tasarımcısı'nda özel bir grup seçin.

2. Özellikler **penceresinde** Konum özelliğini **genişletin.**

3. **PositionType özelliğini** uygun değere ayarlayın:

    - **BeforeOfficeId,** grubu belirtilen yerleşik grubun önünde konumlandırmaz.

    - **AfterOfficeId,** grubu belirtilen yerleşik gruptan sonra konumlar.

4. **OfficeId özelliğini** yerleşik bir grubun denetim kimliğine ayarlayın.

     Denetim kimliklerinin listesi için bkz. [Office 2010 yardım dosyaları: Office akıcı kullanıcı arabirimi denetim tanımlayıcıları.](https://www.microsoft.com/download/details.aspx?id=50745)

## <a name="see-also"></a>Ayrıca bkz.
- [Şerit'e genel bakış](../vsto/ribbon-overview.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [Adım adım kılavuz: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Adım adım kılavuz: Şerit XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Nasıl Kullanmaya başlayın: şeridi özelleştirme](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Nasıl yapın: Şeritteki bir sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Nasıl olur: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Nasıl kullanılır: Eklenti kullanıcı arabirimi hatalarını gösterme](../vsto/how-to-show-add-in-user-interface-errors.md)
