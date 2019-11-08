---
title: Xamarin ile hata ayıklama
description: Hata ayıklama, programlama için ortak ve gerekli bir parçasıdır. Yetişkinlere yönelik bir IDE olarak, Mac için Visual Studio hata ayıklamayı kolay hale getirmek için bir bütün özellik paketini içerir. Güvenli hata ayıklamadan veri görselleştirmesine kadar, bu makale Mac için Visual Studio ' de hata ayıklamanın tam potansiyelini nasıl kullanacağınızı açıklayacak.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.openlocfilehash: 96474925c5411d76395cb60ab1ad4851c1cbfa19
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73715944"
---
# <a name="debugging-with-xamarin"></a>Xamarin ile hata ayıklama

Mac için Visual Studio, Xamarin. iOS, Xamarin. Mac ve Xamarin. Android uygulamaları için hata ayıklama desteğine izin veren yerel bir hata ayıklayıcıya sahiptir.

Mac için Visual Studio, mono çalışma zamanına uygulanan [*mono yazılım hata ayıklayıcısını*](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/)kullanır ve bu, tüm platformlarda yönetilen kodun hatalarını ayıklamasına Mac için Visual Studio olanak tanır.

## <a name="the-debugger"></a>Hata ayıklayıcı

Mac için Visual Studio, tüm Xamarin uygulamalarındaki yönetilen (C# veya F#) kodda hata ayıklamak için mono Soft Debugger 'ı kullanır. Mono geçici hata ayıklayıcı, mono çalışma zamanı içinde yerleşik bir ortak çalışma hata ayıklayıcısıdır ve normal hata ayıklayıcılarından farklıdır; oluşturulan kod ve mono çalışma zamanı bir hata ayıklama deneyimi sağlamak için IDE ile birlikte çalışır. Mono çalışma zamanı, [mono belgelerinde](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/)hakkında daha fazla bilgi edinmek için bir kablo protokolü aracılığıyla hata ayıklama işlevini kullanıma sunar.

[Lldb](https://lldb.llvm.org/index.html) veya [gdb](https://www.gnu.org/software/gdb/)gibi sabit hata ayıklayıcılar, hata ayıklaması yapılan programdan bilgi veya ortak işlem olmadan bir programı denetler, ancak yerel iOS veya Android kodunda hata ayıklamanıza gerek kalmadan Xamarin uygulamalarında hata ayıklarken yararlı olabilir.

## <a name="using-the-debugger"></a>Hata ayıklayıcıyı kullanma

Herhangi bir uygulamada hata ayıklamaya başlamak için yapılandırmanın **hata ayıklama**olarak ayarlandığından emin olun. Hata ayıklama yapılandırması, kesme noktaları, veri görselleştiricileri kullanma ve çağrı yığınını görüntüleme gibi hata ayıklamayı desteklemek için faydalı bir araç kümesi sağlar:

![Hata ayıklama yapılandırması](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Kesme noktası ayarlama

IDE 'niz içinde bir kesme noktası ayarlamak için, düzenleyicinin kenar boşluğu alanına tıklayarak kesmek istediğiniz kodun satır numarasını seçin:

![Kenar boşluğunda kesme noktası ayarlanıyor](media/debugging-image0.png)

**Kesme noktaları paneline**giderek kodunuzda ayarlanmış olan tüm kesme noktalarını görüntüleyebilirsiniz:

![Kesme noktaları listesi](media/debugging-image0a.png)

## <a name="start-debugging"></a>Hata ayıklamayı Başlat

Hata ayıklamayı başlatmak için IDE 'nizin hedef cihazı veya benzer/öykünücü seçin:

![Hedef cihaz seçin](media/debugging-image1.png)

Ardından **oynat** düğmesine veya **cmd + Return**tuşuna basarak uygulamanızı dağıtın. Bir kesme noktasına ulaştığınızda, kod sarı olarak vurgulanır:

![Kesme noktasının isabet olduğunu Vurgula](media/debugging-image2.png)

Kodunuzda neler olduğunu öğrenmek için, bu noktada, nesnelerin değerlerini incelemek üzere kullanılan hata ayıklama araçları ile ilgili daha fazla bilgi edinebilirsiniz:

![Görselleştirmeler hatalarını ayıklama](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Koşullu kesme noktaları

Ayrıca, bir kesme noktası olması gereken koşulları görüntüleyen kuralları ayarlayabilirsiniz, bu durum, *koşullu kesme noktası*ekleme olarak bilinir. Koşullu kesme noktası ayarlamak için **kesme noktası Özellikler penceresi**erişin ve bu iki şekilde yapılabilir:

* Yeni bir koşullu kesme noktası eklemek için, bir kesme noktası ayarlamak istediğiniz kodun sol tarafındaki Düzenleyici kenar boşluğuna sağ tıklayın ve yeni kesme noktası ' nı seçin:

 ![Kesme noktası bağlam menüsü](media/debugging-image4.png)

* Varolan bir kesme noktasına koşul eklemek için, kesme noktasına sağ tıklayın ve **kesme noktası özellikleri**' ni seçin ya da **kesme noktaları panelinde**aşağıda gösterilen kesme noktasını Düzenle düğmesini seçin:

 ![Kesme noktaları panelinde mevcut kesme noktasını Düzenle](media/debugging-image5.png)

Ardından, kesme noktasının gerçekleşmesini istediğiniz koşulu girebilirsiniz:

 ![Kesme noktası koşullarını Düzenle](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Kod üzerinden adımla

Bir kesme noktasına ulaşıldığında, hata ayıklama araçları programın yürütülmesi üzerinde denetim almanızı sağlar. Mac için Visual Studio dört düğme görüntüleyecektir ve kodu çalıştırıp adım adım ilerlemenize olanak tanır. Mac için Visual Studio, aşağıdaki gibi görünür:

 ![Kod içinde adım adım geçiş yapmak için düğmeler](media/debugging-image7.png)

Dört düğme aşağıda verilmiştir:

* **Çal** -bu, sonraki kesme noktasına kadar kodu yürütmeye başlayacaktır.
* **Üzerinde adımla** -bu, sonraki kod satırını yürütür. Bir sonraki satır bir işlev çağrısý ise, üzerine adımla işlevi yürütülür ve işlevden *sonraki kod satırında duracaktır* .
* **Içine adımla** , sonraki kod satırını da yürütür. Bir sonraki satır bir işlev çağrıdır, işlevin ilk satırında, işlevin satır içi hata ayıklamasına devam edebilmenizi sağlayan adımla durur. Sonraki satır bir işlev değilse, adımla aynı şekilde davranır.
* **Dışarı adımla** -bu, geçerli işlevin çağrıldığı satıra geri döner.

## <a name="debugging-monos-class-libraries"></a>Mono sınıf kitaplıklarında hata ayıklama

Xamarin ürünleri, mono 'ın sınıf kitaplıkları için kaynak kodla birlikte görüntülenir ve bu işlemi hata ayıklayıcıdan tek adımda kullanarak nesnelerin bir alt bölümünde nasıl çalıştığını inceleyebilirsiniz.

Bu özellik hata ayıklama sırasında daha fazla bellek tükettiği için varsayılan olarak kapalıdır.

Bu özelliği etkinleştirmek için, **Mac için Visual Studio > tercihleri > hata ayıklayıcıya** gidin ve "**sadece proje kodunu Ayıkla;" çerçeve koduna adımla.** " seçeneğinin aşağıda gösterildiği gibi **seçilmemiş**olması gerekir:

![Çerçeve kodu seçeneğine adımla](media/debugging-image8.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da hata ayıklama (Windows üzerinde)](/visualstudio/debugger/)
