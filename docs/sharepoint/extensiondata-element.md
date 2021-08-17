---
title: ExtensionData Öğesi | Microsoft Docs
description: Yeni proje öğesi şemasında bir öğe olan ExtensionData öğesi SharePoint bilgilerini görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: f175c0b4cdc4a9b5fb9537821d2ffcc646d44bf14119a132d7561439e92f5e6a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425381"
---
# <a name="extensiondata-element"></a>ExtensionData öğesi
  Proje öğesiyle ilişkili özel veri öğeleri koleksiyonunu SharePoint temsil eder.

## <a name="syntax"></a>Syntax

```xml
<ExtensionData>
  <ExtensionDataItem.../>
</ExtensionData>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|İsteğe bağlı öğe.<br /><br /> Anahtar/değer biçiminde bir proje öğesiyle SharePoint özel bir veri öğesini temsil eder. Hem anahtar hem de değer dizeler olmalı.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Bir proje SharePoint temsil eder. Bu öğe, dosyanın gerekli kök `.spdata` öğesi.|

## <a name="remarks"></a>Açıklamalar
 Bir nesnenin özelliğini kullanarak SharePoint bir proje öğesiyle özel verileri Visual Studio, verileri proje öğesi için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> **dosyasındaki ExtensionData** öğesine `.spdata` kaydeder. Daha fazla bilgi için [bkz. Verileri proje sisteminin SharePoint kaydetme.](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Şema adı**|SharePoint Project Öğesi Şeması|
|**Doğrulama dosyası**|ProjectItemModelSchema.xsd|
|**Boş olabilir**|Hayır|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
