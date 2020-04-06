---
title: Semboller Öğesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c24c3f84df23a07b6b16272b66b29e32ad7b911
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699345"
---
# <a name="symbols-element"></a>Symbols Öğesi
Diğer VSCT elemanları tarafından kullanılan GUI'leri ve KOPYALARı tanımlar. Yönetilmeyen kod için, bu bilgiler genellikle [Extern Öğesi](../extensibility/extern-element.md)tarafından belirtilen üstbilgi dosyalarından gelir. Yönetilen kod, bu bilgileri tanımlamak için Semboller öğesinin alt öğelerini kullanır.

 Varolan bir .cto dosyasından .vsct dosyası oluşturursanız, semboller Semboller öğesinin alt öğesi olarak oluşturulur. Daha fazla bilgi için [bkz: Nasıl: Bir . Varolan bir dosyadan Vsct Dosyası . Cto Dosyası](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 Semboller öğesi, önişlemci tarafından kullanılmak üzere ad değeri çiftleri tanımlayan [Tanım Öğesi](../extensibility/define-element.md)ile karıştırılmamalıdır.

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
|None||

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|GuidSymbol|GUID simgesi tanımlar. GuidSymbol'un iki gerekli özelliği vardır: ad ve değer. Ad, sembolün adıdır ve değer GUID'in dize olarak değeridir.<br /><br /> Örneğin:\<GuidSymbol adı="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|IDSymbol|Bir sembol tanımlar. IDSymbol'un iki gerekli özelliği vardır: ad ve değer. Ad, sembolün adıdır ve değer de simgenin dize olarak değeridir.<br /><br /> Örneğin:\<IDSymbol adı="MyMenuGroup" value="0x1020" />|

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
