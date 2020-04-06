---
title: Elementi Tanımla | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc09de1d822f41b25397c7a56c7cce4449a9e551
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712268"
---
# <a name="define-element"></a>Öğeyi tanımla
Sembol adı ve değer çiftini tanımlar. Bu sembol koşullu özniteliklerle değerlendirilebilir. Daha fazla bilgi için [koşullu öznitelikleri](../extensibility/vsct-xml-schema-conditional-attributes.md)bakın. Ayrıca bakınız [Semboller öğesi.](../extensibility/symbols-element.md)

## <a name="syntax"></a>Sözdizimi

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|ad|Gereklidir. Sembolün adı:<br /><br /> name="Mod"|
|value|Gereklidir. Sembolün değeri:<br /><br /> değer="Standart"|
|Koşul|İsteğe bağlı. Daha fazla bilgi için [koşullu öznitelikleri](../extensibility/vsct-xml-schema-conditional-attributes.md)bakın.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|VSPackage'ın tümleşik geliştirme ortamına (IDE) sağladığı komutları temsil eden tüm öğeleri tanımlar. Örneğin, menü öğeleri, menüler, araç çubukları ve açılan kutular.|

## <a name="example"></a>Örnek

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
