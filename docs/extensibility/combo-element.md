---
title: Birleşik öğe öğesi | Microsoft Docs
description: 'Combo öğesi, Birleşik giriş kutusunda görünen komutları tanımlar. Dört tür vardır: DropDownCombo, DynamicCombo, IndexCombo ve MRUCombo.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 431d68b6e545506f5fc90cc5a98a52dd4f1c33ad
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904961"
---
# <a name="combo-element"></a>Combo öğesi
Birleşik giriş kutusunda görünen komutları tanımlar. Aşağıda gösterildiği gibi dört tür Birleşik giriş kutusu vardır: DropDownCombo, DynamicCombo, IndexCombo ve MRUCombo.

## <a name="syntax"></a>Syntax

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
|guid|Gereklidir. GUID/ID komut tanımlayıcısının GUID 'SI.|
|kimlik|Gereklidir. GUID/ID komut tanımlayıcısının KIMLIĞI.|
|defaultWidth|Gereklidir. Birleşik giriş kutusu için piksel genişliğini belirten bir tamsayı.|
|ıdcommandlist|Gereklidir. Birleşik giriş kutusunda görüntülenecek öğe listesini almak için etkin komut hedefine gönderilen bir KIMLIK. KIMLIK, denetimle aynı GUID kapsamında olacaktır.|
|Priority|İsteğe bağlı. Önceliği belirten sayısal bir değer.|
|tür|İsteğe bağlı. Düğme türünü belirten, numaralandırılmış bir değer.<br /><br /> Verilmezse, düğme kullanır.<br /><br /> DropDownCombo<br /> VSPackage, bu Birleşik giriş kutusunun içeriğini doldurmaktan sorumludur. Kullanıcı bu açılan kutunun metin kutusuna herhangi bir şey yazamaz.<br /><br /> DynamicCombo<br /> VSPackage, bu Birleşik giriş kutusunun içeriğini doldurmaktan sorumludur. Kullanıcı bu Birleşik eklentiyi düzenleyebilir ve içindeki öğeleri de seçebilir.<br /><br /> IndexCombo<br /> DynamicCombo ile aynıdır, ancak kendi metni yerine öğenin dizinini oluşturur.<br /><br /> MRUCombo<br /> VSPackage adına tümleşik geliştirme ortamı (IDE) tarafından doldurulmuştur.  Kullanıcı bu Birleşik giriş kutusunda düzenleyebilir. IDE, Birleşik giriş kutusu başına son 16 girişe kadar hatırlar.<br /><br /> Kullanıcı Birleşik giriş kutusunda bir şey seçtiğinde veya yeni bir şey girerse, IDE uygun VSPackage 'a bildirim gönderir.|
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Üst|İsteğe bağlı. Düğmenin üst öğesi.|
|CommandFlag|Gereklidir. Bkz. [komut bayrağı öğesi](../extensibility/command-flag-element.md). Bir düğme için geçerli CommandFlag değerleri aşağıdaki gibidir.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -Filtre tuşları<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -Üzerinde yatay|
|Dizeler|Gereklidir. Bkz. [dizeler öğesi](../extensibility/strings-element.md). Alt ButtonText öğesi tanımlanmalıdır.|
|Ek Açıklama|İsteğe bağlı açıklama.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Commands öğesi](../extensibility/commands-element.md)|VSPackage araç çubuğundaki komutların koleksiyonunu temsil eder.|

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
- [Visual Studio komut tablosu (. vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
