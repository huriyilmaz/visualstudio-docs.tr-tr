---
title: Bit eşlem öğesi | Microsoft Docs
description: Bit eşlem öğesi bir bit eşlemi tanımlar. Bit eşlem bir kaynaktan ya da bir dosyadan yüklenir. Bu makale bir örnek içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd30cb2d09d042e70b5fc142ac220f2356962146
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974589"
---
# <a name="bitmap-element"></a>Bit eşlem öğesi
Bit eşlemi tanımlar. Bit eşlem bir kaynaktan ya da bir dosyadan yüklenir.

## <a name="syntax"></a>Syntax

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|guid|Gereklidir. GUID/ID komut tanımlayıcısının GUID 'SI.<br /><br /> Bit eşlemin GUID özniteliği herhangi bir VSPackage veya diğer komut grubuyla ilişkili değil.  Bit eşlem tanımının benzersiz olması ve herhangi bir amaçla kullanılmamalıdır.|
|RESID|GUID/ID komut tanımlayıcısının KIMLIĞI. Resd ya da href özniteliği gereklidir.<br /><br /> Resd özniteliği, komut tablosu birleştirme sırasında yüklenecek bit eşlem şeridi belirleyen bir tamsayı kaynak KIMLIĞIDIR.  Komut tablosu yüklenirken, kaynak KIMLIĞI tarafından belirtilen bit eşlemler aynı modülün kaynağından yüklenir.|
|usedList|Resd özniteliği mevcutsa gereklidir. Bit eşlem şeridinde kullanılabilir görüntüleri seçer.|
|değerini|Bit eşlemin yolu. Resd ya da href özniteliği gereklidir.<br /><br /> Dahil edilen ikiliye gömülü olan belirtilen görüntü dosyası için ekleme yolu aranır.  Komut tablosu birleştirme sırasında görüntü kopyalanır ve ek kaynak araması veya yükleme gerekmez.  UsedList özniteliği yoksa, şerit 'teki tüm görüntüler kullanılabilir. **Note:**  Resimler, *. bmp*, *. png* ve *. gif* içeren birkaç biçimden birinde sağlanabilir.  Derleyicinin önceki sürümleri, kısmi saydamlık için alfa bilgilerine sahip 32 bit bit eşlem görüntülerini desteklemez. Bu sürümler için geçici çözüm *. png* biçimini kullanmaktır.|
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Bit eşlemler öğesi](../extensibility/bitmaps-element.md)|Bit eşlem öğelerini gruplandırır.|

## <a name="example"></a>Örnek

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (. vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
