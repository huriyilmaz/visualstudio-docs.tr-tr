---
title: SharePoint Araç uzantılarının programlama modeline genel bakış
titleSuffix: ''
description: SharePoint araçları uzantılarının programlama modeline genel bakış konusunu okuyun. Genişletilebilirlik arabirimlerini uygulayın. Nesne modellerini anlayın.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 67e0f4ae5b06e96747a7257b2b9b444566235877
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305127"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>SharePoint Araç uzantılarının programlama modeline genel bakış
  Visual Studio 'da SharePoint araçları için bir uzantı oluşturduğunuzda, SharePoint araçları tarafından sunulan bir veya daha fazla genişletilebilirlik arabirimini uygulayarak başlarsınız. Çoğu durumda, uzantınızın özelliklerini uygulamak için SharePoint araçları tarafından sunulan diğer türleri de kullanacaksınız. Bazı senaryolarda, Visual Studio ve SharePoint tarafından sunulan diğer nesne modellerinde türleri de kullanabilirsiniz. Bu nesne modellerinin her birinin amacını anlamalısınız ve SharePoint araçları için uzantı oluşturmak üzere bunları birbirleriyle nasıl kullanacağınızı bilmeniz gerekir.

## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Genişletilebilirlik arabirimlerini uygulayarak SharePoint araçlarını genişletin
 Visual Studio, SharePoint araçları için genişletilebilirlik modeli sağlamak üzere .NET Framework 4 ' te Managed Extensibility Framework (MEF) kullanır. MEF, uygulamaların genişletilebilirlik noktaları sergilemesini ve çalışma zamanında uzantıları bulmasını ve yüklemesini sağlayan bir API 'dir (System. ComponentModel. Composition derlemesinde uygulanır). MEF hakkında daha fazla bilgi için bkz. [Managed Extensibility Framework &#40;MEF&#41;](/dotnet/framework/mef/index).

 SharePoint araçlarını genişletmek için, Visual Studio tarafından sunulan bir veya daha fazla genişletilebilirlik arabirimini uygulayın. Ayrıca, <xref:System.ComponentModel.Composition.ExportAttribute> arayüz uygulamanıza, gerektiğinde ve ek SharePoint araçlarına özel öznitelikler de uygulamanız gerekir. Aşağıdaki tabloda, SharePoint araçlarını genişletmek için uygulayabileceğiniz arabirimler listelenmektedir.

|Arabirim|Description|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Bu arabirimi yeni bir SharePoint proje öğesi türü tanımlamak için uygulayın. Bir örnek için bkz. [nasıl yapılır: bir SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Visual Studio 'da zaten yüklü olan bir SharePoint proje öğesi türünü genişletmek için bu arabirimi uygulayın. Bir örnek için bkz. [nasıl yapılır: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|SharePoint projelerini genişletmek için bu arabirimi uygulayın. Bir örnek için bkz. [nasıl yapılır: SharePoint Proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Bu arabirimi, SharePoint proje öğesi dağıtıldığında veya geri çekildiğinde yürütülebilecek yeni bir dağıtım adımı tanımlamak için uygulayın. Bir örnek için bkz. [Izlenecek yol: SharePoint projeleri için özel bir dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|**Sunucu Gezgini** penceresindeki **SharePoint bağlantıları** düğümü altında var olan bir düğümü genişletmek için bu arabirimi uygulayın. Bir örnek için bkz. [nasıl yapılır: bir SharePoint düğümünü Sunucu Gezgini genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|**Sunucu Gezgini** penceresindeki **SharePoint bağlantıları** düğümü altında yeni bir düğüm türü tanımlamak için bu arabirimi uygulayın. Bir örnek için bkz. [nasıl yapılır: bir SharePoint düğümünü Sunucu Gezgini genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Özel bir özellik doğrulama kuralı tanımlamak için bu arabirimi uygulayın. Bir örnek için bkz. [nasıl yapılır: SharePoint çözümleri için özel özellik ve paket doğrulama kuralları oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Özel bir paket doğrulama kuralı tanımlamak için bu arabirimi uygulayın. Bir örnek için bkz. [nasıl yapılır: SharePoint çözümleri için özel özellik ve paket doğrulama kuralları oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

 SharePoint araçlarının bir uzantısını uyguladıktan sonra, Visual Studio 'nun uzantıyı bulmasını ve yüklemesini sağlamak için uzantı derlemesini bir Visual Studio uzantısı (VSıX) paketinde dağıtmanız gerekir. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>SharePoint araçları uzantılarında kullandığınız nesne modellerini anlayın
 SharePoint araçları için uzantı oluştururken kullanabileceğiniz birkaç nesne modeli vardır:

- *SharePoint araçları nesne modeli*. Bu nesne modeli, SharePoint Araçları uzantıları oluşturmak için uyguladığınız genişletilebilirlik arabirimlerini ve diğer ilgili türleri sağlar.

- *Visual Studio otomasyonu ve Tümleştirme nesne modelleri*. SharePoint araçları nesne modelinin kapsamı ötesinde Visual Studio özelliklerine erişmek için bu nesne modellerini kullanın.

    > [!NOTE]
    > SharePoint araçları nesne modelindeki bazı nesneleri Visual Studio Otomasyon ve Tümleştirme nesne modellerindeki nesnelere dönüştürebilir, SharePoint proje hizmetini kullanarak bunun tersini yapabilirsiniz. Daha fazla bilgi için bkz. [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

- *SharePoint Server ve istemci nesne modelleri*. SharePoint sitesi değiştirmek veya SharePoint sitesinden SharePoint araçları uzantısı bağlamından veri almak için bu nesne modellerini kullanın.

### <a name="sharepoint-tools-object-model"></a>SharePoint araçları nesne modeli
 Her SharePoint araçları uzantısı, uzantının temel davranışını ve işlevselliğini tanımlamak için SharePoint araçları nesne modelindeki türleri kullanır. Aşağıdaki tablolar, bu nesne modelinde yer alan ad alanlarını, bunları içeren derleme tarafından anlatmaktadır.

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll

|Ad Alanı|Description|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint>|SharePoint proje sistemini genişletmek ve otomatikleştirmek için kullandığınız türleri içerir. Örneğin, yerleşik SharePoint projelerini ve proje öğelerini genişletebilir veya kendi proje öğelerinizi de oluşturabilirsiniz. Daha fazla bilgi için bkz. [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Kendi dağıtım adımlarınızı ve dağıtım yapılandırmalarının oluşturulması gibi, SharePoint projeleri için dağıtım işlemini genişletmek için kullandığınız türleri içerir. Daha fazla bilgi için bkz. [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|**Sunucu Gezgini** penceresindeki **SharePoint bağlantıları** düğümü altında düğümleri genişletmek veya yeni düğüm türlerini tanımlamak için kullandığınız türleri içerir. Daha fazla bilgi için, bkz. [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Features>|Bir SharePoint projesindeki Özellik tanımlarına erişmek için kullandığınız türleri içerir.|
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|Bir SharePoint çözümünde paket tanımına erişmek için kullandığınız türleri içerir.|
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|SharePoint projeleri için özellik ve paket doğrulama davranışını özelleştirmek üzere kullandığınız türleri içerir. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint çözümleri için özel özellik ve paket doğrulama kuralları oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft.VisualStudio.SharePoint.Commands.dll

|Ad Alanı|Description|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Özel *SharePoint komutları* oluşturmak için kullanabileceğiniz türleri içerir. SharePoint komutu SharePoint Araçlar uzantısından SharePoint Server nesne modeline çağıran bir yöntemdir. Daha fazla bilgi için bkz. [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md).|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll

|Ad Alanı|Description|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Bir liste, alan veya içerik türünü temsil eden bir düğüm gibi bir SharePoint sitesindeki tek tek bileşenleri temsil eden yerleşik **Sunucu Gezgini** düğümleri hakkında bilgi almak için kullanabileceğiniz türleri içerir. Daha fazla bilgi için, bkz. [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|

### <a name="visual-studio-automation-object-model"></a>Visual Studio Otomasyon nesne modeli
 Visual Studio Otomasyon nesne modeli, Visual Studio projelerini ve IDE 'yi otomatikleştirmek için kullanabileceğiniz API 'Ler sağlar. SharePoint projelerine özgü olmayan projeyle ilgili görevleri veya Visual Studio 'da diğer genel otomasyon görevlerini gerçekleştirmek için Visual Studio nesne modeli ' ni kullanın. Geleneksel olarak, bu nesne modeli genellikle Visual Studio eklentilerinde ve makrolarında kullanılır, ancak bunu SharePoint araçları uzantılarında de kullanabilirsiniz.

 Visual Studio Automation nesne modelinin ana bölümü *EnvDTE.dll* derlemesinde tanımlanmıştır. *EnvDTE \\ \<version> . dll* derlemeleri, Visual Studio 'nun belirli sürümlerinde tanıtılan ek işlevler sağlar. Bu derlemeler Visual Studio 'Ya dahildir.

 Otomasyon nesne modeli hakkında daha fazla bilgi için bkz. [Visual STUDIO SDK başvurusu](../extensibility/visual-studio-sdk-reference.md).

### <a name="visual-studio-integration-object-model"></a>Visual Studio Tümleştirme nesne modeli
 Integration Object modeli, *VSPackage* oluşturarak Visual Studio 'ya özellik eklemek Için kullanabileceğiniz API 'ler sağlar. VSPackage, araç pencereleri, düzenleyiciler, tasarımcılar, hizmetler ve projeler gibi özel özellikler sağlayarak Visual Studio IDE 'yi genişleten bir modüldür.

 Yerleşik SharePoint araçlarıyla kullanılacak yeni bir Visual Studio özelliği eklemek istiyorsanız, Tümleştirme nesne modelini kullanabilirsiniz. Örneğin, bir SharePoint sitesi için özel bir eylemi temsil eden özel bir SharePoint proje öğesi oluşturursanız, özel eylem için Tasarımcı uygulayan bir VSPackage da oluşturabilirsiniz. **Çözüm Gezgini** içindeki özel eylemi temsil eden proje öğesine bir kısayol menü öğesi ekleyerek tasarımcıyı özel eylemle ilişkilendirebilirsiniz. Kendi kısayol menüsünü açarak (özel eylem projesi öğesine sağ tıklayıp ya da seçip **SHIFT** + **F10** tuşlarını seçerek) ve sonra **Aç**' ı seçerek tasarımcıyı açabilirsiniz.

 Bu nesne modeli, Visual Studio SDK ile birlikte bulunan bir derlemeler kümesi içinde tanımlanmıştır. Bu nesne modelindeki bazı ana derlemelerden *Microsoft.VisualStudio.Shell.11.0.dll*, *Microsoft.VisualStudio.Shell.Interop.dll* ve *Microsoft.VisualStudio.OLE.Interop.dll* dahildir.

 Tümleştirme nesne modeli hakkında daha fazla bilgi için bkz. [Automation model genel bakış](../extensibility/internals/automation-model-overview.md) ve [Visual Studio SDK başvurusu](../extensibility/visual-studio-sdk-reference.md).

### <a name="sharepoint-object-models"></a>SharePoint nesne modelleri
 SharePoint Araçları uzantıları, SharePoint sitesini değiştirmek veya SharePoint sitesinden veri almak için SharePoint API 'Lerini kullanabilir. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] ve [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] iki farklı nesne modeli sağlar: sunucu nesne modeli ve istemci nesne modeli.

 API 'Leri bir SharePoint Araçları uzantısında herhangi bir nesne modelinde kullanabilirsiniz, ancak her nesne modelinde SharePoint Araçları uzantıları bağlamında bazı avantajlar ve dezavantajları vardır. Daha fazla bilgi için bkz. [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md).

|Nesne modeli|Description|
|------------------|-----------------|
|Sunucu nesne modeli|Sunucu nesne modeli, [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] programlı olarak kullanıma sunulacak tüm özelliklere erişim sağlar [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] . Bu nesne modeli, SharePoint sunucusunda çalışan SharePoint çözümleri tarafından kullanılmak üzere tasarlanmıştır. Bu nesne modelinin çoğunluğu *Microsoft.SharePoint.dll* derlemesinde tanımlanmıştır. Sunucu nesne modeli hakkında daha fazla bilgi için bkz. [SharePoint Foundation Server-Side nesne modelini kullanma](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).|
|İstemci nesne modeli|İstemci nesne modeli, uzak bir istemciden veya sunucudan SharePoint verileriyle birlikte çalışmak için kullanılabilen sunucu nesne modelinin bir alt kümesidir. Ortak görevleri gerçekleştirmek üzere yürütülmesi gereken gidiş dönüş sayısını en aza indirmek için tasarlanmıştır. İstemci nesne modelinin çoğunluğu *Microsoft.SharePoint.Client.dll* ve *Microsoft.SharePoint.Client.Runtime.dll* derlemelerinde tanımlanmıştır. İstemci nesne modeli hakkında daha fazla bilgi için bkz. [yönetilen Istemci nesne modeli](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint araçlarını Visual Studio 'da genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [SharePoint proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md)
