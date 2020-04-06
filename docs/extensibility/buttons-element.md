---
title: Düğmeler Öğesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64ac5621093f30af28ade0817906b767231e4ee1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739925"
---
# <a name="buttons-element"></a>Düğmeler öğesi
Gruplar Tek tek komutları temsil eden [Düğme](../extensibility/button-element.md) öğeleri.

## <a name="syntax"></a>Sözdizimi

```
<Buttons>
  <Button>... </Button>
  <Button>... </Button>
</Buttons>
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
|[Düğmeler öğesi](../extensibility/buttons-element.md)|Düğme öğelerini grupla.|
|[Düğme öğesi](../extensibility/button-element.md)|Kullanıcının etkileşim kurabileceği bir komut tanımlar.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Komutlar öğesi](../extensibility/commands-element.md)|VSPackage araç çubuğundaki komutların toplanmasını temsil eder.|

## <a name="example"></a>Örnek

```
<Buttons>
  <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button">
    <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/>
    <Icon guid="guidGenericCmdBmp" id="bmpArrow"/>
    <Strings>
      <ButtonText>C# Command Sample</ButtonText>
    </Strings>
  </Button>
</Buttons>
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
