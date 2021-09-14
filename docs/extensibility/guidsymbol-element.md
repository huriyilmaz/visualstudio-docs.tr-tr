---
title: GuidSymbol Öğesi | Microsoft Docs
description: GuidSymbol öğesi bir menüyü, grubu veya komutu temsil eden GUID:ID çiftinin GUID'lerini içerir.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626300"
---
# <a name="guidsymbol-element"></a>GuidSymbol öğesi
öğesi `GuidSymbol` bir menüyü, grubu veya komutu temsil eden GUID:ID çiftinin GUID'lerini içerir. Kimlik, öğesinde `IDSymbol` bir öğesinden `GuidSymbol` gelir. öğesi, `GuidSymbol` `name` özniteliğinde yer alan GUID için kolay ad sağlayan bir `value` özniteliğine sahip.

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
|name|Gereklidir. GUID simgesinin adı.|
|değer|Gereklidir. GUID simgesinin GUID'i.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[IDSymbol öğesi](../extensibility/idsymbol-element.md)|Menü, grup veya komutu temsil eden GUID:ID çiftinin kimliğini içerir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Semboller öğesi](../extensibility/symbols-element.md)|Bir `GuidSymbol` *.vsct dosyasındaki öğeleri gruplar.*|

## <a name="remarks"></a>Açıklamalar
 *Genellikle, bir .vsct* dosyası kendi bölümünde, biri paketin kendisi için, biri komut kümesi için (paketin kullanılabilir olduğu menüler, gruplar ve komutlar koleksiyonu) ve biri düğmeler ve diğer görsel bileşenler için simgeler sağlayan bit eşlemler için üç öğe `GuidSymbol` `Symbols` içerir. Verilen `IDSymbol` bir öğedeki `GuidSymbol` her öğe benzersiz bir öğesine sahip `value` olmalıdır. Ancak, `IDSymbol` aynı değerlere sahip öğeler, farklı ebeveynleri olduğu sürece bir pakette yer alan öğeler olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
