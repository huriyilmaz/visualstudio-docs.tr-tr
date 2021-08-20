---
title: Genişletilebilirlik arabirimlerini kullanarak Kullanıcı arabirimi özelliklerini özelleştirme
description: Visual Studio Office geliştirme araçlarının kullanıcı arabirimi özelliklerini özelleştirmenize yardımcı olan genişletilebilirlik arabirimleri sağladığını öğrenin.
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
ms.openlocfilehash: 4e4c37a90774cdbd148900a8df9ddb6b3d58bb1c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106542"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>Genişletilebilirlik arabirimlerini kullanarak Kullanıcı arabirimi özelliklerini özelleştirme
  Visual Studio Office geliştirme araçları, bir VSTO eklenti içinde özel görev bölmeleri, şerit özelleştirmeleri ve Outlook form bölgeleri oluşturmak için kullandığınızda birçok uygulama ayrıntılarını işleyen sınıflar ve tasarımcılar sağlar. Ancak, özel gereksinimleriniz varsa, her bir özellik için *genişletilebilirlik arabirimini* de uygulayabilirsiniz.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="overview-of-extensibility-interfaces"></a>Genişletilebilirlik arabirimlerine genel bakış
 Microsoft Office, COM VSTO eklentilerinin şerit gibi belirli özellikleri özelleştirmek için uygulayabileceği bir genişletilebilirlik arabirimleri kümesi tanımlar. Bu arabirimler, erişimi sağladıkları Özellikler üzerinde tam denetim sağlar. Ancak, bu arabirimlerin uygulanması yönetilen kodda COM birlikte çalışabilirlik hakkında bilgi gerektirir. Bazı durumlarda, bu arabirimlerin programlama modeli .NET Framework alışkın olan geliştiriciler için de sezgisel değildir.

 Visual Studio Office proje şablonlarını kullanarak bir VSTO eklentisi oluşturduğunuzda, şerit gibi özellikleri özelleştirmek için genişletilebilirlik arabirimlerini uygulamanız gerekmez. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Bu arabirimleri sizin için uygular. Bunun yerine, Visual Studio tarafından sunulan daha sezgisel sınıflar ve tasarımcılar kullanabilirsiniz. ancak, isterseniz doğrudan VSTO eklentilerinizde genişletilebilirlik arabirimlerini uygulayabilirsiniz.

 Visual Studio bu özellikler için sağladığı sınıflar ve tasarımcılar hakkında daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md), [şerit tasarımcısı](../vsto/ribbon-designer.md)ve [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>VSTO bir eklentiye uygulayabileceğiniz genişletilebilirlik arabirimleri
 Aşağıdaki tabloda uygulayabileceğiniz genişletilebilirlik arabirimleri ve bunları destekleyen uygulamalar listelenmektedir.

|Arabirim|Açıklama|Uygulamalar|
|---------------|-----------------|------------------|
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Şerit kullanıcı arabirimini özelleştirmek için bu arabirimi uygulayın. **Note:**  VSTO eklentiinizdeki varsayılan bir uygulama oluşturmak için, bir projeye **şerit (XML)** öğesi ekleyebilirsiniz <xref:Microsoft.Office.Core.IRibbonExtensibility> . Daha fazla bilgi için bkz. [ŞERIT XML](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word|
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Özel bir görev bölmesi oluşturmak için bu arabirimi uygulayın.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Outlook form bölgesi oluşturmak için bu arabirimi uygulayın.|Outlook|

 ,, ve gibi Microsoft Office tarafından tanımlanan diğer birçok genişletilebilirlik arabirimi vardır <xref:Microsoft.Office.Core.IBlogExtensibility> <xref:Microsoft.Office.Core.EncryptionProvider> <xref:Microsoft.Office.Core.SignatureProvider> . Visual Studio, Office proje şablonları kullanılarak oluşturulan bir VSTO eklentisinin bu arabirimlerin uygulanmasının kullanılmasını desteklemez.

## <a name="use-extensibility-interfaces"></a>Genişletilebilirlik arabirimlerini kullanma
 bir kullanıcı arabirimi özelliğini bir genişletilebilirlik arabirimi kullanarak özelleştirmek için, VSTO eklenti projenizde uygun arabirimi uygulayın. Ardından, <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> arabirimini uygulayan sınıfının bir örneğini döndürmek için yöntemini geçersiz kılın.

 <xref:Microsoft.Office.Core.IRibbonExtensibility>Outlook için bir VSTO eklentisinin,, ve arabirimlerinin nasıl uygulanacağını gösteren örnek bir uygulama için <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> , [Office geliştirme örneklerinde](../vsto/office-development-samples.md)uı yöneticisi örneğine bakın.

### <a name="example-of-implementing-an-extensibility-interface"></a>Genişletilebilirlik arabirimi uygulama örneği
 Aşağıdaki kod örneği, <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> özel bir görev bölmesi oluşturmak için arabirimin basit bir uygulamasını gösterir. Bu örnek iki sınıfı tanımlar:

- `TaskPaneHelper`Sınıfı, <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> özel bir görev bölmesi oluşturup göstermek için uygular.

- `TaskPaneUI`Sınıfı, görev bölmesinin kullanıcı arabirimini sağlar. sınıfının öznitelikleri, `TaskPaneUI` sınıfı COM 'a görünür hale getirir ve bu, Microsoft Office uygulamaların sınıfı bulmasını sağlar. Bu örnekte, Kullanıcı arabirimi boştur <xref:System.Windows.Forms.UserControl> , ancak kodu değiştirerek denetimler ekleyebilirsiniz.

  > [!NOTE]
  > `TaskPaneUI`Sınıfı com 'a sunmak için, proje Için **REGISTER for com Interop** özelliğini de ayarlamanız gerekir.

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb" id="Snippet1":::
  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs" id="Snippet1":::

  uygulama hakkında daha fazla bilgi için <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> , Microsoft Office belgelerindeki [2007 Office sisteminde özel görev bölmeleri oluşturma](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) konusuna bakın.

### <a name="example-of-overriding-the-requestservice-method"></a>RequestService metodunu geçersiz kılma örneği
 Aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> önceki kod örneğinden sınıfının bir örneğini döndürmek için yönteminin nasıl geçersiz kılınacağını göstermektedir `TaskPaneHelper` . Hangi arabirimin istendiğini öğrenmek için *serviceGuid* parametresinin değerini denetler ve ardından bu arabirimi uygulayan bir nesne döndürür.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [diğer Office çözümlerdeki VSTO eklentilerdeki kodu çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [nasıl yapılır: Visual Studio Office projeler oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
