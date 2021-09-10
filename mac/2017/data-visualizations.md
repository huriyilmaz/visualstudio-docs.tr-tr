---
title: Hata Ayıklama - Veri Görselleştirmeleri
description: Hata ayıklama, programlamanın ortak ve gerekli bir bölümüdür. Mac için Visual Studio, hata ayıklamayı kolaylaştıran bir özellik paketi içerir. Bu makalede, hata ayıklayıcısında nesneleri incelerken görüntülen 7.000 veri görselleştirmesi inceler.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 3355b81406d2b510dc13604a026bcd014bf9dbcb
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962132"
---
# <a name="data-visualizations"></a>Veri görselleştirmeleri

Mac için Visual Studio hata ayıklayıcı için ui desteği içerir ve hata ayıklama sırasında bir değişken, alan veya özelliğin değerlerinin görselleştirmelerine izin verir. Bu veri görselleştiricileri verilerin genişletilmiş bir sürümünü gösterir ve geliştiricilerin bilinen yapıları (örneğin bir renk yapısının rengini gösterme) incelemesine olanak sağlar.

Hata ayıklama Yerel  **panelinin** görselleştiricileri, değerin sağ tarafından görüntülenen önizleme simgesine tıklarsanız, kullanıcı satırın üzerine geldiğinde görüntülenebilir:

![Yerel Pad](media/data-visualizations-image9.png)

Aşağıdaki listede, hata ayıklama sırasında kullanılabilen yeni görselleştirmelerin birçoğuna Mac için Visual Studio.

## <a name="point"></a>Nokta
iOS ve Mac'te Point/PointF veya CGPoint, hata ayıklama panelinin X ve Y değerlerini gösteren bir tuple olarak işler:

![Nokta Görselleştirme](media/data-visualizations-image10.png)

## <a name="size"></a>Boyut
iOS ve Mac'te Size/SizeF veya CGSize, dikdörtgen olarak işleme alır. Bir boyut 250 px'i geçene kadar ölçeklendirilir ve bu noktada dikdörtgeni en büyük boyuta 250 px olarak ölçeklendirir:

[Boyut Görselleştirmesi](media/data-visualizations-image11.png)

## <a name="rectangle"></a>Dikdörtgen
iOS ve Mac'te Dikdörtgen/DikdörtgenF veya CGRect, boyutları ve kaynağı görüntüler. Boyut'a benzer şekilde, boyut 250 px'i geçene kadar ölçeklendirilir:

![Dikdörtgen Görselleştirme](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Koordinat
Koordinatlar, konumun merkeze sabitlenmiş olduğu bir haritada çizildi:

[Koordinat Görselleştirmesi](media/data-visualizations-image13.png)

## <a name="color"></a>Renk
Bu, renk önizlemesini, RGBA bileşenlerini, Hue-Saturation-Lightness değerlerini ve rengin altılık değerini gösteren UIColor, CGColor ve Color özelliklerini görüntüler:

![Renk Görselleştirmesi](media/data-visualizations-image14.png)

## <a name="images"></a>Görüntüler

Medya, en fazla 250 px boyutuna kadar ölçeklendirilen ve görüntü 250 px'i aştıklarında sığacak şekilde ölçeklendirilen medyadır:

![Görüntü Görselleştirme](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>Nedener Eğrileri

Görselleştirici bir `NSBezierPath` görüntüler:

![Bezier EğriSi Görselleştirmesi](media/data-visualizations-image16.png)

## <a name="string"></a>Dize

100 karakterden kısa bir dize önizleme olmadan tam olarak görüntülenir. Daha uzun dizeler önizlemede tam olarak görüntülenir. Dizeler düzenlenebilir ve görselleştiriciye bir düzenleme düğmesi eşlik ettiği için dize değerinin önizlemede veya Dize Değeri Düzenleyicisi'nde düzenlenebilir. Bu düğme aşağıda gösterilmiştir:

![Dize Görselleştirmesi](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Küçük Dizeler:
![Küçük Dize Görselleştirmesi](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Orta Uzunlukta Dizeler:
![Orta Dize Görselleştirmesi](media/data-visualizations-image19.png)

### <a name="editor"></a>Düzenleyicisi:

![Düzenleyici Görselleştirmesi](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>Ienumerable

IEnumerable tüm değerleri numaralar; Değerleri Göster düğmesine tıklayarak her bir değeri **görüntülayabilirsiniz.** IEnumerable seçeneği, kendi hata ayıklayıcı görselleştiricilerine sahip olduğu için , , gibi nesneler `Array` `ArrayList` için değerleri `List<>` `Dictionary<,>` görüntülemez.

![IEnumerable Görselleştirmesi](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Diğer Görselleştiriciler

Kendi satır içi görselleştiricileri de olan diğer bazı türler aşağıda listelenmiştir:

![Diğer Görselleştirmeler](media/data-visualizations-image23.png)

* **Temel Türler**
  * Bu, ilkel türün ham değerini gösterir.
* **Sabit listesi**
  * Bu, enum Türü niteleyicisi olmadan alan değerini görüntüler.
* **Tuple**
  * Biçiminde görüntülenir (,)
* **Null**
  * "null" değerini gösterir.
* **URL**
  * Bu, tıklanabilir bir köprü görüntüler.
* **Intptr**
  * Bu, IntPtr'nin onaltılık bir gösterimini görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatikler ve Yereller pencerelerinde değişkenleri inceleme (Visual Studio üzerinde Windows)](/visualstudio/debugger/autos-and-locals-windows)
- [Görselleştiricide dizeleri görüntüleme (Visual Studio üzerinde Windows)](/visualstudio/debugger/string-visualizer-dialog-box)