---
title: 'Nasıl yapılır: yerleşik bir sekmeyi özelleştirme'
description: Yerleşik bir sekmeye grupları ve denetimleri nasıl ekleyebileceğiniz hakkında bilgi edinin. yerleşik sekme, zaten bir Microsoft Office uygulamasının şeridinde bulunan bir sekmedir.
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
ms.openlocfilehash: ea01db137d7c1f6144f43e84f901e92702815fdf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046886"
---
# <a name="how-to-customize-a-built-in-tab"></a>Nasıl yapılır: yerleşik bir sekmeyi özelleştirme
  Yerleşik bir sekmeye grup ve denetim ekleyebilirsiniz. yerleşik sekme, zaten bir Microsoft Office uygulamasının şeridinde bulunan bir sekmedir. Örneğin, **veri** sekmesi Excel yerleşik bir sekmedir. Özel bir grup oluşturduğunuzda, bu sekme en son sekmede görünür, ancak grubunuzu sekme üzerinde herhangi bir yere taşıyabilirsiniz.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> Yerleşik bir sekmeye grup ekleyebilirsiniz, ancak yerleşik bir sekmeden yerleşik grupları kaldıramazsınız.

### <a name="to-add-groups-to-a-built-in-tab"></a>Yerleşik bir sekmeye gruplar eklemek için

1. **Çözüm Gezgini**' de şerit kodu dosyasına sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

    > [!NOTE]
    > Şerit kod dosyası **Çözüm Gezgini** görünmüyorsa, projenize bir **Şerit öğesi** eklemeniz gerekir. Bkz. [nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Şerit Tasarımcısı ' nda herhangi bir sekmeye sağ tıklayın ve ardından **Özellikler**' e tıklayın.

3. **Özellikler** penceresinde **ControlID** özelliğini genişletin ve sonra **controlıdtype** özelliğini **Office** olarak ayarlayın.

4. **OfficeId** özelliğini, özelleştirmek istediğiniz yerleşik SEKMENIN *denetim kimliği* olarak ayarlayın.

     denetim kimliği, Microsoft Office uygulamalarda yerleşik olarak bulunan sekmeleri, grupları ve denetimleri benzersiz bir şekilde tanımlayan addır.

     denetim kimliklerinin bir listesi için bkz. [Office 2010 yardım dosyaları: Office floent kullanıcı arabirimi denetim tanımlayıcıları](https://www.microsoft.com/download/details.aspx?id=6627).

5. **araç kutusunun** **Office şerit denetimleri** sekmesinden grupları sekmeye sürükleyin.

    > [!NOTE]
    > Yerleşik gruplar tasarımcıda görünmez. Bu nedenle, yerleşik bir sekme ile çalışıp çalışmadığını belirlemenin tek yolu, sekmenin **ControlID** özelliğini incelemektir.

### <a name="to-position-groups-on-a-built-in-tab"></a>Grupları yerleşik bir sekmede konumlandırmak için

1. Şerit tasarımcısında özel bir grup seçin.

2. **Özellikler** penceresinde, **konum** özelliğini genişletin.

3. **PositionType** özelliğini uygun değer olarak ayarlayın:

    - **BeforeOfficeId** , grubu belirtilen yerleşik bir gruptan önce konumlandırır.

    - **AfterOfficeId** , belirtilen yerleşik bir gruptan sonra grubu konumlandırır.

4. **OfficeId** özelliğini yerleşik bir grubun denetim kimliği olarak ayarlayın.

     denetim kimliklerinin bir listesi için bkz. [Office 2010 yardım dosyaları: Office floent kullanıcı arabirimi denetim tanımlayıcıları](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>Ayrıca bkz.
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [İzlenecek yol: Şerit XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Nasıl yapılır: eklenti Kullanıcı arayüzü hatalarını gösterme](../vsto/how-to-show-add-in-user-interface-errors.md)
