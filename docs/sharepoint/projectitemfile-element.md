---
title: ProjectItemFile öğesi | Microsoft Docs
description: SharePoint proje öğesi XML şeması başvurusunda bir proje öğesi dosyasını temsil eden projectıtemfile öğesi hakkında başvuru bilgileri alın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 065bb202420549462597ccea7cece0a3c3485c4b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135851"
---
# <a name="projectitemfile-element"></a>ProjectItemFile öğesi
  SharePoint öğesine dağıtıldığında proje öğesi dahil olmak üzere özellik öğesi dosyası gibi bir SharePoint dosyasını temsil eder.

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
|**Hedef**|İsteğe bağlı **xs: String** özniteliği.<br /><br /> dosyanın dağıtım kök klasörüne göre SharePoint dağıtılacağı yol. Dağıtım kök klasörü, **tür** özniteliği tarafından belirtilen dağıtım türü tarafından belirlenir. **Hedef** özniteliği belirtilmemişse, dosya **kaynak** özniteliğinde belirtilen adı taşıyan bir klasöre dağıtılır.<br /><br /> daha fazla bilgi için, [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)bölümünde SharePoint proje öğelerinin **dağıtım yolu** ve **dağıtım kök** özellikleri için açıklamalara bakın.|
|**Tür**|Gerekli **xs: String** özniteliği.<br /><br /> Dosya için dağıtım türü. olası değerler hakkında daha fazla bilgi için bkz. [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)içindeki SharePoint proje öğelerinin **dağıtım türü** özelliği için açıklama.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Dosyalar](../sharepoint/files-element.md)|SharePoint 'ye dağıtıldığında SharePoint proje öğesiyle birlikte içerilecek dosyaları belirtir.|

## <a name="remarks"></a>Açıklamalar
 **projectıtemfile** öğelerinde genellikle başvurulan SharePoint dosyalara özellik öğesi dosyaları (*Elements.xml*), liste tanımları için şema dosyaları (*Schema.xml*) ve Web Bölümleri (*. webpart*) için Web bölümü tanım dosyaları dahildir.

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/Sharepointprojectıtemmodel|
|**Şema adı**|SharePoint Project öğesi şeması|
|**Doğrulama dosyası**|Projectıtemmodelschema. xsd|
|**Boş olabilir**|Hayır|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
