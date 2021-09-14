---
title: FeatureProperty Öğesi | Microsoft Docs
description: Proje öğesi şemasında yer alan bir öğe olan FeatureProperty öğesi SharePoint başvuru bilgilerini görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 01536094bdb9fd084b32ce56429d085f5f377f8f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625215"
---
# <a name="featureproperty-element"></a>FeatureProperty öğesi
  Özel bir özel özelliği, özel bir özel durum için dağıtıldığında bir Özellik'e dahil SharePoint. Bir Özellik dağıtıldıktan sonra kodundaki özelliğine erişebilirsiniz.

## <a name="syntax"></a>Syntax

```xml
<FeatureProperty Key = "Key of the property value"
    Value = "Property value" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|**Key**|Gerekli **xs:string** özniteliği.<br /><br /> Özellik değerini depolamak ve almak için kullanılan anahtar. Her özelliğin Özellik içinde benzersiz bir anahtarı olmalıdır.|
|**Değer**|Gerekli **xs:string** özniteliği.<br /><br /> Özellik değeri.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Özelliğin bir özelliğine dağıtıldığında dahil edilen özellik değerlerinin bir koleksiyonunu temsil SharePoint.|

## <a name="remarks"></a>Açıklamalar
 Özellik özellikleri hakkında daha fazla bilgi için [bkz. Proje öğelerinde paket ve dağıtım bilgileri sağlama.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Şema adı**|SharePoint Project Öğe Şeması|
|**Doğrulama dosyası**|ProjectItemModelSchema.xsd|
|**Boş olabilir**|No|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Proje öğelerinde paketleme ve dağıtım bilgilerini sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
