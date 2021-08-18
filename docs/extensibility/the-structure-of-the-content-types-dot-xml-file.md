---
title: '[Content_types].xml Dosya | Microsoft Docs'
description: VSIX paketinde içerik türleri hakkında bilgi içeren içerik türleri dosyasının yapısı hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 681b2877983762ec0601543ae996748612fd3812
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049317"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>[Content_types].xml Dosyasının Yapısı
VSIX paketinde içerik türleri hakkında bilgi içerir. Visual Studio yüklemek için [Content_Types].xml dosyasını kullanır, ancak dosyanın kendisini yüklemez.

> [!NOTE]
> Bu konu yalnızca VSIX paketlerinde kullanılan [Content_Type].xml dosyaları için geçerli olsa da, [Content_Types].xml dosya türü Açık Paketleme Kuralları *(OPC)* standardında yer alır. Daha fazla bilgi için MSDN Web [sitesinde OPC:](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data) A New Standard For Packaging Your Data konusuna bakın.

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Aşağıdaki bölümlerde kök öğe, öznitelikleri ve alt öğeleri açıklanmaktadır.

### <a name="root-element"></a>Kök Öğe

|Öğe|Açıklama|
|-------------|-----------------|
|`Types`|VSIX paketinde dosya türlerini numaraya alan alt öğeleri içerir.|

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Xmlns`|(Gerekli.) Bu [Content_Types].xml dosyası için kullanılan şemanın konumu.|

### <a name="attribute-name-attribute"></a>{Öznitelik adı} Öznitelik

| Değer | Açıklama |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | İçerik türleri şemasının konumu. |

### <a name="child-elements"></a>Alt Öğeler
 öğesi `Types` herhangi bir sayıda öğe `Default` içerebilir.

|Öğe|Açıklama|
|-------------|-----------------|
|`Default`|VSIX paketinde bir içerik türünü açıklar. Pakette her dosya türünün kendi öğesi `Default` olması gerekir.|

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Extension`|VSIX paketinde bir dosyanın dosya adı uzantısı.|
|`ContentType`|Dosya adı uzantısıyla ilişkili içerik türü açık bir şekilde açık bir şekilde anlattır.|

### <a name="attribute-name-attribute"></a>{Öznitelik adı} Öznitelik
 Visual Studio ilişkili `ContentType` türler için aşağıdaki değerleri `Extension` tanır.

|Dahili numara|Contenttype|
|---------------|-----------------|
|Txt|metin/düz|
|pkgdef|metin/düz|
|xml|text/xml|
|vsixmanifest|text/xml|
|html veya html|text/html|
|Rtf|application/rtf|
|pdf|application/pdf|
|Gıf|image/gif|
|jpg veya jpeg|image/jpg|
|tiff|image/tiff|
|vsix|uygulama/zip|
|Zip|uygulama/zip|
|Dll|application/octet-stream|
|diğer tüm dosya türleri|application/octet-stream|

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama
 Aşağıdaki [Content_Types].xml dosya tipik bir VSIX paketini açıklar.

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
- [VSIX Uzantı Şeması 1.0 Başvurusu](/previous-versions/dd393700(v=vs.110))
- [OPC: Verilerinizi paketlemek için yeni bir standart](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data)