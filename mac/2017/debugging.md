---
title: Xamarin ile hata ayıklama
description: Hata ayıklama, programlamanın ortak ve gerekli bir bölümüdür. Olgun bir IDE olarak, Mac için Visual Studio ayıklamayı kolaylaştıran bir özellik paketi içerir. Güvenli hata ayıklamadan veri görselleştirmeye kadar bu makalede, hata ayıklamanın tüm potansiyelinin nasıl Mac için Visual Studio.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.topic: overview
ms.openlocfilehash: 5db0cd7a9c1fc21f5b109a3c103a06a35d348755
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962143"
---
# <a name="debugging-with-xamarin"></a>Xamarin ile hata ayıklama

Mac için Visual Studio Xamarin.iOS, Xamarin.Mac ve Xamarin.Android uygulamaları için hata ayıklama desteğine izin veren bir yerel hata ayıklayıcısı vardır.

Mac için Visual Studio tüm platformlarda [](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/)yönetilen kodun hata ayıklamasına olanak Mono çalışma zamanı Mac için Visual Studio mono yazılım hata ayıklayıcısını kullanır.

## <a name="the-debugger"></a>Hata Ayıklayıcı

Mac için Visual Studio Xamarin uygulamalarında yönetilen (C# veya F#) kodunda hata ayıklamak için Mono Soft Debugger kullanır. Mono Soft hata ayıklayıcısı, normal hata ayıklayıcılarından farklıdır ve bu hata ayıklayıcı, hata ayıklayıcıda yerleşik olarak Mono çalışma zamanı; oluşturulan kod ve Mono çalışma zamanı hata ayıklama deneyimi sağlamak için IDE ile birlikte çalışır. Bu Mono çalışma zamanı, mono belgelerinde hakkında daha fazla bilgi edinerek bir kablo protokolü aracılığıyla hata [ayıklama işlevini ortaya çıkarır.](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/)

[LLDB](https://lldb.llvm.org/index.html) veya [GDB](https://www.gnu.org/software/gdb/)gibi sabit hata ayıklayıcılar, bir programı, hata ayıklama programından bilgi veya işbirliği yapmadan kontrol ediyor, ancak yerel iOS veya Android kodunda hata ayıklamanız gereken durumlarda Xamarin uygulamalarında hata ayıklarken yine de yararlı olabilir.

## <a name="using-the-debugger"></a>Hata ayıklayıcısını kullanma

Herhangi bir uygulamada hata ayıklamaya başlamak için yapılandırmanın Her zaman Hata Ayıkla olarak ayarlanmış **olduğundan emin olur.** Hata ayıklama yapılandırması, kesme noktaları, veri görselleştiricileri kullanma ve çağrı yığınını görüntüleme gibi hata ayıklamayı desteklemek için yararlı bir araç kümesi sağlar:

![Hata ayıklama yapılandırması](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Kesme noktası ayarlama

IDE'nize bir kesme noktası ayarlamak için düzenleyicinizin kenar boşluğu alanına, kesme noktası istediğiniz kodun satır numarasının yanındaki üzerine tıklayın:

![Kenar boşluğunda kesme noktası ayarlama](media/debugging-image0.png)

Kesme noktaları paneline gidip kodunda ayarlanmış olan tüm kesme **noktalarına bakabilirsiniz:**

![Kesme noktası listesi](media/debugging-image0a.png)

## <a name="start-debugging"></a>Hata ayıklamayı başlatma

Hata ayıklamayı başlatmak için IDE'nizin hedef cihazı veya benzer/öykünücüsünü seçin:

![Hedef cihazı seçme](media/debugging-image1.png)

Ardından Oynat düğmesine basarak veya **Cmd** + return **tuşlarına basarak uygulamanızı dağıtın.** Bir kesme noktasıyla karşılaşmak için kod sarı vurgulanır:

![Kesme noktası isabetini gösteren vurgu](media/debugging-image2.png)

Nesnelerin değerlerini incelemek için kullanılan araç gibi hata ayıklama araçları, kodunda neler olduğu hakkında daha fazla bilgi almak için bu noktada kullanılabilir:

![Görselleştirmelerde hata ayıklama](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Koşullu kesme noktaları

Ayrıca, bir kesme noktası gerçekleşmesi gereken koşulları belirten kurallar da ayarlayabiliyor, buna koşullu kesme noktası *ekleme de denmektedir.* Koşullu kesme noktası ayarlamak için Kesme noktası Özellikler penceresi erişin. Bu iki şekilde yapılabilir:

* Yeni bir koşullu kesme noktası eklemek için, üzerinde kesme noktası ayarlamak istediğiniz kodun satır numarasının sol tarafından düzenleyici kenar boşluğuna sağ tıklayın ve Yeni Kesme Noktası'yı seçin:

 ![Kesme noktası bağlam menüsü](media/debugging-image4.png)

* Mevcut bir kesme noktası için koşul eklemek için kesme noktası üzerine sağ tıklayın ve Kesme Noktası Özellikleri'ni seçin veya Kesme Noktaları Paneli'nin altında gösterilen Kesme Noktası Düzenle düğmesini seçin:

 ![Kesme Noktaları Paneli'nin mevcut Kesme Noktası'sini düzenleme](media/debugging-image5.png)

Daha sonra kesme noktası gerçekleşmesini istediğiniz koşulu girsiniz:

 ![Kesme noktası koşullarını düzenleme](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Kodda adım adım ilerler

Bir kesme noktası ulaşıldı, Hata Ayıklama araçları programın yürütmesi üzerinde denetim elde etmek için olanak sağlar. Mac için Visual Studio, kodu çalıştırmanıza ve adım adım çalışmanıza olanak sağlayan dört düğme görüntüler. Bu Mac için Visual Studio aşağıdaki gibi görünüyor:

 ![Kodda adım adım ilerler](media/debugging-image7.png)

Dört düğme şu şekildedir:

* **Yürüt** - Sonraki kesme noktası kadar kodu yürütmeye başlar.
* **Adım At** - Sonraki kod satırı yürütülür. Sonraki satır bir işlev çağrısı ise, Adım At işlevi yürütür ve işlevden sonraki kod *satırına* durur.
* **Adımla** - Bu, bir sonraki kod satırı da yürütülür. Sonraki satır bir işlev çağrısı ise, işlevin ilk satırda Adımla durarak işlevin satır satır hata ayıklamasına devam edin. Sonraki satır bir işlev yoksa, AdımLa ile aynı şekilde davranır.
* **Dışarı Adımla** - Bu, geçerli işlevin çağrıldı olduğu satıra geri döner.

## <a name="debugging-monos-class-libraries"></a>Mono'nun sınıf kitaplıklarında hata ayıklama

Xamarin ürünleri, Mono'nun sınıf kitaplıkları için kaynak koduyla birlikte gelir ve bu kodu kullanarak hata ayıklayıcısından tek adımla her şeyin nasıl çalıştığını incelersiniz.

Bu özellik hata ayıklama sırasında daha fazla bellek tükettiği için varsayılan olarak kapalıdır.

Bu özelliği etkinleştirmek için Hata **Ayıklayıcısı'Mac için Visual Studio > Tercihler'e >** ve " Yalnızca proje kodunda hata ayıkla;**çerçeve koduna adım atma.**" seçeneği, **aşağıda gösterildiği gibi** seçili değildir:

![Çerçeve kodu seçeneğine adım atma](media/debugging-image8.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama Visual Studio (Windows)](/visualstudio/debugger/)
