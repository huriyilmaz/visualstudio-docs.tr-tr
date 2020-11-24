---
title: ProjectOutputFile öğesi | Microsoft Docs
description: SharePoint proje öğesi XML şeması başvurusunda ayrı bir projenin çıkışını temsil eden ProjectOutputFile öğesi hakkında başvuru bilgileri alın.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ffe6f95bdfd7795c837aaaa25ec7ef2a35a7ae76
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442035"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile öğesi
  SharePoint 'e dağıtıldığında proje öğesiyle birlikte dahil edilecek ayrı bir projenin çıkışını temsil eder.

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
|**ProjectId**|Gerekli **xs: String** özniteliği.<br /><br /> Dahil etmek istediğiniz çıktıyı içeren bağımlı projenin GUID 'SI. Bu, bağımlı proje dosyasındaki **ProjectGuid** öğesine karşılık gelir.|
|**ProjectPath**|Gerekli **xs: String** özniteliği.<br /><br /> Dahil etmek istediğiniz çıktıyı içeren bağımlı projenin proje dosyası adı da dahil olmak üzere göreli yol. Bu yol, SharePoint proje öğesini içeren SharePoint projesinin kök klasörüne görelidir.|
|**Hedef**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> Bağımlı proje çıkışının, dağıtım kök klasörüne göre SharePoint sunucusunda dağıtılacağı yol. Dağıtım kök klasörü, **tür** özniteliği tarafından belirtilen dağıtım türü tarafından belirlenir.<br /><br /> Daha fazla bilgi için [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)bölümünde SharePoint proje öğelerinin **dağıtım yolu** ve **dağıtım kök** özellikleri için açıklamalara bakın.|
|**Tür**|Gerekli **xs: String** özniteliği.<br /><br /> Bağımlı projenin çıktısı için kullanılacak dağıtımın türü. Olası değerler hakkında daha fazla bilgi için SharePoint [çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)bölümünde SharePoint proje öğelerinin **dağıtım türü** özelliğinin açıklamasına bakın.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Dosyalar](../sharepoint/files-element.md)|SharePoint 'e dağıtıldığında SharePoint proje öğesiyle birlikte içerilecek dosyaları belirtir.|

## <a name="remarks"></a>Açıklamalar
 Bir projenin çıkışını SharePoint proje öğesinin dağıtımına dahil etmek için **ProjectOutputFile** öğesini kullanın. Farklı bir proje veya proje öğesini içeren aynı proje belirtebilirsiniz. Daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgilerini sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Uzayına**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/Sharepointprojectıtemmodel|
|**Şema adı**|SharePoint proje öğesi şeması|
|**Doğrulama dosyası**|Projectıtemmodelschema. xsd|
|**Boş olabilir**|Hayır|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
