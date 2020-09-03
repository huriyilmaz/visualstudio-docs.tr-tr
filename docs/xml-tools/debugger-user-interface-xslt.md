---
title: XSLT hata ayıklayıcısı pencereleri
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb72acf2db63e54da8a1ee001d2abfaa30850fc3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592886"
---
# <a name="debugger-user-interface-xslt"></a>Hata ayıklayıcı kullanıcı arabirimi (XSLT)

Bu makalede hata ayıklayıcı pencereleri ve iletişim kutuları açıklanmaktadır. Yalnızca XSLT 'ye özgü hata ayıklama davranışına sahip kullanıcı arabirimi parçalarını ele alır.

Daha fazla bilgi için bkz. [Kullanıcı arabirimi başvurusuna hata ayıklama](../debugger/debugging-user-interface-reference.md).

## <a name="locals-window"></a>Yerel öğeler penceresi

Yereller penceresi, stil sayfasında tanımlanmış değişkenler hakkında bilgi görüntüler. Yereller penceresi üç sütun bilgi içerir:

**Ad**

Bu sütun, geçerli kapsamdaki tüm yerel değişkenlerin adlarını içerir. Düğüm kümelerinin alt klasörlerini görmek için ayrıntıya gidebileceğiniz bir ağaç denetimi vardır.

**Değer**

Bu sütunda her bir değişken tarafından içerilen değer gösterilir. Öznitelik, işleme yönergesi, açıklama, metin ve CData düğümleri, düğümün metin değerini görüntüler. Ad alanı düğümleri ad alanı URI 'sini görüntüler.

**Tür**

Bu sütun, **ad** sütununda listelenen her değişkenin veri türünü tanımlar.

Yereller penceresi ayrıca XSLT dönüşümünün bağlamını izleyen önceden tanımlanmış bağlam değişkenlerini de görüntüler. Aşağıdaki tabloda XSLT hata ayıklayıcısı tarafından kullanılan önceden tanımlanmış bağlam değişkenleri açıklanmaktadır.

|Ad|Açıklama|
|-|-----------------|
|`last()`|Bağlam boyutu.|
|`position()`|Bağlam düğümünün bağlam boyutuna göre konumu veya dizin numarası.|
|`self::node()`|Bağlam düğümünün değeri.|

## <a name="output-window"></a>Çıktı penceresi

Çıkış penceresinde hata iletileri veya hata ayıklama sırasında oluşan güvenlik özel durumları gösterilir. Ayrıca hata ayıklayıcı çıktısını gösterir.

## <a name="task-list"></a>Görev Listesi

**Görev listesi** stil sayfasındaki tüm derleme hatalarını listeler. Hataya çift tıklamak imleci hata ile satıra götürür.

**Görev LISTESI** XSLT dosyasındaki betik bloklarından oluşan tüm hataları içerir.

> [!NOTE]
> XSLT hata ayıklayıcısında hiçbir uyarı yoktur, bu nedenle **görev listesi**hiçbir şekilde görünmez.

## <a name="breakpoints-window"></a>Kesme Noktaları penceresi

Kesme noktaları penceresi geçerli projede ayarlanan tüm kesme noktalarını gösterir. Pencere görünümünde bir kesme noktası eklenirse pencere, yeni kesme noktasını gösterecek şekilde otomatik olarak güncelleştirilir.

Kesme noktaları penceresi diğer Visual Studio hata ayıklayıcıları ile aynı şekilde davranır.

## <a name="watch-window"></a>Gözcü penceresi

İzleme penceresi değişkenleri değerlendirmek için kullanılır. Değişkenlerin değerlerini de değiştirebilirsiniz.

İzleme penceresi görüntülenen değişkenler geçerli bağlam içindir (çağrı yığınında en üstteki öğe). Bağlamı değiştirirseniz, Gözcü penceresi güncellenir ve bu bağlam için ayarlanan değişkenleri görüntüler.

## <a name="call-stack-window"></a>Çağrı Yığını penceresi

Çağrı **yığını penceresi,** çağrı yığınında işlevlerin adlarını, parametre türlerini ve parametre değerlerini görüntülemek için kullanılır. Çağrı yığını bilgileri yalnızca, hata Ayıklanan program bir kesme durumunda olduğunda gösterilir.

Çağrı yığını, XSLT yürütmesinin devam ettiği çeşitli bağlamlarını temsil eder. Örneğin, "a" şablonundan "b" şablonuna bir çağrı varsa, "a" şablonu ve "b" şablonu, **çağrı yığını** penceresinde listenin en üstünde bulunan geçerli bağlamla görüntülenir. Kullanıcı şu anda yürütülmekte olan sorguyu görebilir.

Şablonlar XSLT dosyasında bir ada sahip değilse, XSLT işlemcisi tarafından oluşturulan adlar kullanılır.

Listenin en üstünde yer aldığı bir öğeyi tıklatmak, XSLT yürütme dalının standart yeşil vurgulama ve yeşil oklar kullanılarak gerçekleştiği görüntüleyiciye işaret gösterir.

## <a name="quickwatch-dialog-box"></a>QuickWatch iletişim kutusu

**Hızlı izleme** iletişim kutusu, XPath 1,0 ifadelerini değerlendirmek için kullanılır. Bağlam düğümü ( `self::node()` Yereller penceresinden düğüm) XPath ifadesinin yürütülmesi için bağlam sağlar. XPath ifadesinin yürütülmesi sonucu izleme penceresi görüntülenir.

Aşağıdaki listede XPath ifade değerlendirmesi kısıtlamaları açıklanmaktadır:

- Yalnızca yerleşik XPath işlevlerine izin verilir.

- Ve gibi yerleşik XSLT işlevlerine `document()` `key()` izin verilmez.

- Kullanıcı tanımlı işlevlere izin verilmiyor.

Daha fazla bilgi için bkz. [nasıl yapılır: bir XPath Ifadesini değerlendirme](../xml-tools/how-to-evaluate-an-xpath-expression.md).

## <a name="disassembly-window"></a>Ayrıştırma penceresi

Ayrıştırılmış pencere, XSLT derleyicisi tarafından oluşturulan derleme kodunu gösterir. Bu pencere, diğer tüm Visual Studio Derlemele pencereleri ile aynı şekilde kullanılabilir.

Daha fazla bilgi için [nasıl yapılır: ayrıştırma penceresini kullanma](../debugger/how-to-use-the-disassembly-window.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Visual Studio 'da oto ve Yereller pencerelerinde değişkenleri İnceleme](../debugger/autos-and-locals-windows.md)
