---
title: Include öğesi | Microsoft Docs
description: Include öğesi, geçerli dosyaya eklenmek üzere sağlanan içerme yolunda konumlanan bir dosyayı belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71da1241863e41529af33bdd5e45dcf0a8bfbdb1
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996350"
---
# <a name="include-element"></a>Include öğesi
Include öğesi, geçerli dosyaya eklenmek üzere sağlanan içerme yolunda konumlanan bir dosyayı belirtir.  Tanımlanan tüm semboller ve türler, derlenen sonucun bir parçası olacak.

## <a name="syntax"></a>Sözdizimi

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|değerini|Gereklidir. Üst bilgi dosyasının yolu:<br /><br /> href = "Stdidcmd. h"|
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Yok.|Yok.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|Bir VSPackage 'ın IDE 'ye sağladığı komutları (menü öğeleri, menüler, araç çubukları ve Birleşik giriş kutuları) temsil eden tüm öğeleri tanımlar.|

## <a name="example"></a>Örnek

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (. vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
