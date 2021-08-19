---
title: CommandPlacements öğesi | Microsoft Docs
description: CommandPlacements öğesi, Commandyerleştirme öğelerini ve diğer CommandPlacements gruplandırmaları gruplandırır. CommandPlacements öğesi isteğe bağlıdır.
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
ms.openlocfilehash: 3ee3d626536ef16bc378be647b8418bb732ad8d6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051293"
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
- [komut tablosu (. vsct) dosyaları Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
