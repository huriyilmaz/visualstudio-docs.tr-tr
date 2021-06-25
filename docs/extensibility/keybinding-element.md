---
title: KeyBinding Öğesi | Microsoft Docs
description: KeyBinding öğesi, komutlar için klavye kısayollarını belirtir. Komutlarla ilişkilendirilmiş tek ve çift anahtar bağlamaları olabilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6afd0a9658f088b66f2c18c632ffcd7b9a09f555
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898867"
---
# <a name="keybinding-element"></a>KeyBinding öğesi
KeyBinding öğesi, komutlar için klavye kısayollarını belirtir.

 Komutlarla ilişkilendirilmiş tek ve çift anahtar bağlamaları olabilir. Tek tuş bağlamaya örnek olarak Kaydet **komutu için Ctrl** + **S** **kullanılır.** Çift anahtar bağlamaları, bir komutu tetiklemek için iki anahtar bileşimi gerektirir. Çift tuş bağlamaya örnek olarak yer işareti <strong>ayarlamak için Ctrl *+</strong> K <strong>,</strong>Ctrl <strong>+</strong> K** kullanılır.

## <a name="syntax"></a>Syntax

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|guid|Gereklidir.|
|kimlik|Gereklidir.|
|düzenleyici|Gereklidir. Düzenleyici GUID'si, bu klavye kısayolu için etkin olacak düzenleme bağlamını gösterir. Genel bağlama kapsamı değeri "guidVSStd97" şeklindedir.|
|key1|Gereklidir. Geçerli değerler yazım hatasına neden olan tüm alfasayısal değerleri ve 0x ve öncesinde iki basamaklı onaltılık değerleri [VK_constants.](/windows/desktop/inputdev/virtual-key-codes)|
|mod1|İsteğe bağlı. Boşlukla ayrılmış **Ctrl,** **Alt** ve **Shift** tuş bileşimi.|
|key2|İsteğe bağlı. Geçerli değerler yazım hatasına neden olan tüm alfasayısal değerleri ve 0x ve öncesinde iki basamaklı onaltılık değerleri [VK_constants.](/windows/desktop/inputdev/virtual-key-codes)|
|mod2|İsteğe bağlı. Boşlukla ayrılmış **Ctrl,** **Alt** ve **Shift** tuş bileşimi.|
|öykünücü|İsteğe bağlı.|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Üst||
|Ek Açıklama||

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[KeyBindings öğesi](../extensibility/keybindings-element.md)|KeyBinding öğelerini ve diğer KeyBindings gruplamalarını gruplar.|

## <a name="example"></a>Örnek

```
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>Ayrıca bkz.
- [KeyBindings öğesi](../extensibility/keybindings-element.md)
- [Visual Studio tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
