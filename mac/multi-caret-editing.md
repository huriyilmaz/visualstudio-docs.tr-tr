---
title: Çoklu giriş işareti düzenleme
description: Mac için Visual Studio kod düzenlenirken birden fazla konuma metin ekleyin.
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 08/19/2019
ms.topic: reference
ms.openlocfilehash: 36852fe81906b49dd9eb174ffd89bc67630a9bb6
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805552"
---
# <a name="multi-caret-editing"></a>Çoklu giriş işareti düzenleme

Çoklu giriş işareti düzenlemesi, tek seferde _n_ sayıda ekleme noktası eklemenize olanak tanır. Çoklu giriş işareti modundayken, belgenize fare tıklamaları veya klavye komutları aracılığıyla ek Evcil hayvan ekleyebilirsiniz. Birincil giriş işareti kırmızı bir imleç ile gösterilir ve ikincil sepetler açık mavi renkte bulunur. Çoklu giriş işareti düzenleme modu anahtar aracılığıyla devre dışı bırakılabilir `ESC` .

## <a name="enabling-multi-caret-editing"></a>Çoklu klavyeyle düzenleme etkinleştiriliyor

### <a name="keyboard"></a>Klavye

Klavye aracılığıyla çok şapka modunu birkaç şekilde etkinleştirebilirsiniz. Aşağıdaki tabloda, çok giriş işareti düzenlemesini belirli modlar için kullanılabilecek klavye kısayolları verilmiştir:

| Kısayol tuşu  | Eylem                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Sonraki eşleşen giriş işaretini Ekle    | 
|  ⌥⇧;   | Her eşleşen giriş Ekle | 
|  ⌥⇧,   | Son giriş işaretini kaldır             | 
|  ⌥⇧/   | Son giriş işaretini aşağı taşı          | 

Bu davranışların her biri, komutu çağırdığınızda giriş işaretinin geçerli konumuna bağlanır. Örneğin, giriş işareti "ad" sözcüğünün başlısın ve "tüm eşleştirmeyle" maetleri Ekle "seçeneğini çağırırsanız (⌥ ⇧;) geçerli belgenizdeki "Name" sözcüğünün her bir örneği, sözcüğün başlangıcına eklenecek bir giriş işaretine sahip olacaktır. Benzer şekilde, "sonraki eşleşen giriş işaretini Ekle" (⌥ ⇧.) komutunu çağırırsanız, "Name" sözcüğünün bir sonraki örneğine bir giriş işareti konur. Bu komut birden çok kez çağrılabilir.

![Çoklu giriş işareti klavyesi](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Fare/Dokunmatik yüzey

İmlecinizi kullanarak, birden çok Evcil hayvan için belirli ekleme noktalarını seçebilirsiniz. Klavye kısayolları eşleşen dizelere bağlıyken, imlecin bulunduğu belgede herhangi bir yere bir giriş işaretini el ile ekleyebilirsiniz. Sepetlerin ayarlandıktan sonra her biri, klavyenizde yazdığınız önemli girdileri yankıdan alır.

Fareyi kullanarak birden çok Evcil hayvan eklemek için, ⌘ ⌥ tuşlarına basılı tutmanız ve sepetlerin girilmesini istediğiniz yere tıklamalısınız. ⌘ ⌥ Anahtarları tutulduğu sürece ekleme modunda olursunuz. Yanlış bir konuma bir giriş işareti eklerseniz, ⌘ ⌥ 'yi basılı tutmaya ve aynı alanı yeniden tıklatmaya devam ederek giriş işaretini kaldırabilirsiniz. İstediğiniz yerde yer alan tüm Evcil hayvan varsa, ⌘ ⌥ tuşlarına basmayı durdurun ve yazmaya başlayın. Aşağıdaki GIF, hem bir ekleme noktası kümesi seçip hem de hatalı ayarlanmış noktaları kaldırarak gösterir.

![Çoklu giriş işareti faresi](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Ayrıca bkz.

- [hızlı eylemler (Windows Visual Studio)](/visualstudio/ide/quick-actions)
- [kodu yeniden düzenleme (Windows Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
