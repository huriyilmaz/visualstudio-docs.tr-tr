---
title: ProjectOutputFile Öğesi | Microsoft Docs
description: Proje öğesi XML şema başvurusunda ayrı bir projenin çıkışını temsil eden ProjectOutputFile öğesi SharePoint başvuru bilgilerini alma.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 9a8ecbe4c9214487f1e5d93462bace0af1d58165
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725629"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile öğesi
  Proje öğesi, bir projeye dağıtıldığında dahil etmek için ayrı bir projenin çıkışını SharePoint.

## <a name="syntax"></a>Syntax

```xml
<ProjectOutputFile ProjectId = "GUID of the project"
    ProjectPath = "Relative path of the project"
    Target = "Deployment path of the project output"
    Type = "Type of deployment for the project output" />
```

## <a name="type"></a>Tür
 **ProjectOutputFileType**

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|**ProjectId**|Gerekli **xs:string** özniteliği.<br /><br /> Dahil etmek istediğiniz çıkışı içeren bağımlı projenin GUID'si. Bu, bağımlı proje **dosyasındaki ProjectGuid** öğesine karşılık gelir.|
|**ProjectPath**|Gerekli **xs:string** özniteliği.<br /><br /> Dahil etmek istediğiniz çıktıya sahip bağımlı projenin proje dosya adı dahil göreli yolu. Bu yol, proje öğesini içeren SharePoint projesinin kök SharePoint görelidir.|
|**Hedef**|İsteğe **bağlı xs:string** özniteliği.<br /><br /> Bağımlı proje çıktının dağıtım kök klasörüne göre SharePoint sunucusuna dağıtılacağı yol. Dağıtım kök klasörü, Tür özniteliği tarafından belirtilen dağıtım türü **tarafından** belirlenir.<br /><br /> Daha fazla bilgi için, Çözüm  geliştirme  içinde proje öğelerinin Dağıtım Yolu SharePoint Dağıtım Yolu ve Dağıtım [Kök özellikleri SharePoint bakın.](../sharepoint/developing-sharepoint-solutions.md)|
|**Tür**|Gerekli **xs:string** özniteliği.<br /><br /> Bağımlı projenin çıkışı için kullanmak üzere dağıtım türü. Olası değerler hakkında daha fazla bilgi için, Çözüm geliştirme konusunda proje öğelerinin dağıtım SharePoint [için açıklamaya SharePoint bakın.](../sharepoint/developing-sharepoint-solutions.md) |

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Dosyalar](../sharepoint/files-element.md)|SharePoint proje öğesi SharePoint.|

## <a name="remarks"></a>Açıklamalar
 Proje öğesinin dağıtımına proje çıktısını dahil etmek için **ProjectOutputFile** SharePoint kullanın. Farklı bir proje veya proje öğesini içeren aynı projeyi belirtebilirsiniz. Daha fazla bilgi için [bkz. Proje öğelerinde paketleme ve dağıtım bilgilerini sağlama.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Şema adı**|SharePoint Project Öğe Şeması|
|**Doğrulama dosyası**|ProjectItemModelSchema.xsd|
|**Boş olabilir**|No|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Proje öğelerinde paketleme ve dağıtım bilgilerini sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Yeni SharePoint geliştirme](../sharepoint/developing-sharepoint-solutions.md)
