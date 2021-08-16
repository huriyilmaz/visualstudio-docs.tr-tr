---
title: ProjectItem Öğesi | Microsoft Docs
description: Proje öğesi XML şema başvurusunda bir proje SharePoint temsil eden ProjectItem öğesi SharePoint başvuru bilgilerini elde edin.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: da3645e6d8a0f8ae7568aa1e68a3ccf114a4f96f56bb25350a26f6c0dd0b7931
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367479"
---
# <a name="projectitem-element"></a>ProjectItem öğesi
  Bir proje SharePoint temsil eder. Bu öğe . spdata dosyasının *gerekli kök öğesi.*

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
|**DefaultFile**|İsteğe **bağlı xs: dize** özniteliği.<br /><br /> dosya adı da dahil olmak üzere, dosyanın dosya adını Visual Studio proje öğesini SharePoint düzenleyicide **Çözüm Gezgini.** Yol, *.spdata* dosyasını içeren klasörden görelidir.|
|**FeatureReceiverClass**|İsteğe **bağlı xs:string** özniteliği.<br /><br /> Bu proje öğesi için bir özellik alıcı sınıfının tam SharePoint adı. Özellik alıcıları hakkında daha fazla bilgi için [bkz. Proje öğelerinde paketleme ve dağıtım bilgilerini sağlama.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|
|**FeatureReceiverAssembly**|İsteğe **bağlı xs:string** özniteliği.<br /><br /> Bu proje öğesi için bir özellik alıcı tanımlayan derlemenin tam adını SharePoint belirtir. Özellik alıcıları hakkında daha fazla bilgi için [bkz. Proje öğelerinde paketleme ve dağıtım bilgilerini sağlama.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) Tam derleme adları hakkında daha fazla bilgi için bkz. [Derleme Adları.](/dotnet/framework/app-domains/assembly-names)|
|**SupportedTrustLevels**|İsteğe **bağlı xs:string** özniteliği.<br /><br /> Bu proje öğesinin desteklediği SharePoint düzeylerini belirtir. Bu değer şu dizelerden biri olabilir: Sandboxed, FullTrust veya All. All değeri hem Korumalı Alanlı'yi hem de FullTrust'i belirtir.<br /><br /> Özel bir SharePoint öğe türünde, bu özniteliğin değeri yöntemi uygulamanıza özelliğine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> atadığınız değere <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> karşılık gelen değerdir. Bu öznitelik için farklı bir değer belirtir Visual Studio, özelliğinde belirttiğiniz güven düzeyini belirtmek için değerin üzerine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> yazmaz.|
|**Supporteddeploymentscopes**|İsteğe **bağlı xs:string** özniteliği.<br /><br /> Bu proje öğesinin desteklediği dağıtım SharePoint belirtir. Bu değer, şu dizelerden birini veya daha fazlasını içeren virgülle ayrılmış bir dizedir: Grup, Site, Web, WebApplication veya Package. Örnek: `Web, Site`<br /><br /> Özel bir SharePoint öğe türünde, bu özniteliğin değeri yöntemi uygulamanıza özelliğine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> atadığınız değere <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> karşılık gelen değerdir. Bu öznitelik için farklı bir değer belirtir Visual Studio, özelliğinde belirttiğiniz güven düzeyini belirtmek için değerin üzerine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> yazmaz.|
|**Tür**|Gerekli **xs:string** özniteliği.<br /><br /> Proje öğesinin SharePoint tanımlayıcısı. Özel bir SharePoint öğesi türünde tanımlayıcı, değerine geçişin <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> dizesidir. Daha fazla bilgi için [bkz. Nasıl kullanılır: Proje SharePoint türü tanımlama.](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)<br /><br /> Visual Studio'a dahil edilen yerleşik SharePoint proje öğelerinin tanımlayıcılarının listesi için bkz. SharePoint [proje öğelerini genişletme.](../sharepoint/extending-sharepoint-project-items.md)|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|İsteğe bağlı öğe.<br /><br /> Proje öğesiyle ilişkili özel veri öğeleri koleksiyonunu SharePoint temsil eder.<br /><br /> Yalnızca bir **ExtensionData öğesi** dahilebilirsiniz.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|İsteğe bağlı öğe.<br /><br /> Bir Özellik,özel bir özel durum için dağıtıldığında dahil edilen özellik değerleri koleksiyonunu SharePoint.<br /><br /> Yalnızca bir **FeatureProperties öğesi** dahil olabilir.|
|[Dosyalar](../sharepoint/files-element.md)|İsteğe **bağlı FileCollectionType** öğesi.<br /><br /> Özellik öğesi dosyaları ve bağımlı SharePoint olmayan projelerin çıkışı gibi, SharePoint proje öğesiyle dağıtılacak SharePoint belirtir.<br /><br /> Bir Files **veya** **ProjectItemFolder öğesi** dahil ancak ikisini birden dahil etmek değil.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|İsteğe **bağlı ProjectItemFolderType** öğesi.<br /><br /> Eşlenmiş bir klasörü temsil eder.<br /><br /> Bir Files **veya** **ProjectItemFolder öğesi** dahil ancak ikisini birden dahil etmek değil.|
|[SafeControls](../sharepoint/safecontrols-element.md)|İsteğe bağlı öğe.<br /><br /> ASPX denetimleri koleksiyonunu temsil eder ve Web Bölümleri kullanıcının sitenin herhangi bir ASPX sayfasından erişmesi için güvenli olarak belirlenen SharePoint temsil eder.<br /><br /> Yalnızca bir **SafeControls öğesi** dahil olabilir.|

### <a name="parent-elements"></a>Üst öğeler
 Yok.

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Şema adı**|SharePoint Project Öğesi Şeması|
|**Doğrulama dosyası**|ProjectItemModelSchema.xsd|
|**Boş olabilir**|Hayır|

## <a name="see-also"></a>Ayrıca bkz.
[SharePoint öğesi şema çıkarlığı](../sharepoint/sharepoint-project-item-schema-reference.md)
