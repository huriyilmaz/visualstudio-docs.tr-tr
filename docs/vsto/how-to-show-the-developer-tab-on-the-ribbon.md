---
title: 'Nasıl yapılır: Şeritte Geliştirici sekmesini gösterme'
description: Visual Studio 'Yu kullanarak bir Microsoft Word belgesindeki Şeritteki Geliştirici sekmesini programlı bir şekilde gösterme hakkında bilgi edinin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4dc38b941d27cab0653b923ddd03ba8b78eeab58
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528139"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Nasıl yapılır: Şeritte Geliştirici sekmesini gösterme
  Bir Office uygulamasının şeridinde **Geliştirici** sekmesine erişmek için, varsayılan olarak görünmediğinden bu sekmeyi gösterecek şekilde yapılandırmanız gerekir. Örneğin, <xref:Microsoft.Office.Tools.Word.GroupContentControl> Word için belge düzeyi özelleştirmeye eklemek istiyorsanız bu sekmeyi göstermeli.

> [!NOTE]
> Bu kılavuz yalnızca Office 2010 veya üzeri uygulamalar için geçerlidir. Bu sekmeyi 2007 Microsoft Office sisteminde göstermek istiyorsanız, bu konunun aşağıdaki sürümüne bakın [: Şeritte Geliştirici sekmesini gösterme](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> Access bir **Geliştirici** sekmesine sahip değildir.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-show-the-developer-tab"></a>Geliştirici sekmesini göstermek için

1. Bu konu tarafından desteklenen Office uygulamalarından herhangi birini başlatın. Bu konunun önceki kısımlarında bulunan **:** Note bölümüne bakın.

2. **Dosya** sekmesinde **Seçenekler** düğmesini seçin.

     Aşağıdaki şekilde Office 2010 ' deki **Dosya** sekmesi ve **Seçenekler** düğmesi gösterilmektedir.

     ![Dosya seçme, Outlook 2010 seçenekleri](../vsto/media/vsto-office-file-tab.png "Dosya seçme, Outlook 2010 seçenekleri")

     Aşağıdaki şekilde Office 2013 ' deki **Dosya** sekmesi gösterilmektedir.

     ![Outlook 2013 dosya sekmesi](../vsto/media/vsto-office2013-filetab.png "Outlook 2013 dosya sekmesi")

     Aşağıdaki şekilde Office 2013 ' deki **Seçenekler** düğmesi gösterilmektedir.

     ![Outlook 2013 Preview 'daki Seçenekler düğmesi](../vsto/media/vsto-office2013-optionsbutton.png "Outlook 2013 Preview 'daki Seçenekler düğmesi")

3. _ApplicationName_**seçenekleri** Iletişim kutusunda, **Şeridi Özelleştir** düğmesini seçin.

     Aşağıdaki şekilde, Excel 2010 ' de **Seçenekler** iletişim kutusu ve **Şeridi Özelleştir** düğmesi gösterilmektedir. Bu düğmenin konumu, bu konunun en üstündeki "uygulandığı öğe" bölümünde listelenen tüm diğer uygulamalarda benzerdir.

     ![Şeridi Özelleştir düğmesi](../vsto/media/vsto-office2010-customizeribbonbutton.png "Şeridi Özelleştir düğmesi")

4. Ana sekmeler listesinde, **Geliştirici** onay kutusunu seçin.

     Aşağıdaki şekilde, Word 2010 ve içindeki **Geliştirici** onay kutusu gösterilmektedir [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] . Bu onay kutusunun konumu, bu konunun en üstündeki "uygulandığı öğe" bölümünde listelenen tüm diğer uygulamalarda benzerdir.

     ![Word Seçenekleri iletişim kutusunda Geliştirici onay kutusu](../vsto/media/vsto-office2010-developercheckbox.png "Word Seçenekleri iletişim kutusunda Geliştirici onay kutusu")

5. **Seçenekler** iletişim kutusunu kapatmak için **Tamam** düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
