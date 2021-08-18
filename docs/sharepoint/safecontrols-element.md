---
title: SafeControls öğesi | Microsoft Docs
description: bir SharePoint sitesinin aspx sayfasında erişim için güvenli olarak işaretlenmiş bir ASPX denetimleri veya web bölümleri koleksiyonu tutan safecontrols öğesi hakkında bilgi alın.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092793"
---
# <a name="safecontrols-element"></a>SafeControls öğesi
  herhangi bir kullanıcının SharePoint sitesindeki herhangi bir aspx sayfasına erişmesi için güvenli olarak belirlenmiş bir aspx denetimleri ve Web Bölümleri koleksiyonu.

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
|[SafeControl](../sharepoint/safecontrol-element.md)|İsteğe bağlı öğe.<br /><br /> tüm kullanıcıların SharePoint sitesindeki herhangi bir aspx sayfasına erişmesi için güvenli olarak belirlenmiş bir aspx denetimi veya Web bölümü temsil eder.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|bir SharePoint proje öğesini temsil eder. Bu öğe *. spdata* dosyasının gerekli kök öğesi.|

## <a name="remarks"></a>Açıklamalar
 Güvenli denetimler hakkında daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgilerini sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/Sharepointprojectıtemmodel|
|**Şema adı**|SharePoint Project öğesi şeması|
|**Doğrulama dosyası**|Projectıtemmodelschema. xsd|
|**Boş olabilir**|Hayır|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
