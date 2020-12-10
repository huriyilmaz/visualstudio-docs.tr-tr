---
title: IDSymbol öğesi | Microsoft Docs
description: 'IDSymbol öğesi, bir menü, Grup veya komutu temsil eden GUID: ID çiftinin KIMLIĞINI içerir.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4feb477f8507bc3fe57e6db355538ab98ceeeaa
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995544"
---
# <a name="idsymbol-element"></a>IDSymbol öğesi
`IDSymbol`Öğesi, bir menü, Grup veya komutu temsil eden GUID: ID ÇIFTININ kimliğini içerir. GUID üst `GuidSymbol` öğeden gelir. `IDSymbol`Öğesi, `name` özniteliğinde yer alan ID için kolay bir ad sağlayan bir özniteliğe sahiptir `value` .

## <a name="syntax"></a>Sözdizimi

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|name|Gereklidir. KIMLIK sembolünün adı.|
|değer|Gereklidir. KIMLIK sembolünün sayısal KIMLIK değeri.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GuidSymbol öğesi](../extensibility/guidsymbol-element.md)|Bir menü, Grup veya komutu temsil eden GUID: ID çiftinin GUID 'sini içerir. `IDSymbol`Öğeleri gruplandırır.|

## <a name="remarks"></a>Açıklamalar
 `IDSymbol`Verilen bir öğe içindeki her öğenin `GuidSymbol` benzersiz olması gerekir `value` . Ancak, `IDSymbol` aynı değerlere sahip öğeler farklı üst öğeleri oldukları sürece bir pakette bulunabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (. vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
