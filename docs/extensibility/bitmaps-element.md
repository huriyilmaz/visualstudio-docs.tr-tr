---
title: Bit eşlemler öğesi | Microsoft Docs
description: Bit eşlemler öğesi bir veya daha fazla bit eşlem öğesini gruplandırır. Bu makale, bit eşlem öğesine bir örnek içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc17162c8d66df99eefe721589863ee4221c8602
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068212"
---
# <a name="bitmaps-element"></a>Bit eşlemler öğesi
[Bit eşlem öğesi](../extensibility/bitmap-element.md) öğelerini gruplandırır.

## <a name="syntax"></a>Syntax

```
<Bitmaps>
  <Bitmap>... </Bitmap>
  <Bitmap>... </Bitmap>
</Bitmaps>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Bit eşlemler öğesi](../extensibility/bitmaps-element.md)|Bit eşlem öğelerini gruplandırır.|
|[Bit eşlem öğesi](../extensibility/bitmap-element.md)|Bit eşlemi tanımlar.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Commands öğesi](../extensibility/commands-element.md)|VSPackage araç çubuğundaki komutların koleksiyonunu temsil eder.|

## <a name="example"></a>Örnek

```
<Bitmaps>
  <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
  <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
    usedList="1, 2, 3, 4"/>
</Bitmaps>
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackages Kullanıcı arabirimi öğeleri ekleme](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
