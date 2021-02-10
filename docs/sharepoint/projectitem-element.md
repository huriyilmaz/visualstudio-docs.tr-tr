---
title: ProjectItem öğesi | Microsoft Docs
description: SharePoint proje öğesi XML şema başvurusunda bir SharePoint proje öğesini temsil eden ProjectItem öğesi hakkında başvuru bilgileri alın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2b94b44bfa442805c4c785a48c9f60f56eb8e002
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950594"
---
# <a name="projectitem-element"></a>ProjectItem öğesi
  Bir SharePoint proje öğesini temsil eder. Bu öğe *. spdata* dosyasının gerekli kök öğesi.

## <a name="syntax"></a>Syntax

```xml
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"
    SupportedTrustLevels = "Trust levels that the project item supports"
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"
    Type="Identifier for the project item">
  <Files>...</Files>
  <ProjectItemFolder>...</ProjectItemFolder>
  <SafeControls>...</SafeControls>
  <FeatureProperties>...</FeatureProperties>
  <ExtensionData>...</ExtensionData>
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|**DefaultFile**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> **Çözüm Gezgini**' de SharePoint proje öğesini açtığınızda, Visual Studio Düzenleyicisi 'nde açılan dosyanın dosya adı da dahil olmak üzere göreli yol. Yol, *. spdata* dosyasını içeren klasörden görelidir.|
|**FeatureReceiverClass**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> Bu SharePoint proje öğesi için bir özellik alıcısı sınıfının tam adı. Özellik alıcıları hakkında daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgilerini sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|**FeatureReceiverAssembly**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> Bu SharePoint proje öğesi için bir özellik alıcısı tanımlayan bir derlemenin tam adını belirtir. Özellik alıcıları hakkında daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgilerini sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Tam derleme adları hakkında daha fazla bilgi için bkz. [derleme adları](/dotnet/framework/app-domains/assembly-names).|
|**SupportedTrustLevels**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> Bu SharePoint proje öğesinin desteklediği güven düzeylerini belirtir. Bu değer şu dizelerden biri olabilir: korumalı, FullTrust veya ALL. All değeri hem korumalı hem de FullTrust belirler.<br /><br /> Özel bir SharePoint proje öğesi türünde, bu özniteliğin değeri, yöntemi uygulamanızda özelliği atadığınız değere karşılık gelir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> . Bu öznitelik için farklı bir değer belirtirseniz, Visual Studio, özellikte belirttiğiniz güven düzeyini belirtecek şekilde değerin üzerine yazar <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> .|
|**SupportedDeploymentScopes**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> Bu SharePoint proje öğesinin desteklediği dağıtım kapsamlarını belirtir. Bu değer, şu dizelerden birini veya daha fazlasını içeren, virgülle ayrılmış bir dizedir: Farm, site, Web, WebApplication veya Package. Örnek: `Web, Site`<br /><br /> Özel bir SharePoint proje öğesi türünde, bu özniteliğin değeri, yöntemi uygulamanızda özelliği atadığınız değere karşılık gelir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> . Bu öznitelik için farklı bir değer belirtirseniz, Visual Studio, özellikte belirttiğiniz güven düzeyini belirtecek şekilde değerin üzerine yazar <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> .|
|**Tür**|Gerekli **xs: String** özniteliği.<br /><br /> SharePoint proje öğesi için tanımlayıcı. Özel bir SharePoint proje öğesi türünde, tanımlayıcı öğesine geçirdiğiniz dizedir <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Visual Studio 'Ya dahil olan yerleşik SharePoint proje öğeleri için tanımlayıcıların listesi için bkz. [SharePoint proje öğelerini genişletme](../sharepoint/extending-sharepoint-project-items.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|İsteğe bağlı öğe.<br /><br /> SharePoint proje öğesiyle ilişkili özel veri öğelerinin koleksiyonunu temsil eder.<br /><br /> Yalnızca bir **ExtensionData** öğesi dahil edebilirsiniz.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|İsteğe bağlı öğe.<br /><br /> SharePoint 'e dağıtıldığında bir özelliğe dahil olan özellik değerlerinin koleksiyonunu temsil eder.<br /><br /> Yalnızca bir **FeatureProperties** öğesi ekleyebilirsiniz.|
|[Dosyalar](../sharepoint/files-element.md)|İsteğe bağlı **FileCollectionType** öğesi.<br /><br /> Özellik öğesi dosyaları ve bağımlı SharePoint olmayan projelerin çıktısı gibi SharePoint proje öğesiyle dağıtılacak dosyaları belirtir.<br /><br /> Bir **Dosya** ya da **ProjectItemFolder** öğesi ekleyin, ancak ikisini birden kullanmayın.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|İsteğe bağlı **ProjectItemFolderType** öğesi.<br /><br /> Eşlenmiş bir klasörü temsil eder.<br /><br /> Bir **Dosya** ya da **ProjectItemFolder** öğesi ekleyin, ancak ikisini birden kullanmayın.|
|[SafeControls](../sharepoint/safecontrols-element.md)|İsteğe bağlı öğe.<br /><br /> Herhangi bir kullanıcının SharePoint sitesindeki herhangi bir ASPX sayfasına erişmesi için güvenli olarak belirlenmiş bir ASPX denetimleri ve Web Bölümleri koleksiyonunu temsil eder.<br /><br /> Yalnızca bir **SafeControls** öğesi dahil edebilirsiniz.|

### <a name="parent-elements"></a>Üst öğeler
 Yok.

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/Sharepointprojectıtemmodel|
|**Şema adı**|SharePoint proje öğesi şeması|
|**Doğrulama dosyası**|Projectıtemmodelschema. xsd|
|**Boş olabilir**|Hayır|

## <a name="see-also"></a>Ayrıca bkz.
[SharePoint proje öğesi şeması rseference](../sharepoint/sharepoint-project-item-schema-reference.md)
