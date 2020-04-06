---
title: CommandTable Öğesi | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a362763d34335b9a18c4114a7c35b23f0efee020
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739650"
---
# <a name="commandtable-element"></a>CommandTable öğesi
CommandTable *.vsct* dosyasının kök öğesidir. Bu, bir VSPackage'ın IDE'ye sağladığı komutların gerçek düzenini ve türünü tanımlayan dosyadır. Komutlar menü öğelerini, menüleri, araç çubuklarını ve açılan kutuları içerebilir. Daha fazla bilgi için [Visual Studio komut tablosu (.vsct) dosyalarına](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)bakın.

## <a name="syntax"></a>Sözdizimi

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
| Xmlns | Gereklidir. XML ad alanları:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs="<http://www.w3.org/2001/XMLSchema>" |
| language | İsteğe bağlı. Dil özniteliği, komut tablosundaki tüm \<Dizeleri> öğelerinin varsayılan dilini belirtmek için kullanılabilir.  Dil belirtilmemişse, geçerli işlemin dili kullanılır:<br /><br /> dil="en-us" |

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Extern elemanı](../extensibility/extern-element.md)|İsteğe bağlı. Derleyici için önişlemci yönergeleri içerir.|
|[Öğe ekle](../extensibility/include-element.md)|İsteğe bağlı. Derlemeye dahil edilemeyecek dosyalara giden yollar içerir.|
|[Öğeyi tanımla](../extensibility/define-element.md)|İsteğe bağlı. Adını ve değerini verilen bir sembolü tanımlar.|
|[Komutlar öğesi](../extensibility/commands-element.md)|İsteğe bağlı. Diğer öğelerin tümlerini içeren VSPackage için tüm komutları tanımlayan üst öğe.|
|[Komut Yerleşimleri öğesi](../extensibility/commandplacements-element.md)|İsteğe bağlı. Komutların komutların nereye yerleştirileceğini tanımlar.|
|[GörünürlükKısıtlamalar öğesi](../extensibility/visibilityconstraints-element.md)|İsteğe bağlı. Komutların ve araç çubuklarının statik görünürlüğünü belirler.|
|[KeyBindings öğesi](../extensibility/keybindings-element.md)|İsteğe bağlı. Komutlar için kısayol tuşu birleşimlerini belirtir.|
|[UsedCommands öğesi](../extensibility/usedcommands-element.md)|İsteğe bağlı. Bir VSPackage'ın başlangıçta diğer VSPackages tarafından desteklenen kendi işlevsellik sürümünü isteğe bağlı olarak uygulamasına olanak tanır.|
|[Semboller öğesi](https://www.microsoft.com/download/details.aspx?id=55984)|İsteğe bağlı. Derleyici için herhangi bir sembol verisi -GUIDs, Imds ve benzeri- içerir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|None||

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
