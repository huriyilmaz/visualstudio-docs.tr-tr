---
title: 'Nasıl yapılır: Şeritte Geliştirici sekmesini gösterme'
description: geliştirici sekmesini bir Microsoft Word belgesinde programlı olarak göstermek için Visual Studio nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 382f9f62367734785c997989fb96ccf6414e9360
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083022"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Nasıl yapılır: Şeritte Geliştirici sekmesini gösterme
  **geliştirici** sekmesine bir Office uygulamasının şeritine erişmek için, varsayılan olarak görünmediğinden bu sekmeyi gösterecek şekilde yapılandırmanız gerekir. Örneğin, <xref:Microsoft.Office.Tools.Word.GroupContentControl> Word için belge düzeyi özelleştirmeye eklemek istiyorsanız bu sekmeyi göstermeli.

> [!NOTE]
> bu kılavuz yalnızca Office 2010 veya üzeri uygulamalar için geçerlidir. bu sekmeyi 2007 Microsoft Office sisteminde göstermek istiyorsanız, bu konunun aşağıdaki sürümüne bakın [: şeritte geliştirici sekmesini gösterme](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> Access bir **Geliştirici** sekmesine sahip değildir.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-show-the-developer-tab"></a>Geliştirici sekmesini göstermek için

1. bu konu tarafından desteklenen Office uygulamalardan birini başlatın. Bu konunun önceki kısımlarında bulunan **:** Note bölümüne bakın.

2. **Dosya** sekmesinde **Seçenekler** düğmesini seçin.

     aşağıdaki şekil Office 2010 ' deki **dosya** sekmesini ve **seçenekler** düğmesini gösterir.

     ![dosya seçme, Outlook 2010 ' de seçenekler](../vsto/media/vsto-office-file-tab.png "dosya seçme, Outlook 2010 ' de seçenekler")

     aşağıdaki şekilde Office 2013 ' deki **dosya** sekmesi gösterilmektedir.

     ![Outlook 2013 ' deki dosya sekmesi](../vsto/media/vsto-office2013-filetab.png "Outlook 2013 ' deki dosya sekmesi")

     aşağıdaki şekil Office 2013 ' deki **seçenekler** düğmesini gösterir.

     ![Outlook 2013 Preview ' daki seçenekler düğmesi](../vsto/media/vsto-office2013-optionsbutton.png "Outlook 2013 Preview ' daki seçenekler düğmesi")

3. _ApplicationName_**seçenekleri** Iletişim kutusunda, **Şeridi Özelleştir** düğmesini seçin.

     aşağıdaki şekilde, **seçenekler** iletişim kutusu ve Excel 2010 ' deki **şeridi özelleştir** düğmesi gösterilmektedir. Bu düğmenin konumu, bu konunun en üstündeki "uygulandığı öğe" bölümünde listelenen tüm diğer uygulamalarda benzerdir.

     ![Şeridi Özelleştir düğmesi](../vsto/media/vsto-office2010-customizeribbonbutton.png "Şeridi Özelleştir düğmesi")

4. Ana sekmeler listesinde, **Geliştirici** onay kutusunu seçin.

     Aşağıdaki şekilde, Word 2010 ve içindeki **Geliştirici** onay kutusu gösterilmektedir [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] . Bu onay kutusunun konumu, bu konunun en üstündeki "uygulandığı öğe" bölümünde listelenen tüm diğer uygulamalarda benzerdir.

     ![Word Seçenekleri iletişim kutusunda Geliştirici onay kutusu](../vsto/media/vsto-office2010-developercheckbox.png "Word Seçenekleri iletişim kutusunda Geliştirici onay kutusu")

5. **Seçenekler** iletişim kutusunu kapatmak için **Tamam** düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
