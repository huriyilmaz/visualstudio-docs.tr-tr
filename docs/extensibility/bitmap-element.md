---
title: Bitmap Öğesi | Microsoft Dokümanlar
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
ms.openlocfilehash: 2d663351aad7d381dd5bfe4cbaa0a263cc70b821
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739999"
---
# <a name="bitmap-element"></a>Bitmap öğesi
Bir bit eşlemi tanımlar. Bit eşlemi bir kaynaktan veya dosyadan yüklenir.

## <a name="syntax"></a>Sözdizimi

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Guıd|Gereklidir. GUID/ID komut tanımlayıcısının GUID'i.<br /><br /> Bitmap için kılavuz özniteliği herhangi bir VSPackage veya diğer komut grubu ile ilişkili değildir.  Bitmap tanımına özgü olmalı ve başka bir amaç için kullanılmamalıdır.|
|Resid|GUID/ID komut tanımlayıcısının kimliği. ResID veya href özniteliği gereklidir.<br /><br /> ResID özniteliği, komut tablosu birleştirme sırasında yüklenecek bit eşleme şeridini belirleyen bir gerçek kaynağı kimliğidir.  Komut tablosu yüklenirken, kaynak kimliği tarafından belirtilen bit eşlemleri aynı modülün kaynağından yüklenir.|
|usedList|resID özniteliği varsa gereklidir. Bitmap şeridinde kullanılabilir görüntüleri seçer.|
|Href|Bit haritasına giden yol. ResID veya href özniteliği gereklidir.<br /><br /> Include yolu, ortaya çıkan ikiliye katıştırılmış olan belirtilen görüntü dosyası için aranır.  Komut tablosu birleştirme sırasında, görüntü kopyalanır ve ek kaynak arama veya yük gereklidir.  usedList özniteliği yoksa, şeritteki tüm görüntüler kullanılabilir. **Not:**  Görüntüler *.bmp*, *.png*ve *.gif*içeren çeşitli biçimlerden birinde sağlanabilir.  Derleyicinin önceki sürümleri, kısmi saydamlık için alfa bilgisine sahip 32 bit eşlemi görüntülerini desteklemedi. Bu sürümler için geçici çözüm *.png* biçimini kullanmaktır.|
|Koşul|İsteğe bağlı. Bkz. [Koşullu öznitelikler.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Biteşler öğesi](../extensibility/bitmaps-element.md)|Bitmap öğelerini gruplar.|

## <a name="example"></a>Örnek

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio komut tablosu (.vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
