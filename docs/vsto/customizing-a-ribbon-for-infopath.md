---
title: InfoPath için bir şeridi özelleştirme
description: Microsoft Office ınfopath ' te şeriti özelleştirirken, özel şeritlerinizin uygulamada nerede görüneceğini göz önünde bulundurmanız gerektiğini öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: dd83519b850add8642f0858106f1bc83f5d52503614f05612dca5b2bd9f0f342
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394803"
---
# <a name="customize-a-ribbon-for-infopath"></a>InfoPath için bir şeridi özelleştirme
  Microsoft Office ınfopath ' te şeridi özelleştirdiğinizde, özel şeritlerinizin uygulamada nerede görüneceğini göz önünde bulundurmanız gerekir. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] , aşağıdaki üç InfoPath uygulama penceresi türünde şeridi görüntüleyebilir:

- tasarım modunda açılan bir form şablonu görüntüleyen Windows.

- form şablonunu temel alan bir form görüntüleyen Windows.

- Baskı Önizleme penceresi.

  **Uygulama hedefi:** bu konudaki bilgiler, ınfopath 2010 VSTO eklenti projelerine yöneliktir. daha fazla bilgi için bkz. [Office uygulama ve proje türü tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).

  Kullanıcılar ve tasarımcılar, şablonun görünümünü ve yerleşimini değiştirmek için tasarım modunda bir form şablonu açar. Kullanıcılar, içerik eklemek için form şablonunu temel alan formları açar.

  Baskı Önizleme penceresi, tasarımcılara ve kullanıcılara yazdırmadan önce form veya form şablonunun sayfalarını önizlemesine olanak sağlar.

> [!NOTE]
> **Eklentiler** sekmesi baskı önizleme penceresinde görünmüyor. Baskı Önizleme penceresinde bir özel sekmenin görünmesini istiyorsanız, sekmenin **OfficeId** özelliğinin **TabAddIns** olarak ayarlandığından emin olun.

 Şeritlerinizin görünmesini istediğiniz her pencerenin Şerit türünü belirtmeniz gerekir.

## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>Şerit tasarımcısında Şerit türünü belirtme
 **Şerit (görsel Tasarımcı)** öğesini kullanıyorsanız, **Özellikler** penceresinde şeridin **RibbonType** özelliğine tıklayın ve sonra aşağıdaki tabloda açıklanan şerit kimliklerinden birini seçin.

|Şerit KIMLIĞI|Projeyi çalıştırdığınızda şeridin görüneceği pencere|
|---------------|---------------------------------------------------------------------|
|**Microsoft. InfoPath. Designer**|tasarım modunda açılan bir form şablonu görüntüleyen Windows.|
|**Microsoft. InfoPath. Editor**|form şablonunu temel alan bir form görüntüleyen Windows.|
|**Microsoft. InfoPath. PrintPreview**|Baskı Önizleme penceresi.|

 Projeye birden fazla şerit ekleyebilirsiniz. Birden fazla şerit bir şerit KIMLIĞINI paylaşıyorsa, `CreateRibbonExtensibilityObject` `ThisAddin` çalışma zamanında hangi Şeritin görüntüleneceğini belirtmek için projenizin sınıfındaki yöntemi geçersiz kılın. Daha fazla bilgi için bkz. [Şerit 'e genel bakış](../vsto/ribbon-overview.md).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Şerit XML kullanarak Şerit türünü belirtme
 **Şerit (XML)** öğesini kullanıyorsanız, yöntemindeki *ribbonID* parametresinin değerini kontrol edin <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> ve uygun Şeriti döndürün.

 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>yöntemi, şerit kod dosyasında Visual Studio tarafından otomatik olarak oluşturulur. *RibbonID* parametresi, açılan InfoPath penceresinin türünü tanımlayan bir dizedir.

 Aşağıdaki kod örneği, yalnızca tasarım modunda form şablonu görüntüleyen bir pencerede özel bir şerit 'in nasıl görüntüleneceğini gösterir. Görüntülenecek Şerit, `GetResourceText()` Şerit sınıfında oluşturulan yönteminde belirtilir. Şerit sınıfı hakkında daha fazla bilgi için bkz. [RIBBON XML](../vsto/ribbon-xml.md).

 :::code language="csharp" source="../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb" id="Snippet1":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Şerite erişin](../vsto/accessing-the-ribbon-at-run-time.md)
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
