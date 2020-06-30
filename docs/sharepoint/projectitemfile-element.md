---
title: ProjectItemFile öğesi | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d1c9814498d74a5d1a6533576f1071b4bf7deb57
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539860"
---
# <a name="projectitemfile-element"></a>ProjectItemFile öğesi
  SharePoint 'e dağıtıldığında proje öğesiyle birlikte dahil edilecek özellik öğesi dosyası gibi bir SharePoint dosyasını temsil eder.

## <a name="syntax"></a>Syntax

```xml
<ProjectItemFile Source = "Name of the file"
    Target = "Deployment path of the file"
    Type = "Type of deployment for the file" />
```

## <a name="type"></a>Tür
 **ProjectItemFileType**

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|**Kaynak**|Gerekli **xs: String** özniteliği.<br /><br /> Proje öğesiyle dağıtılacak dosyanın adı.|
|**Hedef**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> Dosyanın SharePoint 'te dağıtım kök klasörüne göre dağıtılacağı yol. Dağıtım kök klasörü, **tür** özniteliği tarafından belirtilen dağıtım türü tarafından belirlenir. **Hedef** özniteliği belirtilmemişse, dosya **kaynak** özniteliğinde belirtilen adı taşıyan bir klasöre dağıtılır.<br /><br /> Daha fazla bilgi için [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)bölümünde SharePoint proje öğelerinin **dağıtım yolu** ve **dağıtım kök** özellikleri için açıklamalara bakın.|
|**Tür**|Gerekli **xs: String** özniteliği.<br /><br /> Dosya için dağıtım türü. Olası değerler hakkında daha fazla bilgi için SharePoint [çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)bölümünde SharePoint proje öğelerinin **dağıtım türü** özelliğinin açıklamasına bakın.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Description|
|-------------|-----------------|
|[Dosyalar](../sharepoint/files-element.md)|SharePoint 'e dağıtıldığında SharePoint proje öğesiyle birlikte içerilecek dosyaları belirtir.|

## <a name="remarks"></a>Açıklamalar
 **ProjectItemFile** öğelerinde genellikle başvurulan SharePoint dosyaları, özellik öğesi dosyalarını (*Elements.xml*), liste tanımları için şema dosyalarını (*Schema.xml*) ve Web bölümleri (*. WebPart*) için Web Bölümü tanım dosyalarını içerir.

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/Sharepointprojectıtemmodel|
|**Şema adı**|SharePoint proje öğesi şeması|
|**Doğrulama dosyası**|Projectıtemmodelschema. xsd|
|**Boş olabilir**|No|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
