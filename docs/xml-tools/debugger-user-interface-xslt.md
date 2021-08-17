---
title: XSLT hata ayıklayıcısı pencereleri
description: YerelLer, Çıkış, Kesme Noktaları, Çağrı Yığını ve İzleme pencereleri dahil olmak üzere XSLT'ye özgü hata ayıklama davranışını kontrol altına alan XSLT hata ayıklayıcısı kullanıcı arabirimi parçaları hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: d5d5a0bd5e0c3885607db77343d20fc013467a93ce7e19be2387d84010556751
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351479"
---
# <a name="debugger-user-interface-xslt"></a>Hata ayıklayıcısı kullanıcı arabirimi (XSLT)

Bu makalede hata ayıklayıcı pencereleri ve iletişim kutuları açıklanmıştır. Yalnızca XSLT'ye özgü hata ayıklama davranışına sahip kullanıcı arabirimi parçalarını ele almaktadır.

Daha fazla bilgi için bkz. [Hata ayıklama kullanıcı arabirimi başvurusu.](../debugger/debugging-user-interface-reference.md)

## <a name="locals-window"></a>Yerel öğeler penceresi

Yereller penceresinde stil sayfalarında tanımlanan değişkenlerle ilgili bilgiler görüntülenir. Yereller penceresi üç bilgi sütunu içerir:

**Ad**

Bu sütun, geçerli kapsamdaki tüm yerel değişkenlerin adlarını içerir. Düğüm kümelerinin alt klasörlerini görmek için detaya inen bir ağaç denetimi vardır.

**Değer**

Bu sütunda her değişkenin içerdiği değer görüntülenir. Öznitelik, işleme yönergesi, açıklama, metin ve CData düğümleri düğümün metin değerini görüntüler. Ad alanı düğümleri ad alanı URI'lerini görüntüler.

**Tür**

Bu sütun, Ad sütununda listelenen her değişkenin veri **türünü** tanımlar.

YerelLer penceresi ayrıca XSLT dönüştürme bağlamını takip etmek için önceden tanımlanmış bağlam değişkenlerini görüntüler. Aşağıdaki tabloda XSLT hata ayıklayıcısı tarafından kullanılan önceden tanımlanmış bağlam değişkenleri açıkmektedir.

|Ad|Açıklama|
|-|-----------------|
|`last()`|Bağlam boyutu.|
|`position()`|Bağlam boyutuna göre bağlam düğümünün konumu veya dizin numarası.|
|`self::node()`|Bağlam düğümünün değeri.|

## <a name="output-window"></a>Çıktı penceresi

Çıkış penceresi hata ayıklama sırasında oluşan hata iletilerini veya güvenlik özel durumlarını gösterir. Ayrıca hata ayıklayıcısı çıktısını da gösterir.

## <a name="task-list"></a>Görev Listesi

Bu **Görev Listesi** stil sayfalarındaki tüm derleme hatalarını listeler. Hataya çift tıklarsanız imleci hatayla satıra alır.

Bu **Görev Listesi** XSLT dosyasındaki betik bloklarında oluşan hataları içerir.

> [!NOTE]
> XSLT hata ayıklayıcısı hiçbir uyarıya sahip değil, bu nedenle hiçbir zaman **Görev Listesi.**

## <a name="breakpoints-window"></a>Kesme Noktaları penceresi

Kesme Noktaları penceresinde geçerli projede ayarlanmış olan tüm kesme noktaları gösterilir. Pencere görünümdeyken bir kesme noktası eklenirse, pencere yeni kesme noktası gösterecek şekilde otomatik olarak güncelleştirilir.

Kesme Noktaları penceresi, diğer hata ayıklayıcıları gibi Visual Studio davranacak.

## <a name="watch-window"></a>Gözcü penceresi

Değişken izleme penceresi değerlendirmek için kullanılır. Değişkenlerin değerlerini de değiştirebilirsiniz.

Bu bağlamda görüntülenen izleme penceresi geçerli bağlama (çağrı yığınındaki en üst öğe) göredir. Bağlamı değiştirirsanız, izleme penceresi bu bağlam için ayarlanmış değişkenleri günceller ve görüntüler.

## <a name="call-stack-window"></a>Çağrı Yığını penceresi

Çağrı **Yığını penceresi** çağrı yığınında, parametre türlerinde ve parametre değerlerinde işlevlerin adlarını görüntülemek için kullanılır. Çağrı yığını bilgileri yalnızca hata ayıklaması yapılan program kesme durumuna geldiğinde gösterilir.

Çağrı yığını, XSLT yürütmenin üzerinden geçen çeşitli bağlamları temsil eder. Örneğin, "a" şablonundan "b" şablonuna yapılan bir çağrı varsa, "a" şablonu  ve "b" şablonu, listenin en üstünde geçerli bağlamın yer alan Çağrı Yığını penceresinde görünür. Kullanıcı şu anda yürütülen sorguyu görebilir.

Şablonların XSLT dosyasında bir adı yoksa, XSLT işlemcisi tarafından oluşturulan adlar kullanılır.

Listenin en üstünde yer alan öğe dışında bir öğeye tıklarsanız, görüntüleyiciye XSLT yürütme dalını standart yeşil vurgulama ve yeşil oklar kullanılarak nerede olduğunu gösterir.

## <a name="quickwatch-dialog-box"></a>QuickWatch iletişim kutusu

**QuickWatch iletişim** kutusu, XPath 1.0 ifadelerini değerlendirmek için kullanılır. Bağlam düğümü `self::node()` (Yereller penceresindeki düğüm), XPath ifadesinin yürütülmesi için bağlamı sağlar. XPath ifadesini yürütmenin sonucu, izleme penceresi.

Aşağıdaki listede XPath ifadesi değerlendirmesiyle ilgili kısıtlamalar açık almaktadır:

- Yalnızca yerleşik XPath işlevlerine izin verilir.

- ve gibi yerleşik XSLT `document()` `key()` işlevlerine izin verilmez.

- Kullanıcı tanımlı işlevlere izin verilmez.

Daha fazla bilgi için, [bkz. How to: Evaluate an XPath expression](../xml-tools/how-to-evaluate-an-xpath-expression.md).

## <a name="disassembly-window"></a>Ayrıştırma penceresi

Disassembly penceresi, XSLT derleyicisi tarafından oluşturulan derleme kodunu gösterir. Bu pencere, diğer tüm farklı Visual Studio kullanılabilir.

Daha fazla bilgi [için, Nasıl: Değerlendirme penceresini kullanma.](../debugger/how-to-use-the-disassembly-window.md)

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Yerel ayarlarda ve yerel ayarlar pencerelerinde değişkenleri Visual Studio](../debugger/autos-and-locals-windows.md)
