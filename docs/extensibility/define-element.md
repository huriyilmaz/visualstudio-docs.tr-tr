---
title: Öğeyi tanımla | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc09de1d822f41b25397c7a56c7cce4449a9e551
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712268"
---
# <a name="define-element"></a>Öğe tanımla
Bir sembol adı ve değer çifti tanımlar. Bu simge koşullu öznitelikler tarafından değerlendirilebilirler. Daha fazla bilgi için bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md). Ayrıca bkz. [Semboller öğesi](../extensibility/symbols-element.md).

## <a name="syntax"></a>Syntax

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|name|Gereklidir. Simgenin adı:<br /><br /> Name = "Mode"|
|değer|Gereklidir. Simgenin değeri:<br /><br /> değer = "standart"|
|Koşul|İsteğe bağlı. Daha fazla bilgi için bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|Bir VSPackage 'ın tümleşik geliştirme ortamına (IDE) sağladığı komutları temsil eden tüm öğeleri tanımlar. Örneğin, menü öğeleri, menüler, araç çubukları ve Birleşik giriş kutuları.|

## <a name="example"></a>Örnek

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (. vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
