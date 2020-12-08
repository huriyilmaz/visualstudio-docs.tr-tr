---
title: Outlook için şerit özelleştirme
description: Microsoft Office Outlook ' ta Şeriti özelleştirirken, özel şeritlerinizin uygulamada nerede görüneceğini göz önünde bulundurmanız gerektiğini öğrenin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25b4faa994a99bccdc2122ad6b9d124f7391e9f8
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848111"
---
# <a name="customize-a-ribbon-for-outlook"></a>Outlook için şerit özelleştirme
  Microsoft Office Outlook 'ta Şeriti özelleştirdiğinizde, özel şeritlerinizin uygulamada nerede görüneceğini göz önünde bulundurmanız gerekir. Outlook, ana uygulama kullanıcı arabiriminde (UI) ve kullanıcılar e-posta iletileri oluşturma gibi belirli görevleri gerçekleştirirken açık olan Windows 'da şeridi görüntüler. Bu uygulama pencereleri Inspectors olarak adlandırılmıştır.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Ana uygulama kullanıcı arabirimine özel bir şerit ekleme
 Outlook 'ta ana uygulama kullanıcı arabirimine gezgin denir. **Şerit (görsel Tasarımcı)** öğesini kullanıyorsanız, **Özellikler** penceresinde şeridin **RibbonType** özelliğine tıklayıp ardından **Microsoft. Outlook. Explorer**' ı seçerek gezgin 'e bir şerit ekleyebilirsiniz.

## <a name="assign-a-ribbon-to-an-inspector"></a>Bir Inspector 'a şerit atama
 Inspector için ileti sınıfına karşılık gelen Şerit türünü belirterek özelleştirmek istediğiniz Inspector 'ı belirlersiniz.

 **Şerit (görsel Tasarımcı)** öğesini kullanıyorsanız, **Özellikler** penceresinde şeridin **RibbonType** özelliğine tıklayın ve ardından değerler listesinden bir veya daha fazla şerit kimliği seçin.

 Projeye birden fazla şerit ekleyebilirsiniz. Birden fazla şerit bir şerit KIMLIĞINI paylaşıyorsa, `CreateRibbonExtensibilityObject` `ThisAddin` çalışma zamanında hangi Şeritin görüntüleneceğini belirtmek için projenizin sınıfındaki yöntemi geçersiz kılın. Daha fazla bilgi için bkz. [Şerit 'e genel bakış](../vsto/ribbon-overview.md). Her şerit türü hakkında daha fazla bilgi için bkz. [Outlook 2007 'Deki şeridi özelleştirme](/previous-versions/office/developer/office-2007/bb226712(v=office.12))teknik makalesi.

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Şerit XML kullanarak Şerit türünü belirtme
 **Şerit (XML)** öğesini kullanıyorsanız, yöntemindeki *ribbonID* parametresinin değerini kontrol edin <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> ve uygun Şeriti döndürün.

 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>Yöntemi, Visual Studio tarafından Şerit kod dosyasında otomatik olarak oluşturulur. *RibbonID* parametresi, Gezgin 'i veya belirli bir Inspector türünü tanımlayan bir dizedir. *RibbonID* parametresinin olası değerlerinin tüm listesi için bkz. [Outlook 2007 'deki şeridi özelleştirme](/previous-versions/office/developer/office-2007/bb226712(v=office.12))teknik makalesi.

 Aşağıdaki kod örneği, özel bir şeridin yalnızca Inspector 'da nasıl görüntüleneceğini gösterir `Microsoft.Outlook.Mail.Compose` . Bu, Kullanıcı yeni bir e-posta iletisi oluşturduğunda açılan Inspector ' dır. Görüntülenecek Şerit, `GetResourceText()` **Şerit** sınıfında oluşturulan yönteminde belirtilir. **Şerit** sınıfı hakkında daha fazla bilgi için bkz. [Ribbon XML](../vsto/ribbon-xml.md).

 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Şerite erişin](../vsto/accessing-the-ribbon-at-run-time.md)
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
