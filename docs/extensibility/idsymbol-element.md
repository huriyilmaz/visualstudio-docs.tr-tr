---
title: IDSymbol Öğesi | Microsoft Docs
description: IDSymbol öğesi bir menüyü, grubu veya komutu temsil eden GUID:ID çiftinin kimliğini içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e5158b16fb2d12a7d1a93c0296126e915a138269
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904952"
---
# <a name="idsymbol-element"></a>IDSymbol öğesi
öğesi `IDSymbol` bir menüyü, grubu veya komutu temsil eden GUID:ID çiftinin kimliğini içerir. GUID üst öğesinden `GuidSymbol` gelir. öğesi, özniteliğinde yer alan kimlik için kolay `IDSymbol` bir ad sağlayan bir `name` `value` özniteliğine sahip.

## <a name="syntax"></a>Syntax

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|name|Gereklidir. Kimlik simgesinin adı.|
|değer|Gereklidir. Kimlik simgesinin Sayısal Kimlik değeri.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GuidSymbol öğesi](../extensibility/guidsymbol-element.md)|Bir menüyü, grubu veya komutu temsil eden GUID:ID çiftinin GUID'lerini içerir. Öğeleri `IDSymbol` gruplar.|

## <a name="remarks"></a>Açıklamalar
 Verilen `IDSymbol` bir öğedeki `GuidSymbol` her öğe benzersiz bir öğesine sahip `value` olmalıdır. Ancak, `IDSymbol` aynı değerlere sahip öğeler, farklı ebeveynleri olduğu sürece bir pakette yer alan öğeler olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
