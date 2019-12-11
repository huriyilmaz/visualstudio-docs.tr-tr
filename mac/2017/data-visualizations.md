---
title: Hata ayıklama-veri görselleştirmeleri
description: Hata ayıklama, programlama için ortak ve gerekli bir parçasıdır. Mac için Visual Studio hata ayıklamayı kolay hale getirmek için bir bütün özellik paketini içerir. Bu makale, hata ayıklayıcıdaki nesneler incelenirken görüntülenebilecek farklı veri görselleştirmelerine bakar.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 3355b81406d2b510dc13604a026bcd014bf9dbcb
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984763"
---
# <a name="data-visualizations"></a>Veri görselleştirmeleri

Mac için Visual Studio hata ayıklayıcı için Kullanıcı arabirimi desteği içerir ve hata ayıklama sırasında değişken, alan veya özellik değerlerinin görselleştirmelerini sağlar. Bu veri Görselleştiriciler, verilerin genişletilmiş bir sürümünü gösterir ve geliştiricilerin bilinen yapıları inceleyerek, örneğin bir Color yapısının rengini gösterir.

Hata ayıklama **Yerel** panelindeki Görselleştiriciler, Kullanıcı satırın üzerine geldiğinde değerin sağında görüntülenen Önizleme simgesine tıklanarak görüntülenebilir:

![Yerel panel](media/data-visualizations-image9.png)

Aşağıdaki liste, Mac için Visual Studio hata ayıklamada bulunan yeni görselleştirmelerin çoğuna bakar.

## <a name="point"></a>Seçeneğinin
İOS ve Mac 'teki bir Point/PointF ya da CGPoint, hata ayıklama panelindeki X ve Y değerlerini gösteren bir kayıt düzeni olarak işlenir:

![Nokta görselleştirme](media/data-visualizations-image10.png)

## <a name="size"></a>Boyut
İOS ve Mac 'te bir boyut/boyut EF veya CGSize bir dikdörtgen olarak işlenir. Boyut 250 PX daha fazla büyüene kadar ölçeğe çizilir, bu noktada dikdörtgeni en büyük boyut olan 250 piksel olacak şekilde ölçeklendirecektir:

[Boyut görselleştirme](media/data-visualizations-image11.png)

## <a name="rectangle"></a>Dikdörtgen
İOS ve Mac 'te bir dikdörtgen/RectangleF veya CGRect, boyutları ve kaynağı görüntüler. Boyuta benzer şekilde, boyut 250 PX daha fazla büyüene kadar ölçeğe çizilir:

![Dikdörtgen görselleştirme](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Koordinat
Koordinatlar, merkeze sabitlenmiş konum ile bir haritada çizilir:

[Koordinat görselleştirme](media/data-visualizations-image13.png)

## <a name="color"></a>Renk
Bu, renk önizlemesi, RGBA bileşenleri, Ton doygunluğu ve açıklık değerlerinin yanı sıra rengin onaltılı değerini gösteren Uıicton, CGColor ve Color özelliklerini görüntüler:

![Renk görselleştirme](media/data-visualizations-image14.png)

## <a name="images"></a>Görüntüler

Medya, en yüksek boyut olan 250 PX ölçeklendirilecek şekilde işlenecek ve görüntü 250 PX ' i aştığında sığacak şekilde ölçeklendirilecektir:

![Görüntü görselleştirme](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>Bezier eğrileri

Görselleştirici bir `NSBezierPath`görüntüler:

![Bezier eğrisi görselleştirme](media/data-visualizations-image16.png)

## <a name="string"></a>Dize

Önizleme olmadan 100 karakterden kısa bir dize tam olarak görüntülenir. Daha uzun dizeler önizlemede tam olarak görüntülenir. Dizeler düzenlenebilir ve Görselleştirici bir düzenleme düğmesi ile birlikte, aşağıdaki gösterildiği gibi, önizleme veya dize değer düzenleyicisinde bir dize değerinin düzenlenmesine izin verir:

![Dize görselleştirme](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Küçük dizeler:
![Küçük dize görselleştirme](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Orta uzunlukta dizeler:
![Orta ölçekli dize görselleştirme](media/data-visualizations-image19.png)

### <a name="editor"></a>Düzenleyen:

![Düzenleyici görselleştirme](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>IEnumerable

IEnumerable tüm değerleri numaralandırır; her birinin değeri, değerleri **göster** düğmesine tıklanarak görüntülenebilir. IEnumerable seçeneği, `Array`, `ArrayList`, `List<>`, `Dictionary<,>` gibi nesnelerin değerlerini görüntüleyemez ve bunların kendi hata ayıklayıcı görselleştiricileri vardır.

![IEnumerable görselleştirme](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Diğer Görselleştiriciler

Kendi satır içi görselleştiricilerini de içeren bazı diğer türler aşağıda listelenmiştir:

![Diğer görselleştirme](media/data-visualizations-image23.png)

* **Temel Türler**
  * Bu, temel türün ham değerini gösterir.
* **Yardımının**
  * Bu, alan değerini enum türü niteleyicisi olmadan görüntüler.
* **Le**
  * Biçimde (,) gösterilir
* **Null**
  * "Null" değerini gösterir.
* **URL**
  * Bu, tıklatılabilir bir köprü görüntüler.
* **IntPtr**
  * Bu, IntPtr öğesinin onaltılı bir gösterimini görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Oto ve Yereller pencerelerinde değişkenleri İnceleme (Windows üzerinde Visual Studio)](/visualstudio/debugger/autos-and-locals-windows)
- [Bir Görselleştirici içindeki dizeleri görüntüleme (Windows üzerinde Visual Studio)](/visualstudio/debugger/string-visualizer-dialog-box)