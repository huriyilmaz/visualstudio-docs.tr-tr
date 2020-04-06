---
title: Combo Element | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ff9d9e20ec221a86f1cce5f9c43a4e47ed6dc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739812"
---
# <a name="combo-element"></a>Açılan eleman
Açılan kutuda görünen komutları tanımlar. Açılan kutular dört türü vardır, aşağıdaki gibi: DropDownCombo, DynamicCombo, IndexCombo ve MRUCombo.

## <a name="syntax"></a>Sözdizimi

```xml
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">
  <Parent>... </Parent
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</combo>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Guıd|Gereklidir. GUID/ID komut tanımlayıcısının GUID'i.|
|id|Gereklidir. GUID/ID komut tanımlayıcısının kimliği.|
|varsayılanGenişlik|Gereklidir. Açılan kutu için piksel genişliğini belirten bir tamsayı.|
|idCommandList|Gereklidir. Açılan kutuda görüntülenecek öğelerin listesini almak için etkin komut hedefine gönderilen bir kimlik. Kimlik, denetimle aynı GUID kapsamında olacaktır.|
|Öncelik|İsteğe bağlı. Önceliği belirten sayısal bir değer.|
|type|İsteğe bağlı. Düğmetürünü belirten numaralandırılmış bir değer.<br /><br /> Verilmediği takdirde Düğme'yi kullanır.<br /><br /> DropDownCombo<br /> VSPackage bu açılan kutunun içeriğini doldurmakla yükümlüdür. Kullanıcı bu açılır metin kutusuna hiçbir şey yazamaz.<br /><br /> DynamicCombo<br /> VSPackage bu açılan kutunun içeriğini doldurmaktan sorumludur. Kullanıcı bu açılan'ı ve içinde öğeleri seçebilir.<br /><br /> IndexCombo<br /> DynamicCombo ile aynı, ancak metnin indeksini yükseltmesi dışında.<br /><br /> MRUCombo<br /> VSPackage adına entegre geliştirme ortamı (IDE) tarafından doldurulur.  Kullanıcı bu açılan kutuda edinebilir. IDE, açılan kutu başına son 16 girişi hatırlar.<br /><br /> Kullanıcı açılan kutuda bir şey seçtiğinde veya yeni bir şey girdiğinde, IDE uygun VSPackage'ı bildirir.|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Üst|İsteğe bağlı. Düğmenin ana öğesi.|
|Komut Bayrağı|Gereklidir. Bkz. [Komut bayrak öğesi.](../extensibility/command-flag-element.md) Bir Düğme için geçerli CommandFlag değerleri aşağıdaki gibidir.<br /><br /> - CaseSensitive<br /><br /> - CommandWellOnly<br /><br /> - Varsayılan Devre<br /><br /> - VarsayılanGörünmez<br /><br /> - Dinamik Görünürlük<br /><br /> - Filtre Tuşları<br /><br /> - Simgeve Metin<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomizE<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - StretchYatay|
|Dizeler|Gereklidir. Bkz. [Dizeleri öğesi.](../extensibility/strings-element.md) Alt ButtonText öğesi tanımlanmalıdır.|
|Ek Açıklama|İsteğe bağlı yorum.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Komutlar öğesi](../extensibility/commands-element.md)|VSPackage araç çubuğundaki komutların toplanmasını temsil eder.|

## <a name="example"></a>Örnek

```xml
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>

<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  priority="0x0500" type="DropDownCombo" defaultWidth="100"
  idCommandList="cmdidGetInsertOptionsList">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
