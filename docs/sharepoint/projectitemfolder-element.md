---
title: ProjectItemFolder öğesi | Microsoft Docs
description: SharePoint proje öğesi XML şeması başvurusunda eşlenen bir klasörü temsil eden projectıtemfolder öğesi hakkında başvuru bilgileri alın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 3873a4cbf50d216f3574c2ef8ce90255d3eb5d7b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725631"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder öğesi
  Eşlenmiş bir klasörü temsil eder.

## <a name="syntax"></a>Syntax

```xml
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"
    Type = "Type of deployment for the mapped folder" />
```

## <a name="type"></a>Tür
 **ProjectItemFolderType**

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|**Hedef**|Gerekli **xs: String** özniteliği.<br /><br /> SharePoint yüklemesinde, eşlenen klasörün dağıtım kök klasörüne göre karşılık geldiği klasörün yolu. Dağıtım kök klasörü, **tür** özniteliği tarafından belirtilen dağıtım türü tarafından belirlenir.<br /><br /> daha fazla bilgi için, [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)bölümünde SharePoint proje öğelerinin **dağıtım yolu** ve **dağıtım kök** özellikleri için açıklamalara bakın.|
|**Tür**|Gerekli **xs: String** özniteliği.<br /><br /> Eşlenen klasör için dağıtım türü. olası değerler hakkında daha fazla bilgi için bkz. [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)içindeki SharePoint proje öğelerinin **dağıtım türü** özelliği için açıklama.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|bir SharePoint proje öğesini temsil eder. Bu öğe, *. spdata* dosyasının gerekli kök öğesidir.|

## <a name="remarks"></a>Açıklamalar
 Eşlenen klasörler hakkında daha fazla bilgi için bkz. [nasıl yapılır: eşlenmiş klasör ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-mapped-folders.md).

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.Microsoft.com/VisualStudio/2010/<br>SharePointTools/Sharepointprojectıtemmodel|
|**Şema adı**|SharePoint Project öğesi şeması|
|**Doğrulama dosyası**|Projectıtemmodelschema. xsd|
|**Boş olabilir**|No|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Nasıl yapılır: eşlenmiş klasörler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-mapped-folders.md)
