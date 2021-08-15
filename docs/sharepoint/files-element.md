---
title: Files Öğesi | Microsoft Docs
description: Proje öğesi şemasında yer alan bir öğe olan Files öğesi SharePoint başvuru bilgilerini görüntüleme.
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
ms.openlocfilehash: 54344e98aaa8982143fd595ac7e6fb4245905c4ee9645953af889fafe15dde80
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121269190"
---
# <a name="files-element"></a>Dosyalar öğesi
  Özellik öğesi dosyaları ve bağımlı olmayan SharePoint projelerinin çıkışı gibi bir proje öğesiyle dağıtılacak SharePoint belirtir.

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
