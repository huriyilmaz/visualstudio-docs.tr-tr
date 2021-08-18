---
title: SafeControl Öğesi | Microsoft Docs
description: Bir kullanıcının bir sitenin ASPX sayfasından erişmesi için güvenli olarak işaretlenmiş bir ASPX denetimi veya web bölümünü temsil eden SafeControl SharePoint bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: cdcd591ff2e742296a23fdf9dfa1d6324bf1e1bf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092832"
---
# <a name="safecontrol-element"></a>SafeControl öğesi
  Herhangi bir kullanıcının sitenin herhangi bir ASPX sayfasından erişmesi için güvenli olarak belirlenen bir ASPX SharePoint temsil eder.

## <a name="syntax"></a>Syntax

```xml
<SafeControl Assembly = "Name of assembly that contains the safe control"
    IsSafe = "true/false"
    IsSafeAgainstScript = "true/false"
    Name = "Name of this safe control entry"
    Namespace = "Namespace of the safe control"
    TypeName = "Type of the safe control" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|**Bütünleştirilmiş Kod**|İsteğe **bağlı xs:string** özniteliği.<br /><br /> ASPX denetimi veya Web Bölümü tanımlandığı derlemenin adı. Varsayılan olarak, bu öznitelik **$SharePoint.Project. Derleme adı için AssemblyFullName$** değiştirilebilir parametresi. Daha fazla bilgi için [bkz. Değiştirilebilir parametreler.](../sharepoint/replaceable-parameters.md)|
|**IsSafe**|İsteğe **bağlı xs:boole özniteliği.**<br /><br /> Güvenilmeyen kullanıcıların erişmesi için ASPX denetimi veya Web Bölümü'nin güvenli olup olmadığını belirtir.|
|**IsSafeAgainstScript**|İsteğe **bağlı xs:boole özniteliği.**<br /><br /> Güvenilmeyen kullanıcıların ASPX denetimi veya Web Bölümü özelliklerini görüntüleyemez veya düzenleyemezlerini belirtir.|
|**Ad**|İsteğe **bağlı xs:string** özniteliği.<br /><br /> Koleksiyonda bu güvenli denetim girişinin adı.|
|**Ad Alanı**|İsteğe **bağlı xs:string** özniteliği.<br /><br /> ASPX denetimi veya Web Bölümü ad alanı.|
|**Typename**|İsteğe **bağlı xs:string** özniteliği.<br /><br /> ASPX denetimi veya Web Bölümü türü adı.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[SafeControls](../sharepoint/safecontrols-element.md)|ASPX denetimleri koleksiyonunu temsil eder ve Web Bölümleri kullanıcının SharePoint sitesinde herhangi bir ASPX sayfasına erişmesi için güvenli olarak belirlenmiştir.|

## <a name="remarks"></a>Açıklamalar
 Güvenli denetimler hakkında daha fazla bilgi için [bkz. Proje öğelerinde paketleme ve dağıtım bilgileri sağlama.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Şema adı**|SharePoint Project Öğesi Şeması|
|**Doğrulama dosyası**|ProjectItemModelSchema.xsd|
|**Boş olabilir**|Hayır|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Proje öğelerinde paketleme ve dağıtım bilgilerini sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
