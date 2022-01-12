---
title: Mac için Visual Studio ile hata ayıklama
description: Hata ayıklama, programlamanın ortak ve gerekli bir bölümüdür. Olgun bir IDE olarak, Mac için Visual Studio ayıklamayı kolaylaştıran bir özellik paketi içerir. Güvenli hata ayıklamadan veri görselleştirmeye kadar bu makalede, hata ayıklamanın tüm potansiyelinin nasıl Mac için Visual Studio.
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 5/13/2020
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.topic: conceptual
ms.openlocfilehash: 62274cb42a26ea793dc2c61e68d8f758517e8ae0
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803719"
---
# <a name="debugging-with-visual-studio-for-mac"></a>Mac için Visual Studio ile hata ayıklama

Mac için Visual Studio.NET Core, .NET Framework, Unity ve Xamarin uygulamaları desteğine sahip hata ayıklayıcıları vardır.

Mac için Visual Studio tüm platformlarda yönetilen kodun hata ayıklamasına olanak Mono çalışma zamanı Mono Mac için Visual Studio Hata Ayıklayıcı'sını kullanır. [](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/)

## <a name="the-debugger"></a>Hata Ayıklayıcı

Mac için Visual Studio Xamarin uygulamalarında yönetilen (C# veya F#) kodunda hata ayıklamak için Mono Soft Debugger kullanır. Mono Soft hata ayıklayıcısı, normal hata ayıklayıcılarından farklıdır ve bu hata ayıklayıcı, hata ayıklayıcıda yerleşik olarak Mono çalışma zamanı; oluşturulan kod ve hata Mono çalışma zamanı bir hata ayıklama deneyimi sağlamak için IDE ile işbirliği yapar. Bu Mono çalışma zamanı, mono belgelerinde hakkında daha fazla bilgi edinen bir kablo protokolü aracılığıyla hata [ayıklama işlevini ortaya çıkarır.](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/)

[LLDB]( http://lldb.llvm.org/index.html) veya [GDB]( https://www.gnu.org/software/gdb/)gibi sabit hata ayıklayıcılar, bir programı, hata ayıklama programından bilgi veya işbirliği yapmadan kontrol ediyor, ancak yerel iOS veya Android kodunda hata ayıklamanız gereken durumlarda Xamarin uygulamalarında hata ayıklarken yine de yararlı olabilir.

.NET Core ve ASP.NET Core uygulamaları için Mac için Visual Studio .NET Core hata ayıklayıcısını kullanır. Bu hata ayıklayıcı da işbirliğine sahip bir hata ayıklayıcısıdır ve .NET çalışma zamanıyla çalışır.

## <a name="using-the-debugger"></a>Hata ayıklayıcısını kullanma

Herhangi bir uygulamada hata ayıklamaya başlamak için yapılandırmanın Her zaman Hata Ayıkla olarak ayarlanmış **olduğundan emin olur.** Hata ayıklama yapılandırması, kesme noktaları, veri görselleştiricileri kullanma ve çağrı yığınını görüntüleme gibi hata ayıklamayı desteklemek için yararlı bir araç kümesi sağlar:

![Hata ayıklama yapılandırması](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Kesme noktası ayarlama

IDE'nize bir kesme noktası ayarlamak için düzenleyicinizin kenar boşluğu alanına, kesme noktası istediğiniz kodun satır numarasının yanındaki üzerine tıklayın:

![Kenar boşluğunda kesme noktası ayarlama](media/debugging-image0.png)

Kesme Noktaları Penceresi'ne gidip kodunda ayarlanmış olan tüm kesme **noktalarına bakabilirsiniz:**

![Kesme noktaları listesi](media/debugging-image0a.png)

## <a name="start-debugging"></a>Hata ayıklamayı başlatma

Hata ayıklamaya başlamak için hedef tarayıcıyı, cihazı veya simülatör/öykünücü'leri seçin:

![Hata ayıklama yapılandırması ](media/debugging-image_0.png)
 ![ Hedef cihazı seçme](media/debugging-image1.png)

Ardından Oynat düğmesine basarak veya **Cmd** + return **tuşlarına basarak uygulamanızı dağıtın.** Bir kesme noktasıyla karşılaşmak için kod sarı vurgulanır:

![Kesme noktası isabetini gösteren vurgu](media/debugging-image2.png)

Nesnelerin değerlerini incelemek için kullanılan araç gibi hata ayıklama araçları, kodunda neler olduğu hakkında daha fazla bilgi almak için bu noktada kullanılabilir:

![Görselleştirmelerde hata ayıklama](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Koşullu kesme noktaları

Ayrıca, bir kesme noktası gerçekleşmesi gereken koşulları belirten kurallar da belirterek koşullu kesme noktası ekleme *olarak bilinir.* Koşullu kesme noktası ayarlamak için Kesme noktası Özellikler penceresi erişin. Bu iki şekilde yapılabilir:

* Yeni bir koşullu kesme noktası eklemek için, üzerinde kesme noktası ayarlamak istediğiniz kodun satır numarasının sol tarafından düzenleyici kenar boşluğuna sağ tıklayın ve Yeni Kesme Noktası'yı seçin:

 ![Kesme noktası bağlam menüsü](media/debugging-image4.png)

* Mevcut bir kesme noktası için koşul eklemek için kesme noktası üzerine sağ tıklayın ve Kesme Noktası Özellikleri'ni seçin veya Kesme Noktaları Penceresi'nin altında gösterilen Kesme Noktası Düzenle düğmesini seçin:

 ![Kesme Noktaları Penceresinde mevcut Kesme Noktası'nın düzenlemesi](media/debugging-image5.png)

Daha sonra kesme noktası gerçekleşmesini istediğiniz koşulu girsiniz:

 ![Kesme noktası koşullarını düzenleme](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Kodda adım adım ilerler

Bir kesme noktası ulaşıldı, Hata Ayıklama araçları programın yürütmesi üzerinde denetim elde etmek için olanak sağlar. Mac için Visual Studio, kodu çalıştırmanıza ve adım adım çalışmanıza olanak sağlayan dört düğme görüntüler. Bu Mac için Visual Studio aşağıdaki gibi görünüyor:

 ![Kodda adım adım ilerler](media/debugging-image7.png)

Dört düğme şu şekildedir:

* **Yürüt** - Sonraki kesme noktası kadar kodu yürütmeye başlar.
* **Adım At** - Sonraki kod satırı yürütülür. Sonraki satır bir işlev çağrısı ise, Adım At işlevi yürütür ve işlevden sonraki kod *satırına* durur.
* **Adımla** - Bu, bir sonraki kod satırı da yürütülür. Sonraki satır bir işlev çağrısı ise, işlevin ilk satırda Step Into durur ve işlevin satır satır hata ayıklamasına devam eder. Sonraki satır bir işlev yoksa, AdımLa ile aynı şekilde davranır.
* **Dışarı Adımla** - Bu, geçerli işlevin çağrıldı olduğu satıra geri döner.

## <a name="change-which-statement-is-executed-next"></a>Daha sonra hangi deyimin yürütül olduğunu değiştirme

Hata ayıklayıcı duraklatıldığında, kenar boşluğundaki bir ok yürütülecek sonraki kod satırını gösterir. Yürütülecek deyimi değiştirmek için başka bir kod satırına oku tıklayıp sürükleyebilirsiniz. Bir kod satırına sağ tıklar ve bağlam menüsünden Sonraki Deyimi Ayarla'ya **tıklayarak** da aynı şeyi yapabilirsiniz.

![Sonraki deyimi ayarlamak için sürükleme ve bırakma oku](media/debugger-drag-setnextstatement.gif)

> [!CAUTION]
> Geçerli yürütme hattının değiştirilmesi, uygulamada beklenmeyen davranışlara neden olabilir. Bir sonraki deyimi yürütmek için değiştirilenin mümkün olmadığının bazı koşulları da vardır. Örneğin, oku bir yöntemden başka bir yönteme sürüklemek işemez. Bu desteklenmeyen durumlarda, Mac için Visual Studio geçerli yürütme hattını değiştirmenin mümkün olmadığını size haber vermenizi sağlar. 

## <a name="debugging-monos-class-libraries"></a>Mono'nun sınıf kitaplıklarında hata ayıklama

Xamarin ürünleri, Mono'nun sınıf kitaplıkları için kaynak koduyla birlikte gelir ve bu kodu kullanarak hata ayıklayıcısından tek adımla her şeyin nasıl çalıştığını incelersiniz.

Bu özellik hata ayıklama sırasında daha fazla bellek tükettiği için varsayılan olarak kapalıdır.

Bu özelliği etkinleştirmek için, Mac için Visual Studio > Tercihleri **> Hata** Ayıklayıcı'ya gidin ve **aşağıda** gösterildiği gibi " Dış koda adımla " seçeneğinin seçili olduğundan emin olun:

![Dış koda adımla seçeneği](media/debugging-image8.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama Visual Studio (Windows)](/visualstudio/debugger/)
