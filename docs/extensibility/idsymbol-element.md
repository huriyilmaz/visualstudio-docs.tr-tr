---
title: IDSymbol Öğesi | Microsoft Dokümanlar
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
ms.openlocfilehash: d02a26a6874165738d917a14986d16d142c01915
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710371"
---
# <a name="idsymbol-element"></a>IDSymbol öğesi
Öğe, `IDSymbol` bir menüyü, grubu veya komutu temsil eden GUID:ID çiftinin kimliğini içerir. GUID ana `GuidSymbol` öğeden gelir. Öğe, `IDSymbol` öznitelikte `name` `value` bulunan kimlik için uygun bir ad sağlayan bir özniteliğe sahiptir.

## <a name="syntax"></a>Sözdizimi

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|ad|Gereklidir. Kimlik sembolünün adı.|
|value|Gereklidir. Kimlik simgesinin sayısal kimlik değeri.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[GuidSymbol öğesi](../extensibility/guidsymbol-element.md)|Bir menüyü, grubu veya komutu temsil eden GUID:ID çiftinin GUID'ini içerir. Öğeleri `IDSymbol` grupla.|

## <a name="remarks"></a>Açıklamalar
 Belirli `IDSymbol` `GuidSymbol` bir öğedeki her öğenin benzersiz `value`bir öğesi olmalıdır. Ancak, `IDSymbol` aynı değerlere sahip öğeler, farklı ebeveynleri olduğu sürece bir pakette bulunabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
