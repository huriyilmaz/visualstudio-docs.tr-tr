---
title: InfoPath için bir şeridi özelleştirme
description: Microsoft Office InfoPath ' te Şeriti özelleştirirken, özel şeritlerinizin uygulamada nerede görüneceğini göz önünde bulundurmanız gerektiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5af7c4ed2f396c5a806cc42c49c8f4209b6b5c2c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828143"
---
# <a name="customize-a-ribbon-for-infopath"></a>InfoPath için bir şeridi özelleştirme
  Microsoft Office InfoPath ' te şeridi özelleştirdiğinizde, özel şeritlerinizin uygulamada nerede görüneceğini göz önünde bulundurmanız gerekir. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] , aşağıdaki üç InfoPath uygulama penceresi türünde şeridi görüntüleyebilir:

- Tasarım modunda açılan bir form şablonu görüntüleyen Windows.

- Form şablonunu temel alan bir form görüntüleyen pencereler.

- Baskı Önizleme penceresi.

  **Uygulama hedefi:** Bu konudaki bilgiler, InfoPath 2010 için VSTO eklentisi projelerine yöneliktir. Daha fazla bilgi için bkz. [Office uygulaması ve proje türü tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).

  Kullanıcılar ve tasarımcılar, şablonun görünümünü ve yerleşimini değiştirmek için tasarım modunda bir form şablonu açar. Kullanıcılar, içerik eklemek için form şablonunu temel alan formları açar.

  Baskı Önizleme penceresi, tasarımcılara ve kullanıcılara yazdırmadan önce form veya form şablonunun sayfalarını önizlemesine olanak sağlar.

> [!NOTE]
> **Eklentiler** sekmesi baskı önizleme penceresinde görünmüyor. Baskı Önizleme penceresinde bir özel sekmenin görünmesini istiyorsanız, sekmenin **OfficeId** özelliğinin **TabAddIns** olarak ayarlandığından emin olun.

 Şeritlerinizin görünmesini istediğiniz her pencerenin Şerit türünü belirtmeniz gerekir.

## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>Şerit tasarımcısında Şerit türünü belirtme
 **Şerit (görsel Tasarımcı)** öğesini kullanıyorsanız, **Özellikler** penceresinde şeridin **RibbonType** özelliğine tıklayın ve sonra aşağıdaki tabloda açıklanan şerit kimliklerinden birini seçin.

|Şerit KIMLIĞI|Projeyi çalıştırdığınızda şeridin görüneceği pencere|
|---------------|---------------------------------------------------------------------|
|**Microsoft. InfoPath. Designer**|Tasarım modunda açılan bir form şablonu görüntüleyen Windows.|
|**Microsoft. InfoPath. Editor**|Form şablonunu temel alan bir form görüntüleyen pencereler.|
|**Microsoft. InfoPath. PrintPreview**|Baskı Önizleme penceresi.|

 Projeye birden fazla şerit ekleyebilirsiniz. Birden fazla şerit bir şerit KIMLIĞINI paylaşıyorsa, `CreateRibbonExtensibilityObject` `ThisAddin` çalışma zamanında hangi Şeritin görüntüleneceğini belirtmek için projenizin sınıfındaki yöntemi geçersiz kılın. Daha fazla bilgi için bkz. [Şerit 'e genel bakış](../vsto/ribbon-overview.md).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Şerit XML kullanarak Şerit türünü belirtme
 **Şerit (XML)** öğesini kullanıyorsanız, yöntemindeki *ribbonID* parametresinin değerini kontrol edin <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> ve uygun Şeriti döndürün.

 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>Yöntemi, Visual Studio tarafından Şerit kod dosyasında otomatik olarak oluşturulur. *RibbonID* parametresi, açılan InfoPath penceresinin türünü tanımlayan bir dizedir.

 Aşağıdaki kod örneği, yalnızca tasarım modunda form şablonu görüntüleyen bir pencerede özel bir şerit 'in nasıl görüntüleneceğini gösterir. Görüntülenecek Şerit, `GetResourceText()` Şerit sınıfında oluşturulan yönteminde belirtilir. Şerit sınıfı hakkında daha fazla bilgi için bkz. [RIBBON XML](../vsto/ribbon-xml.md).

 :::code language="csharp" source="../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb" id="Snippet1":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Şerite erişin](../vsto/accessing-the-ribbon-at-run-time.md)
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
