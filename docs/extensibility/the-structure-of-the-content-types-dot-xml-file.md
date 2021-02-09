---
title: '[Content_types]. xml dosyasının yapısı | Microsoft Docs'
description: VSıX paketindeki içerik türleri hakkında bilgi içeren içerik türleri dosyasının yapısı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38348661946be3894332d49177f972410563b716
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895214"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>[Content_types].xml Dosyasının Yapısı
VSıX paketindeki içerik türleri hakkında bilgi içerir. Visual Studio, paketi yüklemek için [Content_Types]. xml dosyasını kullanır, ancak dosyanın kendisini yüklemez.

> [!NOTE]
> Bu konu yalnızca VSıX paketlerinde kullanılan [Content_Type]. xml dosyaları için geçerli olsa da, [Content_Types]. xml dosya türü *Açık paketleme kuralları (OPC)* standardının bir parçasıdır. Daha fazla bilgi için bkz. [OPC: msdn Web sitesinde verilerinizi paketlemeye yönelik yeni bir standart](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data) .

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Aşağıdaki bölümlerde kök öğe ve öznitelikleri ve alt öğeleri açıklanır.

### <a name="root-element"></a>Kök öğe

|Öğe|Açıklama|
|-------------|-----------------|
|`Types`|VSıX paketindeki dosya türlerini numaralandırmanızı sağlayan alt öğeleri içerir.|

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Xmlns`|(Gerekli.) Bu [Content_Types]. xml dosyası için kullanılan şemanın konumu.|

### <a name="attribute-name-attribute"></a>{Öznitelik adı} Özniteliğe

| Değer | Açıklama |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | İçerik türleri şemasının konumu. |

### <a name="child-elements"></a>Alt Öğeler
 `Types`Öğesi herhangi bir sayıda `Default` öğe içerebilir.

|Öğe|Açıklama|
|-------------|-----------------|
|`Default`|VSıX paketindeki bir içerik türünü açıklar. Paketteki her dosya türünün kendi `Default` öğesi olmalıdır.|

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Extension`|VSıX paketindeki bir dosyanın dosya adı uzantısı.|
|`ContentType`|Dosya adı uzantısıyla ilişkili içerik türünü açıklar.|

### <a name="attribute-name-attribute"></a>{Öznitelik adı} Özniteliğe
 Visual Studio `ContentType` , ilişkili türler için aşağıdaki değerleri tanır `Extension` .

|Dahili numara|ContentType|
|---------------|-----------------|
|txt|metin/düz|
|pkgdef|metin/düz|
|xml|metin/XML|
|vsixmanifest|metin/XML|
|htm veya HTML|text/html|
|biçimindeki|Uygulama/RTF|
|pdf|uygulama/PDF|
|gif|resim/GIF|
|jpg veya JPEG|resim/jpg|
|tiff|resim/TIFF|
|vsix|Uygulama/zip|
|zip|Uygulama/zip|
|dosyasını|Uygulama/sekizli-akış|
|diğer tüm dosya türleri|Uygulama/sekizli-akış|

## <a name="example"></a>Örnek

### <a name="description"></a>Description
 Şu [Content_Types]. xml dosyası tipik bir VSıX paketini açıklamaktadır.

### <a name="code"></a>Kod

```
<?xml version="1.0" encoding="utf-8" ?>
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
    <Default Extension="vsixmanifest" ContentType="text/xml" />
    <Default Extension="dll" ContentType="application/octet-stream" />
    <Default Extension="png" ContentType="application/octet-stream" />
    <Default Extension="txt" ContentType="text/plain" />
    <Default Extension="pkgdef" ContentType="text/plain" />
</Types>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Bir VSIX Paketinin Anatomisi](../extensibility/anatomy-of-a-vsix-package.md)
- [VSıX uzantı şeması 1,0 başvurusu](/previous-versions/dd393700(v=vs.110))
- [OPC: verilerinizi paketlemeye yönelik yeni bir standart](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data)