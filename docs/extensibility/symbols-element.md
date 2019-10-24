---
title: Symbols öğesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce299f99699a7bc048b3dc7da39aea3f734addeb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719396"
---
# <a name="symbols-element"></a>Symbols Öğesi
Diğer VSCT öğeleri tarafından kullanılan GUID 'Leri ve kimlikleri tanımlar. Yönetilmeyen kod için bu bilgiler genellikle [extern öğesi](../extensibility/extern-element.md)tarafından belirtilen başlık dosyalarından gelir. Yönetilen kod, bu bilgileri tanımlamak için semboller öğesinin alt öğelerini kullanır.

 Var olan bir. CTO dosyasından bir. vsct dosyası oluşturursanız, semboller semboller öğesinin alt öğesi olarak oluşturulur. Daha fazla bilgi için bkz [. nasıl yapılır: oluşturma. Varolan bir dosyadan vsct dosyası. CTO dosyası](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 Sembol öğesi, Önişlemci tarafından kullanılmak üzere ad-değer çiftlerini tanımlayan [define öğesiyle](../extensibility/define-element.md)karıştırılmamalıdır.

## <a name="syntax"></a>Sözdizimi

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
|Yok.||

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|GuidSymbol|Bir GUID sembolünü tanımlar. GuidSymbol iki gerekli özniteliğe sahiptir: ad ve değer. Ad, simgenin adıdır ve değer, GUID 'in bir dize olarak değeridir.<br /><br /> Örneğin: \<GuidSymbol Name = "guidVsPackage1Pkg" Value = "{c5f54698-101A-4846-84d3-dc748f9cd848}"/>|
|IDSymbol|Bir sembol tanımlar. IDSymbol iki gerekli özniteliğe sahiptir: ad ve değer. Ad, simgenin adıdır ve değer, sembolün bir dize olarak değeridir.<br /><br /> Örneğin: \<IDSymbol Name = "MyMenuGroup" Value = "0x1020"/>|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable Öğesi](../extensibility/commandtable-element.md)|. Vsct dosyasının kök öğesi.|

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