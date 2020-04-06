---
title: Anahtar Bağlama Elemanı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b458e70a9a85c11707c50da2e16e3aa73f51bc12
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703138"
---
# <a name="keybinding-element"></a>AnahtarBağlama öğesi
KeyBinding öğesi komutlar için klavye kısayollarını belirtir.

 Komutların hem tek hem de çift anahtar bağlamaları bunlarla ilişkili olabilir. Tek bir anahtar bağlama örneği **Kaydet** komutu için **Ctrl**+**S'dir.** Çift anahtar bağlamaları bir komutu tetiklemek için art arda iki anahtar birleşimleri gerektirir. Çift anahtar bağlama bir örnek <strong>Ctrl*+</strong>K<strong>+</strong><strong>,</strong>Ctrl K** bir yer imi ayarlamak tır.

## <a name="syntax"></a>Sözdizimi

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Guıd|Gereklidir.|
|id|Gereklidir.|
|düzenleyici|Gereklidir. Düzenleyici GUID, bu klavye kısayolu etkin olacak düzenleme bağlamını gösterir. Genel bağlama kapsamı değeri "guidVSStd97"dir.|
|key1|Gereklidir. Geçerli değerler tüm tiplenebilir alfanümerikve ayrıca 0x ve [VK_constants](/windows/desktop/inputdev/virtual-key-codes)öncesinde iki basamaklı hekzadesmal değerleri içerir.|
|mod1|İsteğe bağlı. **Ctrl,** **Alt**ve **Shift'in** herhangi bir birleşimi boşlukla ayrılmıştır.|
|key2|İsteğe bağlı. Geçerli değerler tüm tiplenebilir alfanümerikve ayrıca 0x ve [VK_constants](/windows/desktop/inputdev/virtual-key-codes)öncesinde iki basamaklı hekzadesmal değerleri içerir.|
|mod2|İsteğe bağlı. **Ctrl,** **Alt**ve **Shift'in** herhangi bir birleşimi boşlukla ayrılmıştır.|
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
|[KeyBindings öğesi](../extensibility/keybindings-element.md)|Anahtar Bağlama öğelerini ve diğer KeyBindings gruplandırmalarını gruplandırmayı grupla.|

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
- [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
