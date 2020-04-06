---
title: Düğme Elemanı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05bd73764e96a27a92d741f144c222acc48fa518
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739935"
---
# <a name="button-element"></a>Düğme öğesi
Kullanıcının etkileşimkurabileceği bir öğe tanımlar. Düğmeler farklı olabilir: Düğme, MenuButton ve SplitDropDown.

## <a name="syntax"></a>Sözdizimi

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
|Guıd|Gereklidir. GUID/ID komut tanımlayıcısının GUID'i.|
|id|Gereklidir. GUID/ID komut tanımlayıcısının kimliği.|
|Öncelik|İsteğe bağlı. Önceliği belirten sayısal bir değer.|
|type|İsteğe bağlı. Düğme türünü belirten numaralandırılmış bir değer.<br /><br /> Verilmediği takdirde Düğme'yi kullanır.<br /><br /> Düğme<br /> Araç çubuklarında (genellikle simgesel düğme olarak), menülerde ve bağlam menülerinde görünen standart bir komut.<br /><br /> Menü Düğmesi<br /> Komutu yürütmeyen, ancak başka bir menü üreten bir menü öğesi.<br /><br /> SplitDropDown<br /> Microsoft Word'deki standart araç çubuğundaki Geri Alma ve Yeniden Yap düğmeleri gibi denetimler.|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Üst öğe](../extensibility/parent-element.md)|İsteğe bağlı. Düğmenin ana öğesi.|
|[Simge öğesi](../extensibility/icon-element.md)|İsteğe bağlı. Düğmeyle ilişkili simge.|
|[Komut bayrağı öğesi](../extensibility/command-flag-element.md)|Gereklidir. Bir Düğme için geçerli CommandFlag değerleri aşağıdaki gibidir.<br /><br /> - İzin Params<br /><br /> - CommandWellOnly<br /><br /> - Varsayılan Devre<br /><br /> - VarsayılanGörünmez<br /><br /> - DontÖnbellek<br /><br /> - DynamicItemStart<br /><br /> - Dinamik Görünürlük<br /><br /> - FixMenuController<br /><br /> - Simgeve Metin<br /><br /> - NoButtonCustomizE<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - NoShowonMenuController<br /><br /> - Pict<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - Metin Değişiklikleri<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> - TextOnly|
|[Dizeleri öğesi](../extensibility/strings-element.md)|Gereklidir. Alt [ButtonText öğesi](../extensibility/buttontext-element.md) tanımlanmalıdır.|
|Ek Açıklama|İsteğe bağlı yorum.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Düğmeler öğesi](../extensibility/buttons-element.md)|Düğme öğelerini grupla.|

## <a name="example"></a>Örnek
 Aşağıdaki örnekte *.vsct* dosyasındaki bir düğme tanımlanır.

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
- [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
