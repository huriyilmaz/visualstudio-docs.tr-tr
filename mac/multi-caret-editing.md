---
title: Çoklu giriş işareti düzenleme
description: Uygulama içinde kod düzenlerken birden çok konuma metin Mac için Visual Studio.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964806"
---
# <a name="multi-caret-editing"></a>Çoklu giriş işareti düzenleme

Çoklu giriş karakteri düzenleme, tek bir _anda n_ sayıda ekleme noktası eklemenize olanak sağlar. Çoklu klavye modundayken, fare tıklamaları veya klavye komutları aracılığıyla belgenize ek tuşlar ekleyebilirsiniz. Birincil caret kırmızı bir imleçle gösterilirken ikincil caret'ler açık mavi renkte gösterilir. Çoklu imtiyazlı düzenleme modu, anahtar aracılığıyla devre dışı `ESC` bırakılabilir.

## <a name="enabling-multi-caret-editing"></a>Çoklu imtiyaz düzenlemeyi etkinleştirme

### <a name="keyboard"></a>Klavye

Klavye aracılığıyla çoklu klavye modunu çeşitli yollarla etkinleştirebilirsiniz. Aşağıdaki tabloda, çoklu giriş imtiyazlı düzenlemenin belirli modlarını girmek için kullanılabilen klavye kısayolları sağlanmaktadır:

| Hotkey  | Eylem                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Sonraki eşleşen imtiyazı ekle    | 
|  ⌥⇧;   | Eşleştirmeye hiç caret ekleme | 
|  ⌥⇧,   | Son imtiyazı kaldırma             | 
|  ⌥⇧/   | Son dikkati aşağı taşı          | 

Komutu çağırarak bu davranışların her biri, caret'in geçerli konumunun sabiti olur. Örneğin, caret "name" sözcüğün başında ise ve "Eşleşen hiç ekleme ekleme" çağrılsa (⌥⇧;) Geçerli belgeniz içinde "name" sözcüğün her örneği, sözcüğün başlangıcına bir caret eklenir. Benzer şekilde, "Insert next matching caret" (⌥⇧.) komutunu çağırırsanız, "name" sözcüğün sonraki örneğine bir caret yerleştirilir. Bu komut birden çok kez çağrılabilir.

![çoklu klavye](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Fare/dokunmatik yüzey

İmlecinizi kullanarak, birden çok giriş noktanız için belirli ekleme noktalarını serbest sızdırabileceksiniz. Klavye kısayolları eşleşen dizelere bağlıyken, imleçle belgenin herhangi bir yerine el ile bir caret ekleyebilirsiniz. Giriş girişlerinin her biri, klavyenizde yazacakları tuş girişlerini yankılar.

Fareyi kullanarak birden çok giriş kartı eklemek için, giriş ⌘⌥ basılı tutmalı ve giriş girişlerini istediğiniz yere tıklamalısiniz. Yeni anahtarlar tutulacak sürece ekleme ⌘⌥ olursunuz. Yanlış bir konuma bir caret eklersanız, aynı alanı basılı tutmaya devam ⌘⌥ aynı alana tekrar tıklayarak caret'i kaldırabilirsiniz. Tüm caret'leri istediğiniz yerde bulunduktan sonra, tüm tuşlara ⌘⌥ ve yazmaya başlayın. Aşağıdaki GIF hem ekleme noktası kümesi seçmeyi hem de hatalı ayarlanmış noktaları kaldırmayı gösteriyor.

![çoklu caret fare](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler (Visual Studio Windows)](/visualstudio/ide/quick-actions)
- [Kodu yeniden düzenleme (Visual Studio üzerinde Windows)](/visualstudio/ide/refactoring-in-visual-studio)
