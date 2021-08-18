---
title: Şerit'i Outlook
description: Çalışma alanı içinde şeridi özelleştirerek Microsoft Office Outlook özel şeridinizin uygulamada nerede görüneceklerini göz önünde bulundurabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3c3b200a63ed17afbf4068475ae1509f1bf0da80
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047107"
---
# <a name="customize-a-ribbon-for-outlook"></a>Bir şeridi Outlook
  Çalışma alanı içinde şeridi Microsoft Office Outlook özel şeridinizin uygulamada nerede görüneceklerini göz önünde bulundurabilirsiniz. Outlook, ana uygulama kullanıcı arabiriminde (UI) ve kullanıcılar e-posta iletileri oluşturma gibi belirli görevleri gerçekleştirecekleri zaman açık olan pencerelerde şeridi görüntüler. Bu uygulama pencereleri denetçi olarak adlandırılmıştır.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Ana uygulama kullanıcı arabirimine özel şerit ekleme
 Outlook'daki ana uygulama kullanıcı arabirimi Gezgin olarak çağrılır. Şerit **(Görsel Tasarımcı)** öğesini kullanıyorsanız, Özellikler penceresinde şeridin **RibbonType** özelliğine tıklar ve  ardından **Microsoft.Outlook. Explorer'ı açın.**

## <a name="assign-a-ribbon-to-an-inspector"></a>Denetçiye şerit atama
 Denetçi için ileti sınıfına karşılık gelen şerit türünü belirterek özelleştirmek istediğiniz denetçiyi belirleyin.

 Şerit **(Görsel Tasarımcı)** öğesini kullanıyorsanız, Özellikler penceresinde şeridin  **RibbonType** özelliğine tıklayın ve ardından değer listesinden bir veya daha fazla şerit kimlikleri seçin.

 Bir projeye birden fazla şerit ekleme. Birden fazla şerit bir şerit kimliği paylaşıyorsa, çalışma zamanında hangi şeridin görüntülen bir şerit olduğunu belirtmek için `CreateRibbonExtensibilityObject` `ThisAddin` projenizin sınıfındaki yöntemini geçersiz kılın. Daha fazla bilgi için bkz. [Şerit'e genel bakış.](../vsto/ribbon-overview.md) Her şerit türü hakkında daha fazla bilgi için [2007'de Şeridi özelleştirme Outlook bakın.](/previous-versions/office/developer/office-2007/bb226712(v=office.12))

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Şerit XML kullanarak şerit türünü belirtme
 Şerit **(XML) öğesini kullanıyorsanız** yönteminde *ribbonID* parametresinin değerini <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> kontrol edin ve uygun şeridi geri girin.

 yöntemi, <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> şerit kod dosyasında Visual Studio tarafından otomatik olarak oluşturulur. *ribbonID parametresi,* Gezgin'i veya belirli bir denetçi türünü tanımlayan bir dizedir. *ribbonID* parametresinin olası değerlerinin tam listesi için [2007'de Şeridi Özelleştirme teknik Outlook bakın.](/previous-versions/office/developer/office-2007/bb226712(v=office.12))

 Aşağıdaki kod örneğinde yalnızca denetçide özel şerit görüntüleme adımları `Microsoft.Outlook.Mail.Compose` gösterilir. Bu, bir kullanıcı yeni bir e-posta iletisi oluşturduğunda açılan denetçidir. Görüntü yapılacak şerit, `GetResourceText()` Şerit sınıfında oluşturulan **yönteminde** belirtilir. Şerit sınıfı hakkında daha fazla **bilgi için** bkz. [Şerit XML](../vsto/ribbon-xml.md).

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb" id="Snippet1":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Şerit'e erişme](../vsto/accessing-the-ribbon-at-run-time.md)
- [Şerit'e genel bakış](../vsto/ribbon-overview.md)
- [Şerit tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
