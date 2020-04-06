---
title: GuidSymbol Öğesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59068a9ac9f952b5370681b3684ce4234354afc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711121"
---
# <a name="guidsymbol-element"></a>GuidSymbol öğesi
Öğe, `GuidSymbol` bir menüyü, grubu veya komutu temsil eden GUID:ID çiftinin GUID'sini içerir. Kimlik, öğedeki `IDSymbol` bir öğeden gelir. `GuidSymbol` Öğe, `GuidSymbol` öznitelikte `name` `value` bulunan GUID için uygun bir ad sağlayan bir özniteliğe sahiptir.

## <a name="syntax"></a>Sözdizimi

```xml
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">
  <IDSymbol>... </IDSymbol>
  <IDSymbol>... </IDSymbol>
</GuidSymbol>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|ad|Gereklidir. GUID sembolünün adı.|
|value|Gereklidir. GUID sembolünün GUID'i.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[IDSymbol öğesi](../extensibility/idsymbol-element.md)|Bir menüyü, grubu veya komutu temsil eden GUID:ID çiftinin kimliğini içerir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Semboller öğesi](../extensibility/symbols-element.md)|Öğeleri `GuidSymbol` *.vsct* dosyasında grupla.|

## <a name="remarks"></a>Açıklamalar
 Genellikle, bir *.vsct* dosyası `GuidSymbol` `Symbols` bölümünde üç öğe içerir, biri paketin kendisi için, biri komut kümesi için (paketin sunduğu menüler, gruplar ve komutların toplanması) ve diğeri düğmeler ve diğer görsel bileşenler için simgeler sağlayan bit eşlemleri için. Belirli `IDSymbol` `GuidSymbol` bir öğedeki her öğenin benzersiz `value`bir öğesi olmalıdır. Ancak, `IDSymbol` aynı değerlere sahip öğeler, farklı ebeveynleri olduğu sürece bir pakette bulunabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
