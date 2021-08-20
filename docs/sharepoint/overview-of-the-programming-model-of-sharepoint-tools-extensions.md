---
title: SharePoint araç uzantılarının programlama modeline genel bakış
titleSuffix: ''
description: Uygulama araçları uzantılarının programlama modeline SharePoint bakışını okuyun. Genişletilebilirlik arabirimleri uygulama. Nesne modellerini anlama.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: f96c991315483ab4aa8c3764ba9415cf67077a1d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148876"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>SharePoint araçları uzantılarının programlama modeline genel bakış
  Visual Studio'da SharePoint araçları için bir uzantı sanız, SharePoint araçları tarafından ortaya konulan bir veya daha fazla genişletilebilirlik arabirimini SharePoint. Çoğu durumda, uzantınıza özellikler uygulamak için SharePoint araçları tarafından sağlanan diğer türleri de kullanırsiniz. Bazı senaryolarda, uygulama ve uygulama tarafından sağlanan diğer nesne modellerinde Visual Studio SharePoint. Bu nesne modellerinin her biri için amacını anlamanız ve bu modellerle birlikte kullanarak yeni araçlar için uzantılar SharePoint gerekir.

## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Genişletilebilirlik arabirimlerini SharePoint araçları genişletme
 Visual Studio, Managed Extensibility Framework araçları için genişletilebilirlik modelini sağlamak için .NET Framework 4'te SharePoint kullanır. MEF, uygulamaların genişletilebilirlik noktalarını ortaya çıkararak çalışma zamanında uzantıları bulmasını ve yüklemesini sağlayan bir API'dir (System.ComponentModel.Composition derlemesinde uygulanır). MEF hakkında daha fazla bilgi için [bkz. Managed Extensibility Framework &#40;MEF&#41;. ](/dotnet/framework/mef/index)

 Uygulama araçlarını SharePoint için, uygulama tarafından ortaya konulan bir veya daha fazla genişletilebilirlik arabirimi Visual Studio. Ayrıca, arabirim uygulamanıza , ve SharePoint araçlara özgü öznitelikleri de <xref:System.ComponentModel.Composition.ExportAttribute> uygulatabilirsiniz. Aşağıdaki tabloda, uygulama araçlarını genişletmek için uygulay SharePoint listeleniyor.

|Arabirim|Açıklama|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Yeni bir proje öğesi türü tanımlamak için SharePoint kullanın. Bir örnek için, [bkz. Nasıl 2. SharePoint proje öğesi türü tanımlama.](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Bu arabirimi, daha önce SharePoint bir proje öğesi türünü genişletmek için Visual Studio. Bir örnek için, [bkz. Nasıl kullanılır: SharePoint proje öğesi uzantısı oluşturma.](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Projelerini genişletmek için bu SharePoint kullanın. Bir örnek için, [bkz. Nasıl 100 SharePoint 000000000000000000000000000000000000000000](../sharepoint/how-to-create-a-sharepoint-project-extension.md)|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Bu arabirimi, bir proje öğesi dağıtıldığında veya geri çekıldığında yürütül SharePoint yeni bir dağıtım adımı tanımlamak için kullanın. Bir örnek için [bkz. Adım adım: Proje oluşturmak için özel SharePoint oluşturma.](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Sunucu Gezgini penceresindeki Bağlantılar düğümü altındaki **mevcut SharePoint** genişletmek için bu **Sunucu Gezgini** kullanın. Bir örnek için, [bkz. How to: Extend a SharePoint node in Sunucu Gezgini.](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Sunucu Gezgini penceresindeki Bağlantılar düğümü altında **yeni SharePoint** türü tanımlamak için **bu Sunucu Gezgini** kullanın. Bir örnek için, [bkz. How to: Extend a SharePoint node in Sunucu Gezgini.](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Özel özellik doğrulama kuralı tanımlamak için bu arabirimi kullanın. Bir örnek için, [bkz. How to: Create custom feature and package validation rules for SharePoint .](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Özel bir paket doğrulama kuralı tanımlamak için bu arabirimi uygulama. Bir örnek için, [bkz. How to: Create custom feature and package validation rules for SharePoint .](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)|

 SharePoint araçlarının bir uzantısını uygulamaya verdikten sonra, uzantıyı bulmak ve yüklemek için Visual Studio uzantısı (VSIX Visual Studio) paketinde uzantı derlemesini dağıtmanız gerekir. Daha fazla bilgi için [bkz. Visual Studio'de SharePoint araçları için uzantıları dağıtma.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Uygulama araçları uzantılarında kullanılan nesne SharePoint anlama
 Uygulama araçları için uzantılar oluştururken kullanabileceğiniz çeşitli nesne SharePoint vardır:

- *SharePoint araçları nesne modeli.* Bu nesne modeli, SharePoint araçları uzantıları ve diğer ilgili türleri oluşturmak için uygulayan genişletilebilirlik arabirimleri sağlar.

- *Visual Studio otomasyon ve tümleştirme nesnesi modellerini kullanın.* Bu nesne modellerini kullanarak Visual Studio araçları nesne modelinin kapsamının dışında olan SharePoint erişin.

    > [!NOTE]
    > SharePoint araçları nesne modelinde bazı nesneleri Visual Studio otomasyon ve tümleştirme nesnesi modellerinde nesnelere dönüştürebilirsiniz. Bunun tam tersi için de SharePoint proje hizmeti. Daha fazla bilgi için [bkz. SharePoint proje sistemi türleri ile diğer Visual Studio arasında dönüştürme.](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)

- *SharePoint ve istemci nesne modellerini kullanın.* Bu nesne modellerini kullanarak bir SharePoint siteyi değiştirebilir veya SharePoint araçları uzantısı bağlamından SharePoint alın.

### <a name="sharepoint-tools-object-model"></a>SharePoint araçları nesne modeli
 Her SharePoint araçları uzantısı, uzantının temel davranışını SharePoint işlevselliğini tanımlamak için SharePoint araçları nesne modelinde türleri kullanır. Aşağıdaki tablolar, bunları içeren derleme tarafından bu nesne modeline dahil edilen ad alanlarını açıklar.

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll

|Ad Alanı|Açıklama|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint>|Proje sistemini genişletmek ve otomatikleştirmek için SharePoint içerir. Örneğin, yerleşik proje ve SharePoint genişletebilirsiniz veya kendi proje öğelerinizi oluşturabilirsiniz. Daha fazla bilgi için [bkz. SharePoint proje sistemini genişletme.](../sharepoint/extending-the-sharepoint-project-system.md)|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Kendi dağıtım adımlarınızı ve dağıtım yapılandırmalarınızı oluşturma gibi SharePoint projelerinin dağıtım sürecini genişletmek için kullanabileceğiniz türleri içerir. Daha fazla bilgi için [bkz. Paketleme ve SharePoint genişletme.](../sharepoint/extending-sharepoint-packaging-and-deployment.md)|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|SharePoint Penceresindeki Bağlantılar **düğümü altında** düğümleri genişletmek Sunucu Gezgini veya  yeni düğüm türleri tanımlamak için kullanabileceğiniz türleri içerir. Daha fazla bilgi için [bkz. SharePoint'de bağlantı düğümünü Sunucu Gezgini.](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)|
|<xref:Microsoft.VisualStudio.SharePoint.Features>|Bir SharePoint projesinde Özellik tanımlarına erişmek için SharePoint içerir.|
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|Bir çözümde paket tanımına erişmek için SharePoint içerir.|
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|Projelerde özellik ve paket doğrulama davranışını özelleştirmek için SharePoint içerir. Daha fazla bilgi için, [bkz. How to: Create custom feature and package validation rules for SharePoint solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft.VisualStudio.SharePoint.Commands.dll

|Ad Alanı|Açıklama|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|özel komutlarını oluşturmak için kullanabileceğiniz *türleri SharePoint içerir.* Bir SharePoint, bir SharePoint araçları uzantısından SharePoint sunucu nesne modeline çağıran bir yöntemdir. Daha fazla bilgi için [bkz. SharePoint nesne modellerine çağırma.](../sharepoint/calling-into-the-sharepoint-object-models.md)|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll

|Ad Alanı|Açıklama|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Bir SharePoint sitesinde tek tek bileşenleri temsil  eden yerleşik Sunucu Gezgini düğümler (bir listeyi, alanı veya içerik türünü temsil eden bir düğüm gibi) hakkında bilgi almak için kullanabileceğiniz türleri içerir. Daha fazla bilgi için [bkz. SharePoint'de bağlantı düğümünü Sunucu Gezgini.](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)|

### <a name="visual-studio-automation-object-model"></a>Visual Studio otomasyon nesne modeli
 Otomasyon Visual Studio modeli, projeleri ve IDE'leri otomatikleştirmek Visual Studio API'ler sağlar. Visual Studio projelere özgü olmayan projeyle ilgili görevleri gerçekleştirmek veya SharePoint diğer genel otomasyon görevlerini gerçekleştirmek için Visual Studio. Geleneksel olarak, bu nesne modeli genellikle Visual Studio ve makrolarda kullanılır, ancak bu modeli diğer araç SharePoint da kullanabilirsiniz.

 Otomasyon nesne modelinin Visual Studio bölümü, derleme derlemesinde *EnvDTE.dll* tanımlanır. *EnvDTE \\ \<version>.dll* derlemeleri, derlemelerin belirli sürümlerinde tanıtılacak ek Visual Studio. Bu derlemeler, Visual Studio.

 Otomasyon nesne modeli hakkında daha fazla bilgi için [bkz. Visual Studio SDK Başvurusu.](../extensibility/visual-studio-sdk-reference.md)

### <a name="visual-studio-integration-object-model"></a>Visual Studio tümleştirme nesne modeli
 Tümleştirme nesnesi modeli, vsPackage oluşturarak Visual Studio eklemek için *kullanabileceğiniz API'ler sağlar.* VSPackage, araç pencereleri, düzenleyiciler, tasarımcılar, Visual Studio ve projeler gibi özel özellikler sağlayarak IDE'yi genişleten bir modüldür.

 Yerleşik SharePoint araçlarıyla kullanılacak yeni bir Visual Studio eklemek için tümleştirme nesne modelini kullanabilirsiniz. Örneğin, SharePoint sitesi için özel bir eylemi temsil eden özel bir SharePoint proje öğesi oluşturmanız, özel eylem için tasarımcı uygulayan bir VSPackage da oluşturabilirsiniz. tasarımcıyı özel eylemle ilişkilendirmek için proje öğesinin içinde özel eylemi temsil eden bir kısayol menü öğesi **Çözüm Gezgini.** Tasarımcınızı açmak için kısayol menüsünü açabilir (özel eylem proje öğesini sağ tıklayarak veya seçerek ve shift F10 tuşlarını seçerek) ve ardından + Aç'ı **seçebilirsiniz.**

 Bu nesne modeli, Visual Studio SDK'sı ile birlikte bir derleme kümesinde tanımlanır. Bu nesne modelinde ana derlemelerden bazıları , *Microsoft.VisualStudio.Shell.11.0.dll*, *Microsoft.VisualStudio.Shell.Interop.dll* ve *Microsoft.VisualStudio.OLE.Interop.dll.*

 Tümleştirme nesne modeli hakkında daha fazla bilgi için bkz. [Otomasyon Modeline Genel Bakış](../extensibility/internals/automation-model-overview.md) ve Visual Studio SDK [Başvurusu.](../extensibility/visual-studio-sdk-reference.md)

### <a name="sharepoint-object-models"></a>SharePoint modellerini oluşturma
 SharePoint araçları uzantıları, SharePoint bir siteyi değiştirmek veya SharePoint siteden veri almak için SharePoint kullanabilir. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] ve [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] iki farklı nesne modeli sağlar: sunucu nesne modeli ve istemci nesne modeli.

 API'leri bir SharePoint araçları uzantısında herhangi bir nesne modelinde kullanabilirsiniz, ancak her nesne modelinin, SharePoint araçları uzantıları bağlamında bazı avantajları ve dezavantajları vardır. Daha fazla bilgi için [bkz. SharePoint nesne modellerine çağırma.](../sharepoint/calling-into-the-sharepoint-object-models.md)

|Nesne modeli|Açıklama|
|------------------|-----------------|
|Sunucu nesne modeli|Sunucu nesne modeli, program aracılığıyla ortaya çıkaran tüm [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] özelliklere erişim sağlar. Bu nesne modeli, SharePoint sunucusunda SharePoint çözümler tarafından SharePoint tasarlanmıştır. Bu nesne modelinin büyük bir çoğunluğu,Microsoft.SharePoint.dll *tanımlanır.* Sunucu nesne modeli hakkında daha fazla bilgi için [bkz. SharePoint Foundation Server-Side Nesne Modelini Kullanma.](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14))|
|İstemci nesne modeli|İstemci nesne modeli, uzak istemci veya sunucudan gelen verilerle birlikte çalışmak SharePoint sunucu nesne modelinin bir alt kümesidir. Ortak görevleri gerçekleştirmek için yürütülecek gidiş dönüş sayısını en aza indirmek için tasarlanmıştır. İstemci nesne modelinin çoğunluğu, derlemeler ve *Microsoft.SharePoint.Client.dll* *Microsoft.SharePoint.Client.Runtime.dll* tanımlanır. İstemci nesne modeli hakkında daha fazla bilgi için bkz. [Yönetilen İstemci Nesne Modeli.](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14))|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio'SharePoint araçları genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Nesne modellerini SharePoint çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [SharePoint proje hizmeti](../sharepoint/using-the-sharepoint-project-service.md)
