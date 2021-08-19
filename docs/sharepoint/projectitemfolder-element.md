---
title: ProjectItemFolder Öğesi | Microsoft Docs
description: Proje öğesi XML şema başvurusunda eşlenmiş bir klasörü temsil eden ProjectItemFolder SharePoint başvuru bilgilerini elde edin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084135"
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
|**Hedef**|Gerekli **xs: dize** özniteliği.<br /><br /> Eşlenen klasörün dağıtım kök SharePoint karşılık gelen yüklemesinde klasörün yolu. Dağıtım kök klasörü, Tür özniteliği tarafından belirtilen dağıtım türü **tarafından** belirlenir.<br /><br /> Daha fazla bilgi için, Çözüm  geliştirme  içinde proje öğelerinin Dağıtım Yolu SharePoint Dağıtım Yolu ve Dağıtım [Kök özellikleri SharePoint bakın.](../sharepoint/developing-sharepoint-solutions.md)|
|**Tür**|Gerekli **xs:string** özniteliği.<br /><br /> Eşlenen klasör için dağıtım türü. Olası değerler hakkında daha fazla bilgi için, Çözüm geliştirme konusunda proje öğelerinin SharePoint Dağıtım Türü  [özelliğinin SharePoint bakın.](../sharepoint/developing-sharepoint-solutions.md)|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Bir proje SharePoint temsil eder. Bu öğe, *.spdata* dosyasının gerekli kök öğesidir.|

## <a name="remarks"></a>Açıklamalar
 Eşlenen klasörler hakkında daha fazla bilgi için [bkz. Nasıl 2.](../sharepoint/how-to-add-and-remove-mapped-folders.md)

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|
|**Şema adı**|SharePoint Project Öğesi Şeması|
|**Doğrulama dosyası**|ProjectItemModelSchema.xsd|
|**Boş olabilir**|Hayır|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Nasıl: Eşlenmiş klasörler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-mapped-folders.md)
