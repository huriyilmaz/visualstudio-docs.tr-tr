---
title: Hata Ayıklama - Veri Görselleştirmeleri
description: Hata ayıklama, programlamanın yaygın ve gerekli bir parçasıdır. Mac için Visual Studio, hata ayıklamayı kolaylaştırmak için bir dizi özellik içerir. Bu makalede, hata ayıklama nesneleri denetlenirken görüntülenebilir farklı veri görselleri bakar.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 14696040160dfc33f89b7647fb73b116b41afa16
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "67691739"
---
# <a name="data-visualizations"></a>Veri görselleştirmeleri

Mac için Visual Studio hata ayıklayıcı için ui desteği içerir, hata ayıklama sırasında bir değişken, alan veya özellik değerlerinin görselleştirmeleri izin. Bu veri görselleştiricileri verilerin genişletilmiş bir sürümünü gösterir ve geliştiricilerin bilinen yapıları denetlemesine izin verir, örneğin bir renk yapısının rengini gösterir.

Hata ayıklama **Yerel** pad'deki görselleştiriciler, kullanıcı satırın üzerinde gezinirken değerin sağında görünen önizleme simgesine tıklayarak görüntülenebilir:

![Yerel Pad](media/data-visualizations-image9.png)

Aşağıdaki liste, Mac için Visual Studio'da hata ayıklama yaparken kullanılabilen yeni görselleştirmelerin çoğuna bakmaktadır.

## <a name="point"></a>Nokta
iOS ve Mac'teki Bir Nokta/PointF veya CGPoint, hata ayıklama defterindeki X ve Y değerlerini gösteren bir tuple olarak işlenir:

![Nokta Görselleştirme](media/data-visualizations-image10.png)

## <a name="size"></a>Boyut
iOS ve Mac'teki Boyut/SizeF veya CGSize dikdörtgen olarak işlenir. Bir boyut 250 px'i geçene kadar ölçeklenir ve bu noktada dikdörtgeni en büyük boyutla 250 px olarak ölçeklendirir:

[Boyut Görselleştirme](media/data-visualizations-image11.png)

## <a name="rectangle"></a>Dikdörtgen
iOS ve Mac'te bir Dikdörtgen/Dikdörtgen F veya CGRect boyutları ve kökeni görüntüler. Boyut'a benzer şekilde, bir boyut 250 px'i geçene kadar ölçekle çizilir:

![Dikdörtgen Görselleştirme](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Koordinat
Koordinatlar bir harita üzerinde çizilir ve konum merkeze sabitlenir:

[Görselleştirmeyi Koordine Edin](media/data-visualizations-image13.png)

## <a name="color"></a>Renk
Bu, renk önizlemesini, RGBA bileşenlerini, Ton Doygunluk-Hafiflik değerlerini ve rengin büyü değerini gösteren UIColor, CGColor ve Renk özelliklerini görüntüler:

![Renk Görselleştirme](media/data-visualizations-image14.png)

## <a name="images"></a>Görüntüler

Ortam, maksimum 250 px boyutuna kadar ölçeklendirilecek ve görüntü 250 px'i aştığında sığacak şekilde ölçeklendirilir:

![Görüntü Görselleştirme](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>Bezier Eğrileri

Görselleştirici bir `NSBezierPath`görüntüleyecek:

![Bezier Eğrisi Görselleştirme](media/data-visualizations-image16.png)

## <a name="string"></a>Dize

100'den az karakterden oluşan bir dize önizleme olmadan tam olarak görüntülenir. Daha uzun dizeleri önizlemede tam olarak görüntülenir. Dizeleri düzenlenebilir ve görselleştiricibir düzenleme düğmesi ile birlikte, dize değerinin önizlemede veya String Value Editor'da aşağıda gösterildiği şekilde düzenlenmesine izin verir:

![Dize Görselleştirme](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Küçük Dizeleri:
![Küçük Dize Görselleştirme](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Orta uzunlukta Dizeleri:
![Orta Dize Görselleştirme](media/data-visualizations-image19.png)

### <a name="editor"></a>Düzenleyicisi:

![Editör Görselleştirme](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>ıenumerable

Tüm değerleri sayısalolarak gösterir; değerleri **Göster** düğmesine tıklayarak her birinin değerleri görüntülenebilir. İzlenebilir seçenek, bu kendi hata ayıklayıcı görselleştiriciler `List<>` `Dictionary<,>` olduğu gibi , , `Array` `ArrayList`, gibi nesneler için değerleri görüntülemez.

![İzlenebilir Görselleştirme](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Diğer Görselleştiriciler

Kendi sıralı görselleştiricileri olan diğer bazı türler aşağıda listelenmiştir:

![Diğer Görselleştirme](media/data-visualizations-image23.png)

* **Temel Türler**
  * Bu, ilkel türün ham değerini gösterir.
* **Sabit Listesi**
  * Bu, enum Türü niteleyicisi olmadan alan değerini görüntüler.
* **Tuple**
  * Biçimde görüntülenir (,)
* **Null**
  * "Null" değerini gösterir.
* **URL**
  * Bu, tıklanabilir bir köprü görüntüler.
* **ıntptr**
  * Bu IntPtr bir hexadecimal temsilgörüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik ve Yerel pencerelerdeki değişkenleri inceleyin (Windows'ta Visual Studio)](/visualstudio/debugger/autos-and-locals-windows)
- [Dizeleri görselleştiricide görüntüleyin (Windows'ta Visual Studio)](/visualstudio/debugger/string-visualizer-dialog-box)