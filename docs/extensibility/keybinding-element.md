---
title: KeyBinding öğesi | Microsoft Docs
description: KeyBinding öğesi komutların klavye kısayollarını belirler. Komutlarda kendileriyle ilişkilendirilmiş tek ve çift anahtar bağlamaları bulunabilir.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 832dd4319a581dad66fb85215c66bc85cf21e08d
ms.sourcegitcommit: 1c0eda2db1b1fff9595ca644503f467bf3e223e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "137094854"
---
# <a name="keybinding-element"></a>KeyBinding öğesi
KeyBinding öğesi komutların klavye kısayollarını belirler.

 Komutlarda kendileriyle ilişkilendirilmiş tek ve çift anahtar bağlamaları bulunabilir.  +  **Kaydet** komutu için tek tuşla bağlama bir örnektir. Çift anahtar bağlamaları bir komutun tetiklenmesi için iki ardışık anahtar kombinasyonu gerektirir. Çift anahtar bağlamasının bir örneği **Ctrl + k**,**Ctrl + k** , bir yer işareti ayarlamak için bir örnektir.

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
|düzenleyici|Gereklidir. Düzenleyici GUID 'SI, bu klavye kısayolunun etkin olacağı düzenleme bağlamını gösterir. Genel bağlama kapsamı değeri "guidVSStd97" değeridir.|
|key1|Gereklidir. Geçerli değerler, tüm tyıılabilen alfasayısal değerleri ve bundan önce 0x ve [VK_constants](/windows/desktop/inputdev/virtual-key-codes)olan iki basamaklı onaltılık değerler içerir.|
|mod1|İsteğe bağlı. Boşluk ile ayrılmış **Denetim**, **alt** ve **vardiyanın** birleşimi.|
|key2|İsteğe bağlı. Geçerli değerler, tüm tyıılabilen alfasayısal değerleri ve bundan önce 0x ve [VK_constants](/windows/desktop/inputdev/virtual-key-codes)olan iki basamaklı onaltılık değerler içerir.|
|mod2|İsteğe bağlı. Boşluk ile ayrılmış **Denetim**, **alt** ve **vardiyanın** birleşimi.|
|öykünücü|İsteğe bağlı.|
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Üst||
|Ek Açıklama||

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[KeyBindings öğesi](../extensibility/keybindings-element.md)|Anahtar bağlama öğelerini ve diğer KeyBindings gruplandırmaları gruplandırır.|

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
- [komut tablosu (. vsct) dosyaları Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
