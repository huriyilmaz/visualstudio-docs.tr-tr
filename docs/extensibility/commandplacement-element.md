---
title: Komut Yerleştirme Öğesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf9f23b5e860b895baa4c2a7a783f2ee15fcc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739735"
---
# <a name="commandplacement-element"></a>Komut Yerleştirme öğesi
CommandPlacement öğesi düğmelerin, grupların ve menülerin birden fazla gruba veya menüye eklenmesini sağlar. Komut Yerleştirme öğesini kullanarak, kullanıcı arabiriminin görünümünü değiştirmek için bu öğeleri tamamen yeniden tanımlamanız gerekmez.

 Daha fazla bilgi için [bkz.](../extensibility/creating-reusable-groups-of-buttons.md)

## <a name="syntax"></a>Sözdizimi

```
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >
  <Parent>... </Parent>
</CommandPlacement>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Guıd|Gereklidir. [Semboller öğesinde](../extensibility/symbols-element.md)tanımlandığı gibi komut kümesinin guid.|
|id|Gereklidir. Menüde tanımlandığı gibi, yerleştirilecek menü, grup veya `Symbols Element`komutun kimliği.|
|Öncelik|Gereklidir. Öğenin üst öğesindeki görsel konumunu belirler.|
|Koşul|İsteğe bağlı. Bkz. [Koşullu Aözler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Üst|Gereklidir. Yerleştirilecek öğeyi barındıran menü veya grup.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Komut Yerleşimleri öğesi](../extensibility/commandplacements-element.md)|Komuta Yerve Komuta Yerlemi öğelerini belirtir.|

## <a name="example"></a>Örnek

```
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Komut Yerleşimleri öğesi](../extensibility/commandplacements-element.md)
- [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
