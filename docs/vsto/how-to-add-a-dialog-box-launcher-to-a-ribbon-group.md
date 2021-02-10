---
title: 'Nasıl yapılır: Şerit grubuna Iletişim kutusu Başlatıcısı Ekleme'
description: Bir şeritte, grupla ilgili daha fazla seçenek sağlayan ilgili iletişim kutularını veya görev bölmelerini açan herhangi bir gruba bir iletişim kutusu Başlatıcısı ekleyebilirsiniz.
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
ms.workload:
- office
ms.openlocfilehash: d8e04b7549d1b6a458f0993804946502f55f0165
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942288"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Nasıl yapılır: Şerit grubuna Iletişim kutusu Başlatıcısı Ekleme
  Şeritteki herhangi bir gruba bir iletişim kutusu Başlatıcısı ekleyebilirsiniz. İletişim kutusu Başlatıcısı, bir grupta görüntülenen küçük bir simgedir. Kullanıcılar, grupla ilgili daha fazla seçenek sağlayan ilgili iletişim kutularını veya görev bölmelerini açmak için bu simgeye tıklayın.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Şerit grubuna iletişim kutusu başlatıcısı eklemek için

1. **Çözüm Gezgini** içindeki Şerit kod dosyasını (*. vb* veya *. cs* dosyası) seçin.

2. **Görünüm** menüsünde **Tasarımcı**' ya tıklayın.

3. Şerit Tasarımcısı ' nda herhangi bir gruba sağ tıklayın ve ardından **DialogBoxLauncher Ekle**' ye tıklayın.

     <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick>Özel veya yerleşik bir iletişim kutusu açmak için grubun olayına kod ekleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Çalışma zamanında Şerite erişin](../vsto/accessing-the-ribbon-at-run-time.md)
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [Nasıl Yapılır: Şerit Tasarımcısından Şerit XML'ine Dışarıya Şerit Aktarma](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)
- [Nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Outlook için şerit özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md)
- [Nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Nasıl yapılır: eklenti Kullanıcı arayüzü hatalarını gösterme](../vsto/how-to-show-add-in-user-interface-errors.md)
- [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [İzlenecek yol: çalışma zamanında Şeritteki denetimleri güncelleştirme](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [İzlenecek yol: Şerit XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
