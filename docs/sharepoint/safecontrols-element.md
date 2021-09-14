---
title: SafeControls Öğesi | Microsoft Docs
description: Bir sitenin ASPX sayfasında erişim için güvenli olarak işaretlenmiş ASPX denetimleri veya web bölümleri koleksiyonunu tutan SafeControls SharePoint bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 063da0761f15c1a3b39468a810fd5d3055cece62
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635569"
---
# <a name="safecontrols-element"></a>SafeControls öğesi
  Herhangi bir kullanıcının Web Bölümleri sitenin aspx sayfasından erişmesi için güvenli olarak belirlenen ASPX denetimleri ve SharePoint koleksiyonu.

## <a name="syntax"></a>Syntax

```xml
<SafeControls>
  <SafeControl.../>
</SafeControls>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[SafeControl](../sharepoint/safecontrol-element.md)|İsteğe bağlı öğe.<br /><br /> Herhangi bir kullanıcının sitenin herhangi bir ASPX sayfasından erişmesi için güvenli olarak belirlenen bir ASPX SharePoint temsil eder.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Bir proje SharePoint temsil eder. Bu öğe . spdata dosyasının *gerekli kök öğesi.*|

## <a name="remarks"></a>Açıklamalar
 Güvenli denetimler hakkında daha fazla bilgi için [bkz. Proje öğelerinde paketleme ve dağıtım bilgileri sağlama.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)

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
