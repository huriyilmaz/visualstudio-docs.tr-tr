---
title: ExtensionDataItem öğesi | Microsoft Docs
description: SharePoint proje öğesi şemasındaki bir öğe olan ExtensionDataItem öğesi hakkında başvuru bilgilerini görüntüleyin.
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
ms.workload:
- office
ms.openlocfilehash: add1a119283635f9cfd9bebddfe18228f1976703
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876829"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem öğesi
  Anahtar/değer biçiminde SharePoint proje öğesiyle ilişkili özel bir veri öğesi. Anahtar ve değer dizeler olmalıdır.

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
|**Key**|Gerekli **xs: String** özniteliği.<br /><br /> Veri öğesini depolamak ve almak için kullanılan anahtar.|
|**Değer**|Gerekli **xs: String** özniteliği.<br /><br /> Veri öğesinin değeri.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|SharePoint proje öğesiyle ilişkili özel veri öğelerinin koleksiyonunu temsil eder.|

## <a name="remarks"></a>Açıklamalar
 Bir nesnenin özelliğini kullanarak özel verileri bir SharePoint proje öğesiyle ilişkilendirdiğinizde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> , Visual Studio verileri proje öğesi için dosyadaki yeni bir **ExtensionDataItem** öğesine kaydeder `.spdata` . Daha fazla bilgi için bkz. [SharePoint proje sisteminin uzantılarında verileri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Öğe bilgileri

|Özellik|Değer|
|-|-|
|**Ad Alanı**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/Sharepointprojectıtemmodel|
|**Şema adı**|SharePoint proje öğesi şeması|
|**Doğrulama dosyası**|Projectıtemmodelschema. xsd|
|**Boş olabilir**|Hayır|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md)
