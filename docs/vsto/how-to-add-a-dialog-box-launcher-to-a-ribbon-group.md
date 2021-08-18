---
title: 'Nasıllı: Şerit grubuna İletişim kutusu başlatıcısı ekleme'
description: Şeritteki herhangi bir gruba, grupla ilgili daha fazla seçenek sağlayan ilgili iletişim kutularını veya görev bölmelerini açabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 43ff3dec0245759c35dd8fc4165dc7b279835cde
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037999"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Nasıllı: Şerit grubuna İletişim kutusu başlatıcısı ekleme
  Şeritteki herhangi bir gruba iletişim kutusu başlatıcısı eklemek için kullanabilirsiniz. İletişim kutusu başlatıcısı, bir grupta görünen küçük bir simgedir. Kullanıcılar bu simgeye tıklar ve grupla ilgili daha fazla seçenek sağlayan ilgili iletişim kutularını veya görev bölmelerini açar.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Şerit grubuna iletişim kutusu başlatıcısı eklemek için

1. içinde Şerit kod dosyasını *(.vb* veya *.cs* dosyası) **Çözüm Gezgini.**

2. Görünüm menüsünde **Tasarımcı'ya** **tıklayın.**

3. Şerit Tasarımcısı'nda herhangi bir gruba sağ tıklayın ve ardından İletişim Kutusu **EkleLauncher'a tıklayın.**

     Özel veya <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> yerleşik bir iletişim kutusu açmak için grubun olayına kod ekleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Şerit'e genel bakış](../vsto/ribbon-overview.md)
- [Çalışma zamanında Şerit'e erişme](../vsto/accessing-the-ribbon-at-run-time.md)
- [Office örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Şerit tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [Nasıl Yapılır: Şerit Tasarımcısından Şerit XML'ine Dışarıya Şerit Aktarma](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Nasıl yapın: Şeritteki bir sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Nasıl yapılır: Yerleşik sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)
- [Nasıl olur: Backstage görünümüne Denetimler Ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Şerit'i Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Nasıl Kullanmaya başlayın: Şeridi özelleştirme](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Nasıl kullanılır: Eklenti kullanıcı arabirimi hatalarını gösterme](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Adım adım kılavuz: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Adım adım kılavuz: Çalışma zamanında şeritteki denetimleri güncelleştirme](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Adım adım kılavuz: Şerit XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
