---
title: CommandPlacements Öğesi | Microsoft Docs
description: CommandPlacements öğesi, CommandPlacement öğelerini ve diğer CommandPlacements gruplamalarını gruplar. CommandPlacements öğesi isteğe bağlıdır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7293f1c1e6524284e11116167729f4a965d036fb12239794c97721a4302cd0d0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452621"
---
# <a name="commandplacements-element"></a>CommandPlacements öğesi
CommandPlacements öğesi, CommandPlacement öğelerini ve diğer CommandPlacements gruplamalarını gruplar.

 CommandPlacements öğesi isteğe bağlıdır. İkincil bir konuma hiçbir komut, grup veya menü dahil edilecek bir komut, grup veya menü yoksa bu bölümü *.vsct dosyanıza dahil etmek zorunda değildir.*

## <a name="syntax"></a>Syntax

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|CommandPlacements|CommandPlacement öğelerini ve diğer CommandPlacements gruplamalarını gruplar.|
|[CommandPlacement öğesi](../extensibility/commandplacement-element.md)|Düğmelerin, grupların ve menülerin birden fazla gruba veya menüye dahil ekleyebilirsiniz.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|Komutları temsil eden tüm öğeleri tanımlar.|

## <a name="example"></a>Örnek

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Ayrıca bkz.
- [CommandPlacement öğesi](../extensibility/commandplacement-element.md)
- [Visual Studio tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
