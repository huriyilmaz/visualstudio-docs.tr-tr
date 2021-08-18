---
title: Öğe Tanımlama | Microsoft Docs
description: Define öğesi bir sembol adı ve değer çifti tanımlar. Bu sembol koşullu öznitelikler tarafından değerlendir olabilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 87823d3f3aa2e8927187f9395f6c02833b1076b8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122087216"
---
# <a name="define-element"></a>Define öğesi
Bir sembol adı ve değer çifti tanımlar. Bu sembol koşullu öznitelikler tarafından değerlendir olabilir. Daha fazla bilgi için [bkz. Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md) Ayrıca [bkz. Semboller öğesi.](../extensibility/symbols-element.md)

## <a name="syntax"></a>Syntax

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|name|Gereklidir. Sembolün adı:<br /><br /> name="Mode"|
|değer|Gereklidir. Sembolün değeri:<br /><br /> value="Standard"|
|Koşul|İsteğe bağlı. Daha fazla bilgi için [bkz. Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CommandTable öğesi](../extensibility/commandtable-element.md)|VSPackage'ın tümleşik geliştirme ortamına (IDE) sağladığı komutları temsil eden tüm öğeleri tanımlar. Örneğin menü öğeleri, menüler, araç çubukları ve birleşik giriş kutuları.|

## <a name="example"></a>Örnek

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
