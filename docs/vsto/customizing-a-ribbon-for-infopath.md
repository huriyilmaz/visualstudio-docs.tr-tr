---
title: InfoPath için Şerit Özelleştirme
description: InfoPath'te Şerit'i Microsoft Office özel Şerit'inizin uygulamada nerede görüneceklerini düşünmeniz gerektiğini öğrenin.
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
ms.openlocfilehash: 63507abd8f9583b837c32ae1e72edbcfe2a514d1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122053878"
---
# <a name="customize-a-ribbon-for-infopath"></a>InfoPath için Şerit Özelleştirme
  InfoPath'te Şerit Microsoft Office özelleştirerek özel Şerit'inizin uygulamada nerede görünebileceğinizi göz önünde bulundurabilirsiniz. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] Şerit'i aşağıdaki üç InfoPath uygulama penceresinde görüntüleniyor olabilir:

- Windows modunda açılan bir form şablonunun görüntüleniyor.

- Windows şablonunu temel alan bir formun görüntüleniyor.

- Baskı Önizleme penceresi.

  **Aşağıdakiler için geçerlidir:** Bu konudaki bilgiler InfoPath 2010 için VSTO projelerinde geçerlidir. Daha fazla bilgi için [bkz. Uygulama ve Office tarafından kullanılabilen özellikler.](../vsto/features-available-by-office-application-and-project-type.md)

  Kullanıcılar ve tasarımcılar, şablonun görünümünü ve düzenini değiştirmek için tasarım modunda bir form şablonu açar. Kullanıcılar, içerik eklemek için form şablonuna dayalı formları açar.

  Baskı Önizleme penceresi, tasarımcıların ve kullanıcıların bir formun veya form şablonunun sayfalarını yazdırmadan önce önizlemesini sağlar.

> [!NOTE]
> **AddIns** sekmesi Baskı Önizleme penceresinde görünmez. Baskı Önizleme penceresinde özel bir sekmenin görünmesini istemiyorsanız, sekmenin **OfficeId** özelliğinin **TabAddIns** olarak ayarlanmaz.

 Şeridinizin görünmesini istediğiniz her pencerenin Şerit türünü belirtmeniz gerekir.

## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>Şerit tasarımcısında Şerit türünü belirtme
 Şerit **(Görsel Tasarımcı)** öğesini kullanıyorsanız, Özellikler penceresinde Şerit'in  **RibbonType** özelliğine tıklayın ve ardından aşağıdaki tabloda açıklanan Şerit Kimliklerinden herhangi birini seçin.

|Şerit Kimliği|Projeyi çalıştırarak Şerit'in görüntüln olduğu pencere|
|---------------|---------------------------------------------------------------------|
|**Microsoft.InfoPath.Designer**|Windows modunda açılan bir form şablonunun görüntüleniyor.|
|**Microsoft.InfoPath.Editor**|Windows şablonunu temel alan bir formun görüntüleniyor.|
|**Microsoft.InfoPath.PrintPreview**|Baskı Önizleme penceresi.|

 Bir projeye birden fazla Şerit ekleme. Birden fazla Şerit bir Şerit Kimliği paylaşıyorsa, çalışma zamanında hangi Şeridin görüntülen bir Şerit olduğunu belirtmek için `CreateRibbonExtensibilityObject` `ThisAddin` projenizin sınıfındaki yöntemini geçersiz kılın. Daha fazla bilgi için bkz. [Şerit'e genel bakış.](../vsto/ribbon-overview.md)

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Şerit XML kullanarak Şerit türünü belirtme
 Şerit **(XML) öğesini kullanıyorsanız** yönteminde *ribbonID* parametresinin değerini <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> kontrol edin ve uygun Şeridi geri girin.

 yöntemi, <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> Şerit kod dosyasında Visual Studio tarafından otomatik olarak oluşturulur. *ribbonID parametresi,* açılan InfoPath penceresinin türünü tanımlayan bir dizedir.

 Aşağıdaki kod örneği, yalnızca tasarım modunda form şablonu görüntüleyen bir pencerede özel şerit görüntülemeyi gösterir. Görüntü yapılacak Şerit, `GetResourceText()` Şerit sınıfında oluşturulan yönteminde belirtilir. Şerit sınıfı hakkında daha fazla bilgi için bkz. [Şerit XML](../vsto/ribbon-xml.md).

 :::code language="csharp" source="../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb" id="Snippet1":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Şerit'e erişme](../vsto/accessing-the-ribbon-at-run-time.md)
- [Şerit'e genel bakış](../vsto/ribbon-overview.md)
- [Şerit tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
