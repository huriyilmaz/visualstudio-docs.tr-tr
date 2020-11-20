---
title: Commandyerleştirmesini öğesi | Microsoft Docs
description: Commandyerleştirme öğesi düğmelerin, grupların ve menülerin birden fazla gruba veya menüye dahil edilmesini sağlar.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d2828a32ea837e95be438aafa6ec4b31293a43a7
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974065"
---
# <a name="commandplacement-element"></a>Commandyerleştirme öğesi
Commandyerleştirme öğesi düğmelerin, grupların ve menülerin birden fazla gruba veya menüye dahil edilmesini sağlar. Commandyerleştirme öğesini kullanarak, Kullanıcı arabiriminin görünümünü değiştirmek için bu öğeleri tamamen yeniden tanımlamanız gerekmez.

 Daha fazla bilgi için bkz. yeniden [kullanılabilir düğme grupları oluşturma](../extensibility/creating-reusable-groups-of-buttons.md).

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
|guid|Gereklidir. [Sembol öğesinde](../extensibility/symbols-element.md)tanımlandığı şekilde, komut kümesinin GUID 'si.|
|kimlik|Gereklidir. İçinde tanımlandığı şekilde, yerleştirilecek menü, Grup veya komutun kimliği `Symbols Element` .|
|Priority|Gereklidir. Öğenin üst öğesinde görsel konumunu belirler.|
|Koşul|İsteğe bağlı. Bkz. [koşullu Aöznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Üst|Gereklidir. Yerleştirilecek öğeyi barındıran menü veya grup.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandPlacements öğesi](../extensibility/commandplacements-element.md)|CommandPlacements ve Commandyerleştirme öğelerinin gruplarını belirtir.|

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
- [Visual Studio komut tablosu (. vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
