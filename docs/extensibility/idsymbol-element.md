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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 513033b2db2cbf222c7835679ad36e00b91887b6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086904"
---
# <a name="idsymbol-element"></a>IDSymbol öğesi
öğesi `IDSymbol` bir menüyü, grubu veya komutu temsil eden GUID:ID çiftinin kimliğini içerir. GUID üst öğesinden `GuidSymbol` gelir. öğesi, özniteliğinde yer alan kimlik için kolay `IDSymbol` ad sağlayan bir `name` `value` özniteliğine sahip.

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
