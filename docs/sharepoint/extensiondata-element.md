---
title: ExtensionData öğesi | Microsoft Docs
description: SharePoint proje öğesi şemasındaki bir öğe olan extensiondata öğesiyle ilgili başvuru bilgilerini görüntüleyin.
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
ms.openlocfilehash: ec317073601f766dab2042ab6c77542914e87b59
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625256"
---
# <a name="extensiondata-element"></a>ExtensionData öğesi
  SharePoint proje öğesiyle ilişkili özel veri öğeleri koleksiyonunu temsil eder.

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
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|İsteğe bağlı öğe.<br /><br /> anahtar/değer biçiminde SharePoint proje öğesiyle ilişkili özel bir veri öğesini temsil eder. Anahtar ve değer dizeler olmalıdır.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|bir SharePoint proje öğesini temsil eder. Bu öğe, dosyanın gerekli kök öğesi `.spdata` .|

## <a name="remarks"></a>Açıklamalar
 bir nesnenin özelliğini kullanarak özel verileri bir SharePoint proje öğesiyle ilişkilendirdiğinizde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> , Visual Studio verileri proje öğesi için dosyadaki **extensiondata** öğesine kaydeder `.spdata` . daha fazla bilgi için bkz. [SharePoint proje sisteminin uzantılarında verileri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/Sharepointprojectıtemmodel|
|**Şema adı**|SharePoint Project öğesi şeması|
|**Doğrulama dosyası**|Projectıtemmodelschema. xsd|
|**Boş olabilir**|No|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
