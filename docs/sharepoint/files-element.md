---
title: Files Öğesi | Microsoft Docs
description: Proje öğesi şemasında yer alan bir öğe olan Files SharePoint bilgilerini görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 84c3ab0837680fe815f644d6b0456ce0fe066326
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093235"
---
# <a name="files-element"></a>Dosyalar öğesi
  Özellik öğesi dosyaları ve bağımlı SharePoint olmayan projelerin çıkışı gibi, SharePoint proje öğesiyle dağıtılacak SharePoint belirtir.

## <a name="syntax"></a>Syntax

```xml
<Files>
  <ProjectItemFile.../>
  <ProjectOutputFile.../>
</Files>
```

## <a name="type"></a>Tür
 **FileCollectionType**

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|İsteğe **bağlı ProjectItemFileType** öğesi.<br /><br /> Bu SharePoint proje öğesine dahil etmek için Özellik öğesi dosyası gibi bir dosya SharePoint.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|İsteğe **bağlı ProjectOutputFileType** öğesi.<br /><br /> Bir proje, proje öğesi bir projeye dağıtıldığında dahil etmek için bir projenin çıkışını SharePoint.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Bir proje SharePoint temsil eder. Bu öğe, dosyanın gerekli kök `.spdata` öğesi.|

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Şema adı**|SharePoint Project Öğesi Şeması|
|**Doğrulama dosyası**|ProjectItemModelSchema.xsd|
|**Boş olabilir**|Hayır|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
