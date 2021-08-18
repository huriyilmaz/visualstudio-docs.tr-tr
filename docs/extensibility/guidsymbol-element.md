---
title: GuidSymbol öğesi | Microsoft Docs
description: "GuidSymbol öğesi, bir menü, Grup veya komutu temsil eden GUID: ID çiftinin GUID 'sini içerir."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b79b8d9399e4294a4e22cbc36f11bccbf703e215
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086982"
---
# <a name="guidsymbol-element"></a>GuidSymbol öğesi
`GuidSymbol`Öğesi, bir menü, Grup veya komutu temsil eden GUID: ID ÇIFTININ GUID 'sini içerir. KIMLIĞI `IDSymbol` , öğesindeki bir öğeden gelir `GuidSymbol` . `GuidSymbol`Öğesi, `name` özniteliğinde yer alan GUID için kolay bir ad sağlayan bir özniteliğe sahiptir `value` .

## <a name="syntax"></a>Syntax

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
|name|Gereklidir. GUID sembolünün adı.|
|değer|Gereklidir. GUID sembolünün GUID 'SI.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[IDSymbol öğesi](../extensibility/idsymbol-element.md)|Bir menü, Grup veya komutu temsil eden GUID: ID çiftinin KIMLIĞINI içerir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Symbols öğesi](../extensibility/symbols-element.md)|`GuidSymbol` *. Vsct* dosyasındaki öğeleri gruplandırır.|

## <a name="remarks"></a>Açıklamalar
 Genellikle, bir *. vsct* dosyası kendi bölümünde, biri paketin kendisi için, biri `GuidSymbol` `Symbols` komut kümesi için (menülerin, grupların ve paketin kullanılabilir hale getiren komutlar koleksiyonu) ve düğmeler ve diğer görsel bileşenlere simgeler sağlayan bit eşlemler için olmak üzere üç öğesi içerir. `IDSymbol`Verilen bir öğe içindeki her öğenin `GuidSymbol` benzersiz olması gerekir `value` . Ancak, `IDSymbol` aynı değerlere sahip öğeler farklı üst öğeleri oldukları sürece bir pakette bulunabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [komut tablosu (. vsct) dosyaları Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
