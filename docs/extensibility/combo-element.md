---
title: Birleşik Giriş Öğesi | Microsoft Docs
description: 'Combo öğesi, birleşik giriş kutusunda görünen komutları tanımlar. Dört tür vardır: DropDownCombo, DynamicCombo, IndexCombo ve MRUCombo.'
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 39f30058329172ea542b17e37eee0f8645b0bb18
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058129"
---
# <a name="combo-element"></a>Birleşik giriş öğesi
Birleşik giriş kutusunda görünen komutları tanımlar. Dört tür birleşik giriş kutusu vardır: DropDownCombo, DynamicCombo, IndexCombo ve MRUCombo.

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
|guid|Gereklidir. GUID/ID komut tanımlayıcısının GUID'si.|
|kimlik|Gereklidir. GUID/ID komut tanımlayıcısının kimliği.|
|defaultWidth|Gereklidir. Birleşik giriş kutusu için piksel genişliğini belirten bir tamsayı.|
|idCommandList|Gereklidir. Birleşik giriş kutusunda görüntülenecek öğelerin listesini almak için etkin komut hedefine gönderilen kimlik. Kimlik, denetimle aynı GUID kapsamında olur.|
|Öncelik|İsteğe bağlı. Önceliği belirten sayısal bir değer.|
|tür|İsteğe bağlı. Düğmenin türünü belirten numaralandı bir değer.<br /><br /> Verilmezse Düğme'i kullanır.<br /><br /> DropDownCombo<br /> VSPackage, bu birleşik giriş kutusunun içeriğini doldurmakla sorumludur. Kullanıcı bu açılan kutunun metin kutusuna herhangi bir şey yazamaz.<br /><br /> DynamicCombo<br /> VSPackage, bu birleşik giriş kutusunun içeriğini doldurmakla sorumludur. Kullanıcı bu birleşik birleşik arabirimi düzenleyebilir ve içinde öğeleri de seçerek.<br /><br /> IndexCombo<br /> DynamicCombo ile aynı, ancak metni yerine öğenin dizinini yükselter.<br /><br /> MRUCombo<br /> VSPackage adına tümleşik geliştirme ortamı (IDE) tarafından doldurulur.  Kullanıcı bu birleşik giriş kutusunda düzenleyebilir. IDE, birleşik giriş başına en fazla son 16 girişi anımsar.<br /><br /> Kullanıcı birleşik giriş kutusunda bir şey seçer veya yeni bir şey girer, IDE uygun VSPackage'ı bilgiyletir.|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Üst|İsteğe bağlı. Düğmenin üst öğesi.|
|CommandFlag|Gereklidir. Bkz. [Komut bayrağı öğesi.](../extensibility/command-flag-element.md) Bir Düğme için geçerli CommandFlag değerleri aşağıdaki gibidir.<br /><br /> - CaseSensitive<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DynamicVisibility<br /><br /> - FilterKeys<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - StretchHorizontally|
|Dizeler|Gereklidir. Bkz. [Dizeler öğesi.](../extensibility/strings-element.md) Alt ButtonText öğesi tanımlanmalıdır.|
|Ek Açıklama|İsteğe bağlı açıklama.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Commands öğesi](../extensibility/commands-element.md)|VSPackage araç çubuğunda komut koleksiyonunu temsil eder.|

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
- [Visual Studio tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
