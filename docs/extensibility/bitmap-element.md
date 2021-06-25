---
title: Bitmap Öğesi | Microsoft Docs
description: Bitmap öğesi bir bit eşlem tanımlar. Bit eşlem bir kaynaktan veya bir dosyadan yüklenir. Bu makale bir örnek içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c8f3daf25a3ffe025bcdef65dbaa6def942d0fb4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903326"
---
# <a name="bitmap-element"></a>Bit eşlem öğesi
Bit eşlem tanımlar. Bit eşlem bir kaynaktan veya bir dosyadan yüklenir.

## <a name="syntax"></a>Syntax

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|guid|Gereklidir. GUID/ID komut tanımlayıcısının GUID'si.<br /><br /> Bit eşlem için guid özniteliği herhangi bir VSPackage veya başka bir komut grubuyla ilişkili değildir.  Bit eşlem tanımına özel olmalı ve başka bir amaç için kullanılmamalı.|
|Resid|GUID/ID komut tanımlayıcısının kimliği. resID veya href özniteliği gereklidir.<br /><br /> resID özniteliği, komut tablosu birleştirme sırasında yüklenecek bit eşlem şeridini belirleyen bir tamsayı kaynak kimliğidir.  Komut tablosu yüklendiğinde, kaynak kimliği tarafından belirtilen bit eşlemler aynı modülün kaynağından yüklenir.|
|usedList|resID özniteliği varsa gereklidir. Bit eşlem şeridinde kullanılabilir görüntüleri seçer.|
|Href|Bit eşlem yolu. resID veya href özniteliği gereklidir.<br /><br /> Dahil etmek yolu, sonuçta elde edilen ikili dosyaya eklenmiş olan belirtilen görüntü dosyası için aranır.  Komut tablosu birleştirme sırasında görüntü kopyalanır ve ek kaynak araması veya yüklemesi gerekmez.  usedList özniteliği yoksa şeritte bulunan tüm görüntüler kullanılabilir. **Not:**  Görüntüler,.bmp *,*.png *ve* *.gif.*  Derleyicinin önceki sürümleri kısmi saydamlık için alfa bilgi içeren 32 bit bit eşlem görüntülerini desteklemedi. Bu sürümlerin geçici çözümü,.png *kullanmaktır.*|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Bitmaps öğesi](../extensibility/bitmaps-element.md)|Bit Eşlem öğelerini gruplar.|

## <a name="example"></a>Örnek

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
