---
title: ProjectItemFolder öğesi | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38f8f70cc6480554441809e33c4083735600fbbb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539821"
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
|**Hedef**|Gerekli **xs: String** özniteliği.<br /><br /> SharePoint yüklemesinde, eşlenen klasörün dağıtım kök klasörüne göre karşılık geldiği klasörün yolu. Dağıtım kök klasörü, **tür** özniteliği tarafından belirtilen dağıtım türü tarafından belirlenir.<br /><br /> Daha fazla bilgi için [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)bölümünde SharePoint proje öğelerinin **dağıtım yolu** ve **dağıtım kök** özellikleri için açıklamalara bakın.|
|**Tür**|Gerekli **xs: String** özniteliği.<br /><br /> Eşlenen klasör için dağıtım türü. Olası değerler hakkında daha fazla bilgi için SharePoint [çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)bölümünde SharePoint proje öğelerinin **dağıtım türü** özelliğinin açıklamasına bakın.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Bir SharePoint proje öğesini temsil eder. Bu öğe, *. spdata* dosyasının gerekli kök öğesidir.|

## <a name="remarks"></a>Açıklamalar
 Eşlenen klasörler hakkında daha fazla bilgi için bkz. [nasıl yapılır: eşlenmiş klasör ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-mapped-folders.md).

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.Microsoft.com/VisualStudio/2010/<br>SharePointTools/Sharepointprojectıtemmodel|
|**Şema adı**|SharePoint proje öğesi şeması|
|**Doğrulama dosyası**|Projectıtemmodelschema. xsd|
|**Boş olabilir**|No|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Nasıl yapılır: eşlenmiş klasörler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-mapped-folders.md)
