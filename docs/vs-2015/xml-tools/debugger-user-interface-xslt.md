---
title: Hata ayıklayıcı kullanıcı arabirimi (XSLT) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1d35ec92a76c9ecbf933256229b64ce06a03a4fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670984"
---
# <a name="debugger-user-interface-xslt"></a>Hata Ayıklayıcı Kullanıcı Arabirimi (XSLT)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda hata ayıklayıcı pencereleri ve iletişim kutuları açıklanmaktadır. Yalnızca XSLT 'ye özgü hata ayıklama davranışına sahip kullanıcı arabirimi parçalarını ele alır.

 Daha fazla bilgi için bkz. [Kullanıcı arabirimi başvurusuna hata ayıklama](../debugger/debugging-user-interface-reference.md).

## <a name="locals-window"></a>Yereller penceresi
 Yereller penceresi, stil sayfasında tanımlanmış değişkenler hakkında bilgi görüntüler. Yereller penceresi üç sütun bilgi içerir:

 **Ad** Bu sütun, geçerli kapsamdaki tüm yerel değişkenlerin adlarını içerir. Düğüm kümelerinin alt klasörlerini görmek için ayrıntıya gidebileceğiniz bir ağaç denetimi vardır.

 **Değer** Bu sütunda her bir değişken tarafından içerilen değer gösterilir. Öznitelik, işleme yönergesi, açıklama, metin ve CData düğümleri, düğümün metin değerini görüntüler. Ad alanı düğümleri ad alanı URI 'sini görüntüler.

 **Tür** Bu sütun, **ad** sütununda listelenen her değişkenin veri türünü tanımlar.

 Yereller penceresi ayrıca XSLT dönüşümünün bağlamını izleyen önceden tanımlanmış bağlam değişkenlerini de görüntüler. Aşağıdaki tabloda XSLT hata ayıklayıcısı tarafından kullanılan önceden tanımlanmış bağlam değişkenleri açıklanmaktadır.

|Ad|Açıklama|
|----------|-----------------|
|`last()`|Bağlam boyutu.|
|`position()`|Bağlam düğümünün bağlam boyutuna göre konumu veya dizin numarası.|
|`self::node()`|Bağlam düğümünün değeri.|

 Daha fazla bilgi için bkz. [nasıl yapılır: hata ayıklayıcı bağlamını değiştirme](https://msdn.microsoft.com/library/8a69ea63-2ef0-4b4f-9521-cf8ad2e3ec5e).

## <a name="output-window"></a>Çıktı Penceresi
 Çıkış penceresinde hata iletileri veya hata ayıklama sırasında oluşan güvenlik özel durumları gösterilir.

 XSLT hata ayıklayıcısı, hata ayıklayıcı çıkışını göstermek için ayrı bir pencere kullanır. Bu, bir **XSL çıkışını göster** komutundan çıktıyı görüntülemek için kullanılan pencereyle aynı penceresidir.

## <a name="task-list"></a>Görev Listesi
 Görev Listesi stil sayfasındaki tüm derleme hatalarını listeler. Hataya çift tıklamak imleci hata ile satıra götürür.

 Görev Listesi XSLT dosyasındaki betik bloklarından oluşan tüm hataları içerir.

> [!NOTE]
> XSLT hata ayıklayıcısında hiçbir uyarı yoktur, bu nedenle Görev Listesi hiçbir şekilde görünmez.

## <a name="breakpoints-window"></a>Kesme noktaları penceresi
 Kesme noktaları penceresi geçerli projede ayarlanan tüm kesme noktalarını gösterir. Pencere görünümünde bir kesme noktası eklenirse pencere, yeni kesme noktasını gösterecek şekilde otomatik olarak güncelleştirilir.

 Kesme noktaları penceresi diğer Visual Studio hata ayıklayıcıları ile aynı şekilde davranır.

## <a name="command-windowimmediate-window"></a>Komut penceresi/acil pencere
 XSLT hata ayıklayıcısı 'nın bu sürümünde uygulanmadı.

## <a name="watch-window"></a>Gözcü penceresi
 İzleme penceresi değişkenleri değerlendirmek için kullanılır. Değişkenlerin değerlerini de değiştirebilirsiniz.

 İzleme penceresi görüntülenen değişkenler geçerli bağlam içindir (çağrı yığınında en üstteki öğe). Bağlamı değiştirirseniz, Gözcü penceresi güncellenir ve bu bağlam için ayarlanan değişkenleri görüntüler.

## <a name="call-stack-window"></a>Çağrı yığını penceresi
 Çağrı yığını penceresi, çağrı yığınında işlevlerin adlarını, parametre türlerini ve parametre değerlerini görüntülemek için kullanılır. Çağrı yığını bilgileri yalnızca, hata Ayıklanan program bir kesme durumunda olduğunda gösterilir.

 Çağrı yığını, XSLT yürütmesinin devam ettiği çeşitli bağlamlarını temsil eder. Örneğin, "a" şablonundan "b" şablonuna yapılan bir çağrı varsa, "a" şablonu ve "b" şablonu, listenin en üstündeki geçerli bağlamla çağrı yığını penceresinde görünür. Kullanıcı şu anda yürütülmekte olan sorguyu görebilir.

 Şablonlar XSLT dosyasında bir ada sahip değilse, XSLT işlemcisi tarafından oluşturulan adlar kullanılır.

 Listenin en üstünde yer aldığı bir öğeyi tıklatmak, XSLT yürütme dalının standart yeşil vurgulama ve yeşil oklar kullanılarak gerçekleştiği görüntüleyiciye işaret gösterir.

## <a name="quickwatch-dialog-box"></a>QuickWatch Iletişim kutusu
 **Hızlı izleme** iletişim kutusu, XPath 1,0 ifadelerini değerlendirmek için kullanılır. Bağlam düğümü ( `self::node()` Yereller penceresinden düğüm) XPath ifadesinin yürütülmesi için bağlam sağlar. XPath ifadesinin yürütülmesi sonucu izleme penceresi görüntülenir.

 Aşağıdaki listede, XPath ifadesi değerlendirmesinde bazı kısıtlamalar açıklanmaktadır.

- Yalnızca yerleşik XPath işlevlerine izin verilir.

- , Ve gibi yerleşik XSLT işlevlerine `document()` `key()` izin verilmez.

- Kullanıcı tanımlı işlevlere izin verilmiyor.

  Daha fazla bilgi için bkz. [nasıl yapılır: bir XPath Ifadesini değerlendirme](../xml-tools/how-to-evaluate-an-xpath-expression.md).

## <a name="disassembly-window"></a>Ayrıştırma penceresi
 Ayrıştırılmış pencere, XSLT derleyicisi tarafından oluşturulan derleme kodunu gösterir. Bu pencere, diğer tüm Visual Studio Derlemele pencereleri ile aynı şekilde kullanılabilir.

 Daha fazla bilgi için [nasıl yapılır: ayrıştırma penceresini kullanma](../debugger/how-to-use-the-disassembly-window.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [XSLT](../xml-tools/debugging-xslt.md) [hata ayıklayıcısı temel](../debugger/debugger-basics.md) [değişken pencerelerinin](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e) hatalarını ayıklama
