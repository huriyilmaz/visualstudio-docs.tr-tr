---
title: CommandTable öğesi | Microsoft Docs
description: CommandTable, VSPackage 'ın IDE 'ye sağladığı komutların yerleşimini ve türünü tanımlayan. vsct dosyasının kök öğesidir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 79441880091088cf1d953c8925273e801dc0860d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887360"
---
# <a name="commandtable-element"></a>CommandTable öğesi
CommandTable, *. vsct* dosyasının kök öğesidir. Bu, bir VSPackage 'ın IDE 'ye sağladığı komutların gerçek düzen ve türünü tanımlayan dosyadır. Komutlar Menü öğeleri, menüler, araç çubukları ve Birleşik giriş kutuları içerebilir. Daha fazla bilgi için bkz. [Visual Studio komut tablosu (. vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="syntax"></a>Syntax

```xml
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >
  <Extern>... </Extern>
  <Include>... </Include>
  <Define>... </Define>
  <Commands>... </Commands>
  <CommandPlacements>... </CommandPlacements>
  <VisibilityConstraints>... </VisibilityConstraints>
  <KeyBindings>... </KeyBindings>
  <UsedCommands... </UsedCommands>
  <Symbols>... </Symbols>
</CommandTable>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

| Öznitelik | Açıklama |
|-----------| - |
| özniteliði | Gereklidir. XML ad alanları:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns: XS = " <http://www.w3.org/2001/XMLSchema> " |
| language | İsteğe bağlı. Language özniteliği, komut tablosundaki tüm öğelerin varsayılan dilini belirtmek için kullanılabilir \<Strings> .  Dil belirtilmezse, geçerli işlemin dili kullanılacaktır:<br /><br /> Language = "en-US" |

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Extern öğesi](../extensibility/extern-element.md)|İsteğe bağlı. Derleyici için önişlemci yönergelerini içerir.|
|[Include öğesi](../extensibility/include-element.md)|İsteğe bağlı. Derlemeye dahil edilecek herhangi bir dosyanın yolunu içerir.|
|[Öğe tanımla](../extensibility/define-element.md)|İsteğe bağlı. Adı ve değeri verilen bir sembol tanımlar.|
|[Commands öğesi](../extensibility/commands-element.md)|İsteğe bağlı. Tüm diğer öğeleri içeren VSPackage için tüm komutları tanımlayan üst öğe.|
|[CommandPlacements öğesi](../extensibility/commandplacements-element.md)|İsteğe bağlı. Komut çubuğundaki komutların nereye yerleştirileceğini tanımlar.|
|[Visibilitykýsýtlamaöğesi](../extensibility/visibilityconstraints-element.md)|İsteğe bağlı. Komutların ve araç çubuklarının statik görünürlüğünü belirler.|
|[KeyBindings öğesi](../extensibility/keybindings-element.md)|İsteğe bağlı. Varsa, komutlar için kısayol tuş bileşimlerini belirtir.|
|[UsedCommands öğesi](../extensibility/usedcommands-element.md)|İsteğe bağlı. Bir VSPackage 'ın, özgün olarak diğer VSPackages tarafından desteklenen kendi işlev sürümünü kullanmasına izin verir.|
|[Symbols öğesi](https://www.microsoft.com/download/details.aspx?id=55984)|İsteğe bağlı. Derleyici için herhangi bir sembol verisi (--Guid, kimlik vb.) içerir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|Hiçbiri||

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (. vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
