---
title: 'Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme'
description: Bir şeritte özel sekmelerin sırasını değiştirebilir ve sekme koleksiyonu düzenleyicisini kullanarak Şeritteki yerleşik bir sekmeden önce veya sonra özel sekmeleri konumlandırabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 93ce719b8db2280029ad4302adb2afc1e08140de
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106347"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme
  Bir Şeritteki özel sekmelerin sırasını **sekme koleksiyonu düzenleyicisini** kullanarak değiştirebilirsiniz. Şeritteki yerleşik bir sekmeden önce veya sonra özel sekmeler yerleştirebilirsiniz. yerleşik sekme, zaten bir Microsoft Office uygulamasının şeridinde bulunan bir sekmedir. Örneğin, **veri** sekmesi Excel yerleşik bir sekmedir.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Şeritteki sekmelerin sırasını değiştirmek için

1. **Çözüm Gezgini** içindeki Şerit kod dosyasını (*. vb* veya *. cs* dosyası) seçin.

2. **Görünüm** menüsünde **Tasarımcı**' ya tıklayın.

3. Şerit Tasarımcısına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

4. **özellikler** penceresinde, **sekmeler** özelliğini seçin ve ardından üç nokta düğmesini (![ASP.NET mobile designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil tasarımcı elips")) tıklatın.

     **Sekme Koleksiyonu Düzenleyicisi** görünür.

5. **Sekme koleksiyonu düzenleyicisinde**, **Üyeler** listesinde, taşımak istediğiniz sekmeyi seçin ve sekme sırasını değiştirmek için yukarı veya aşağı oklara tıklayın.

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Şeritteki yerleşik bir sekmeden önce veya sonra bir sekmeyi konumlandırmak için

1. Şerit tasarımcısında özel bir sekme seçin.

2. **Özellikler** penceresinde **ControlID** özelliğini genişletin ve **ControlIdType** özelliğinin değerinin **özel** olarak ayarlandığından emin olun.

3. **Özellikler** penceresinde, **konum** özelliğini genişletin.

4. **PositionType** özelliğini uygun değer olarak ayarlayın:

    - **BeforeOfficeId** , belirtilen yerleşik bir sekmeden önce grubu konumlandırır.

    - **AfterOfficeId** , belirtilen yerleşik bir sekmeden sonra grubu konumlandırır.

5. **OfficeId** özelliğini yerleşik bir SEKMENIN denetim kimliği olarak ayarlayın.

     denetim kimliklerinin bir listesi için bkz. [Office 2010 yardım dosyaları: Office floent kullanıcı arabirimi denetim tanımlayıcıları](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>Ayrıca bkz.
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [İzlenecek yol: Şerit XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
