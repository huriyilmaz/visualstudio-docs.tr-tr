---
title: '[Content_Types]. xml dosyasının yapısı | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5cc42a5346498c04f759956b2ca00094ac1df119
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718723"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>[Content_types].xml Dosyasının Yapısı
VSıX paketindeki içerik türleri hakkında bilgi içerir. Visual Studio, paketi yüklemek için [Content_Types]. xml dosyasını kullanır, ancak dosyanın kendisini yüklemez.

> [!NOTE]
> Bu konu yalnızca VSıX paketlerinde kullanılan [Content_Type]. xml dosyaları için geçerli olsa da, [Content_Types]. xml dosya türü *Açık paketleme kuralları (OPC)* standardının bir parçasıdır. Daha fazla bilgi için bkz. [OPC: msdn Web sitesinde verilerinizi paketlemeye yönelik yeni bir standart](http://go.microsoft.com/fwlink/?LinkID=148207) .

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
| http://schemas.openformats.org/package/2006/content-types | İçerik türleri şemasının konumu. |

### <a name="child-elements"></a>Alt Öğeler
 @No__t_0 öğesi herhangi bir sayıda `Default` öğesi içerebilir.

|Öğe|Açıklama|
|-------------|-----------------|
|`Default`|VSıX paketindeki bir içerik türünü açıklar. Paketteki her dosya türünün kendi `Default` öğesi olmalıdır.|

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Extension`|VSıX paketindeki bir dosyanın dosya adı uzantısı.|
|`ContentType`|Dosya adı uzantısıyla ilişkili içerik türünü açıklar.|

### <a name="attribute-name-attribute"></a>{Öznitelik adı} Özniteliğe
 Visual Studio, ilişkili `Extension` türleri için aşağıdaki `ContentType` değerlerini tanır.

|uzantının|contentType|
|---------------|-----------------|
|txt|metin/düz|
|pkgdef|metin/düz|
|'Sini|metin/XML|
|vsixmanifest|metin/XML|
|htm veya HTML|metin/html|
|biçimindeki|Uygulama/RTF|
|belgesini|uygulama/PDF|
|gif|resim/GIF|
|jpg veya JPEG|resim/jpg|
|dosyalarında|resim/TIFF|
|vsix|Uygulama/zip|
|zip|Uygulama/zip|
|dosyasını|Uygulama/sekizli-akış|
|diğer tüm dosya türleri|Uygulama/sekizli-akış|

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama
 Aşağıdaki [Content_Types]. xml dosyası tipik bir VSıX paketini açıklar.

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
- [VSıX uzantı şeması 1,0 başvurusu](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC: verilerinizi paketlemeye yönelik yeni bir standart](http://go.microsoft.com/fwlink/?LinkID=148207)