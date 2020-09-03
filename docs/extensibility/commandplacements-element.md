---
title: CommandPlacements öğesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72b087652a654b563fd4e00bacc52290a29fe1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739706"
---
# <a name="commandplacements-element"></a>CommandPlacements öğesi
CommandPlacements öğesi, Commandyerleştirme öğelerini ve diğer CommandPlacements gruplandırmaları gruplandırır.

 CommandPlacements öğesi isteğe bağlıdır. İkincil bir konuma hiçbir komut, Grup veya menü eklenmemelidir, bu bölümü *. vsct* dosyanıza eklemeniz gerekmez.

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
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|CommandPlacements|Commandyerleştirme öğelerini ve diğer CommandPlacements gruplamalarını gruplandırır.|
|[Commandyerleştirme öğesi](../extensibility/commandplacement-element.md)|Düğmelerin, grupların ve menülerin birden fazla gruba veya menüye dahil edilmesini sağlar.|

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
- [Commandyerleştirme öğesi](../extensibility/commandplacement-element.md)
- [Visual Studio komut tablosu (. vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
