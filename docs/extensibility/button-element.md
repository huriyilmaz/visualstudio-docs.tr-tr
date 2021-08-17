---
title: Düğme Öğesi | Microsoft Docs
description: 'Button öğesi, kullanıcının etkileşimde buluna bir öğeyi tanımlar. Düğmeler farklı türlerde olabilir: Düğme, MenuButton ve SplitDropDown.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c64630126bfb671f9f71f78a51c524c2767164f3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073584"
---
# <a name="button-element"></a>Düğme öğesi
Kullanıcının etkileşimde buluna bir öğeyi tanımlar. Düğmeler farklı türlerde olabilir: Button, MenuButton ve SplitDropDown.

## <a name="syntax"></a>Syntax

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|guid|Gereklidir. GUID/ID komut tanımlayıcısının GUID'si.|
|kimlik|Gereklidir. GUID/ID komut tanımlayıcısının kimliği.|
|Öncelik|İsteğe bağlı. Önceliği belirten sayısal bir değer.|
|tür|İsteğe bağlı. Düğmenin tür belirten numaralandı değeri.<br /><br /> Verilmezse Düğme'leri kullanır.<br /><br /> Düğme<br /> Araç çubuklarında (genellikle bir düğme olarak), menülerde ve bağlam menülerinde görünen standart bir komut.<br /><br /> MenuButton<br /> Komut yürütmeden başka bir menü üreten menü öğesi.<br /><br /> SplitDropDown<br /> Standart araç çubuğundaki Geri Al ve Tekrarla düğmeleri gibi denetimler Microsoft Word.|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Üst öğe](../extensibility/parent-element.md)|İsteğe bağlı. Düğmenin üst öğesi.|
|[Simge öğesi](../extensibility/icon-element.md)|İsteğe bağlı. Düğmeyle ilişkili simge.|
|[Komut bayrağı öğesi](../extensibility/command-flag-element.md)|Gereklidir. Bir Düğme için geçerli CommandFlag değerleri aşağıdaki gibidir.<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibility<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> - Pict<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - TextChanges<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> - TextOnly|
|[Dizeler öğesi](../extensibility/strings-element.md)|Gereklidir. Alt [ButtonText öğesi](../extensibility/buttontext-element.md) tanımlanmalıdır.|
|Ek Açıklama|İsteğe bağlı açıklama.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Düğmeler öğesi](../extensibility/buttons-element.md)|Gruplar Düğmesi öğeleri.|

## <a name="example"></a>Örnek
 Aşağıdaki örnek bir *.vsct dosyasındaki bir düğmeyi* tanımlar.

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
