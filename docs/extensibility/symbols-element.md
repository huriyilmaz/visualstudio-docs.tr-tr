---
title: Symbols Öğesi | Microsoft Docs
description: Semboller öğesi, diğer VSCT öğeleri tarafından kullanılan GUID'leri ve kimlikleri tanımlar. Bu makale bir örnek içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6a9aad102cd5b4e701715d245bde20942d8abd50
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144372"
---
# <a name="symbols-element"></a>Symbols Öğesi
Diğer VSCT öğeleri tarafından kullanılan GUID'leri ve kimlikleri tanımlar. Bu bilgiler genellikle, [unmanaged](../extensibility/extern-element.md)code için Extern Öğesi tarafından belirtilen üst bilgi dosyalarından gelir. Yönetilen kod, bu bilgileri tanımlamak için Semboller öğesinin alt öğelerini kullanır.

 Mevcut bir .cto dosyasından bir .vsct dosyası oluşturmanız, semboller Semboller öğesinin öğesi olarak oluşturulur. Daha fazla bilgi için, [bkz. How to: Create a . Var Olan bir dosyasından Vsct Dosyası. Cto Dosyası](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 Semboller öğesi, ön işlemci tarafından [kullanmak](../extensibility/define-element.md)üzere ad-değer çiftlerini tanımlayan Define Öğesi ile karıştırılmamalıdır.

## <a name="syntax"></a>Syntax

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Hiçbiri||

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|GuidSymbol|GUID sembolünü tanımlar. GuidSymbol iki gerekli öznitelike sahip: ad ve değer. Ad, sembolün adı, değer ise guid değerinin dize olarak değeridir.<br /><br /> Örnek:\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|IDSymbol|Bir sembol tanımlar. IDSymbol iki gerekli öznitelike sahip: ad ve değer. Ad, sembolün adı, değer ise dize olarak sembolün değeridir.<br /><br /> Örnek:\<IDSymbol name="MyMenuGroup" value="0x1020" />|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable Öğesi](../extensibility/commandtable-element.md)|.vsct dosyasının kök öğesi.|

## <a name="example"></a>Örnek

```
<Symbols>
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
    <IDSymbol name="cmdidMyTool" value="0x0101" />
  </GuidSymbol>
</Symbols>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
