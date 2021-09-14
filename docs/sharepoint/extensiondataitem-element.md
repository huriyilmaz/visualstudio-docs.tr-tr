---
title: ExtensionDataItem Öğesi | Microsoft Docs
description: Proje öğesi şemasında yer alan bir öğe olan ExtensionDataItem öğesi SharePoint başvuru bilgilerini görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: b99d9a267b8fb18ec8e238191382d71f558fc3d3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625251"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem öğesi
  Anahtar/değer biçiminde bir proje SharePoint özel veri öğesi. Hem anahtar hem de değer dizeler olmalı.

## <a name="syntax"></a>Syntax

```xml
<ExtensionDataItem Key = "Key of the data item"
    Value = "Value of the data item" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|**Key**|Gerekli **xs: dize** özniteliği.<br /><br /> Veri öğesini depolamak ve almak için kullanılan anahtar.|
|**Değer**|Gerekli **xs:string** özniteliği.<br /><br /> Veri öğesinin değeri.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Proje öğesiyle ilişkili özel veri öğeleri koleksiyonunu SharePoint temsil eder.|

## <a name="remarks"></a>Açıklamalar
 Bir nesnenin özelliğini kullanarak SharePoint özel verileri bir SharePoint proje öğesiyle ilişkilendirmek, Visual Studio proje öğesi için dosyada yeni <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> bir **ExtensionDataItem** öğesine `.spdata` kaydeder. Daha fazla bilgi için [bkz. Verileri proje sisteminin SharePoint kaydetme.](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Şema adı**|SharePoint Project Öğe Şeması|
|**Doğrulama dosyası**|ProjectItemModelSchema.xsd|
|**Boş olabilir**|No|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
