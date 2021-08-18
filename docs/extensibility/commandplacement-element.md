---
title: CommandPlacement Öğesi | Microsoft Docs
description: CommandPlacement öğesi, düğmelerin, grupların ve menülerin birden fazla gruba veya menüye dahil ekleyebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 95a690ce394e088e3e490aa7e279725ff69bbdd1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058038"
---
# <a name="commandplacement-element"></a>CommandPlacement öğesi
CommandPlacement öğesi, düğmelerin, grupların ve menülerin birden fazla gruba veya menüye dahil ekleyebilirsiniz. CommandPlacement öğesini kullanarak, kullanıcı arabiriminin görünümlerini değiştirmek için bu öğeleri tamamen yeniden tanımlamaya gerek yoktur.

 Daha fazla bilgi için [bkz. Yeniden kullanılabilir düğme grupları oluşturma.](../extensibility/creating-reusable-groups-of-buttons.md)

## <a name="syntax"></a>Syntax

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
|guid|Gereklidir. Symbols öğesinde tanımlandığı gibi, komut kümesi [guid'i.](../extensibility/symbols-element.md)|
|kimlik|Gereklidir. içinde tanımlandığı gibi, yerleştiril olacak menü, grup veya komutun `Symbols Element` kimliği.|
|Öncelik|Gereklidir. Öğenin üst öğesinde görsel konumunu belirler.|
|Koşul|İsteğe bağlı. Bkz. [Koşullu Aattributes](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Üst|Gereklidir. Yerleştiril olacak öğeyi barındıran menü veya grup.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandPlacements öğesi](../extensibility/commandplacements-element.md)|CommandPlacements ve CommandPlacement öğelerinin gruplarını belirtir.|

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
- [CommandPlacements öğesi](../extensibility/commandplacements-element.md)
- [Visual Studio tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
