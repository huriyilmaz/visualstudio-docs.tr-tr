---
title: Kullanıcı arabirimi özelliklerini özelleştirme Genişletilebilirlik arabirimlerini kullanarak
description: Office geliştirme Visual Studio kullanıcı arabirimi özelliklerini özelleştirmenize yardımcı olan genişletilebilirlik arabirimleri sağlanmış olduğunu öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], customizing
- application-level add-ins [Office development in Visual Studio], extensibility interfaces
- customizing UI features [Office development in Visual Studio]
- FormRegionStartup interface
- add-ins [Office development in Visual Studio], extensibility interfaces
- extensibility interfaces [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b09bef8bfedc1420172c11ab8913d2ba9b305964ef0cd4d0212477d84490de43
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424417"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>Genişletilebilirlik arabirimlerini kullanarak kullanıcı arabirimi özelliklerini özelleştirme
  Office'daki Visual Studio geliştirme araçları, Visual Studio Eklentisinde özel görev bölmeleri, şerit özelleştirmeleri ve Outlook form bölgeleri oluşturmak için bunları kullanarak birçok uygulama ayrıntılarını VSTO sağlar. Ancak, özel gereksinimleriniz *varsa her özellik için* genişletilebilirlik arabirimini kendiniz de gerçekleştirebilirsiniz.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="overview-of-extensibility-interfaces"></a>Genişletilebilirlik arabirimleri genel bakış
 Microsoft Office, COM eklentilerinin şerit gibi belirli özellikleri özelleştirmek VSTO uygulayan bir dizi genişletilebilirlik arabirimi tanımlar. Bu arabirimler, erişim sağlayan özellikler üzerinde tam denetim sağlar. Ancak, bu arabirimlerin uygulanması yönetilen kodda COM birlikte çalışabilirliği hakkında bilgi gerektirir. Bazı durumlarda bu arabirimlerin programlama modeli, bu arabirimlere alışkın olan geliştiriciler için de sezgisel .NET Framework.

 Visual Studio'da Office proje şablonlarını kullanarak bir VSTO Eklenti oluşturursanız, şerit gibi özellikleri özelleştirmek için genişletilebilirlik arabirimlerini uygulamanıza gerek olmaz. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bu arabirimleri sizin için uygulayan bir uygulamadır. Bunun yerine, kullanıcı tarafından sağlanan daha sezgisel sınıfları ve tasarımcıları Visual Studio. Ancak, genişletilebilirlik arabirimlerini yine de doğrudan VSTO eklentinize genişletilebilirlik arabirimleri ebilirsiniz.

 Bu özellikler için sağladığı sınıflar ve Visual Studio daha fazla bilgi için bkz. Özel [görev](../vsto/custom-task-panes.md)bölmeleri, Şerit [tasarımcısı](../vsto/ribbon-designer.md)ve [Form Outlook oluşturma.](../vsto/creating-outlook-form-regions.md)

## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Bir VSTO Eklentisinde uygulayabilirsiniz genişletilebilirlik arabirimleri
 Aşağıdaki tabloda, uygulayabilirsiniz genişletilebilirlik arabirimleri ve bunları destekleyen uygulamalar listelemektedir.

|Arabirim|Açıklama|Uygulamalar|
|---------------|-----------------|------------------|
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Şerit kullanıcı arabirimini özelleştirmek için bu arabirimi kullanın. **Not:**  Bir projeye **Şerit (XML)** öğesi ekleyebilir ve bu öğenin <xref:Microsoft.Office.Core.IRibbonExtensibility> eklentisinde varsayılan VSTO oluşturabilirsiniz. Daha fazla bilgi için bkz. [Şerit XML](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word|
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Özel bir görev bölmesi oluşturmak için bu arabirimi kullanın.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Form bölgesi oluşturmak için bu Outlook kullanın.|Outlook|

 , ve gibi bir uygulama tarafından tanımlanan Microsoft Office genişletilebilirlik <xref:Microsoft.Office.Core.IBlogExtensibility> <xref:Microsoft.Office.Core.EncryptionProvider> arabirimleri <xref:Microsoft.Office.Core.SignatureProvider> vardır. Visual Studio, proje şablonları kullanılarak oluşturulan VSTO eklentisinde bu arabirimlerin Office desteklemez.

## <a name="use-extensibility-interfaces"></a>Genişletilebilirlik arabirimlerini kullanma
 Bir kullanıcı arabirimi özelliğini genişletilebilirlik arabirimi kullanarak özelleştirmek için eklenti projenize uygun VSTO arabirimini kullanın. Ardından, <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> arabirimini uygulayan sınıfının bir örneğini dönmek için yöntemini geçersiz kılın.

 Outlook için bir VSTO Eklentisinde , ve arabirimlerini uygulamanın nasıl uygulandığını gösteren örnek bir uygulama için, Office örneklerde <xref:Microsoft.Office.Core.IRibbonExtensibility> <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> KULLANıCı Arabirimi Yöneticisi <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> [Örneği'ne bakın.](../vsto/office-development-samples.md)

### <a name="example-of-implementing-an-extensibility-interface"></a>Genişletilebilirlik arabirimi uygulama örneği
 Aşağıdaki kod örneği, özel bir görev bölmesi oluşturmak <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> için arabirimin basit bir uygulamasını gösterir. Bu örnek iki sınıf tanımlar:

- sınıfı, `TaskPaneHelper` özel bir görev bölmesi oluşturmak ve görüntülemek için <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> uygulanır.

- sınıfı `TaskPaneUI` görev bölmesinin kullanıcı arabirimini sağlar. sınıfının öznitelikleri sınıfı COM'da görünür hale gelir ve bu da Microsoft Office `TaskPaneUI` sınıfını bulmalarını sağlar. Bu örnekte kullanıcı arabirimi <xref:System.Windows.Forms.UserControl> boştur, ancak kodu değiştirerek denetimler ebilirsiniz.

  > [!NOTE]
  > Sınıfı COM'da ortaya çıkarmak için, projenin COM Birlikte Çalışma `TaskPaneUI` Için Kaydol **özelliğini** de ayarlayacaksınız.

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb" id="Snippet1":::
  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs" id="Snippet1":::

  uygulama hakkında daha fazla bilgi için, Microsoft Office belgelerinde <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> [2007 Office sistemi](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) içinde özel görev bölmeleri oluşturma.

### <a name="example-of-overriding-the-requestservice-method"></a>RequestService yöntemini geçersiz kılma örneği
 Aşağıdaki kod örneği, önceki kod örneğinden sınıfının bir örneğini geri dönmek için yöntemini <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> `TaskPaneHelper` geçersiz kılmayı gösteriyor. Hangi arabirimin istendığını belirlemek için *serviceGuid* parametresinin değerini denetler ve ardından bu arabirimi uygulayan bir nesnesi döndürür.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.
- [Office örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
- [Yeni Office geliştirme](../vsto/developing-office-solutions.md)
- [Diğer VSTO çözümlerinden eklentilerde kod Office çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Nasıl Office: Visual Studio'da Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
