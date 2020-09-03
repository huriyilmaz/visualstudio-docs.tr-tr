---
title: Mac için Visual Studio ile hata ayıklama
description: Hata ayıklama, programlama için ortak ve gerekli bir parçasıdır. Yetişkinlere yönelik bir IDE olarak, Mac için Visual Studio hata ayıklamayı kolay hale getirmek için bir bütün özellik paketini içerir. Güvenli hata ayıklamadan veri görselleştirmesine kadar, bu makale Mac için Visual Studio ' de hata ayıklamanın tam potansiyelini nasıl kullanacağınızı açıklayacak.
author: therealjohn
ms.author: johmil
ms.date: 5/13/2020
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.topic: overview
ms.openlocfilehash: 09a761a8269fa40c3fab49a34b3e43a7f0ec63cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85939073"
---
# <a name="debugging-with-visual-studio-for-mac"></a>Mac için Visual Studio ile hata ayıklama

Mac için Visual Studio, .Net Core, .NET Framework, Unity ve Xamarin uygulamaları desteğiyle ilgili hata ayıklayıcılarına sahiptir.

Mac için Visual Studio, mono çalışma zamanına uygulanan [*mono yazılım hata ayıklayıcısını*](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/)kullanır ve bu, tüm platformlarda yönetilen kodun hatalarını ayıklamasına Mac için Visual Studio olanak tanır.

## <a name="the-debugger"></a>Hata ayıklayıcı

Mac için Visual Studio, tüm Xamarin uygulamalarındaki yönetilen (C# veya F #) kodunda hata ayıklamak için mono Soft Debugger 'ı kullanır. Mono geçici hata ayıklayıcı, mono çalışma zamanı içinde yerleşik bir ortak hata ayıklayıcı olduğundan, normal hata ayıklayıcılarından farklıdır; oluşturulan kod ve mono çalışma zamanı, bir hata ayıklama deneyimi sağlamak için IDE ile birlikte çalışır. Mono çalışma zamanı, [mono belgelerinde](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/)hakkında daha fazla bilgi edinmek için bir kablo protokolü aracılığıyla hata ayıklama işlevini kullanıma sunar.

[Lldb]( http://lldb.llvm.org/index.html) veya [gdb]( https://www.gnu.org/software/gdb/)gibi sabit hata ayıklayıcılar, hata ayıklaması yapılan programdan bilgi veya ortak işlem olmadan bir programı denetler, ancak yerel iOS veya Android kodunda hata ayıklamanıza gerek kalmadan Xamarin uygulamalarında hata ayıklarken yararlı olabilir.

.NET Core ve ASP.NET Core uygulamaları için Mac için Visual Studio .NET Core hata ayıklayıcısını kullanır. Bu hata ayıklayıcı Ayrıca ortak bir hata ayıklayıcı ve .NET çalışma zamanı ile birlikte çalışır.

## <a name="using-the-debugger"></a>Hata ayıklayıcıyı kullanma

Herhangi bir uygulamada hata ayıklamaya başlamak için yapılandırmanın  **hata ayıklama**olarak ayarlandığından emin olun. Hata ayıklama yapılandırması, kesme noktaları, veri görselleştiricileri kullanma ve çağrı yığınını görüntüleme gibi hata ayıklamayı desteklemek için faydalı bir araç kümesi sağlar:

![Hata ayıklama yapılandırması](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Kesme noktası ayarlama

IDE 'niz içinde bir kesme noktası ayarlamak için, düzenleyicinin kenar boşluğu alanına tıklayarak kesmek istediğiniz kodun satır numarasını seçin:

![Kenar boşluğunda kesme noktası ayarlanıyor](media/debugging-image0.png)

**Kesme noktaları paneline**giderek kodunuzda ayarlanmış olan tüm kesme noktalarını görüntüleyebilirsiniz:

![Kesme noktaları listesi](media/debugging-image0a.png)

## <a name="start-debugging"></a>Hata ayıklamayı Başlat

Hata ayıklamayı başlatmak için hedef tarayıcı, cihaz veya simülatör/öykünücü ' ı seçin:

![Hata ayıklama yapılandırması ](media/debugging-image_0.png)
 ![ hedef cihaz Seç](media/debugging-image1.png)

Ardından  **oynat** düğmesine veya  **cmd + Return**tuşuna basarak uygulamanızı dağıtın. Bir kesme noktasına ulaştığınızda, kod sarı olarak vurgulanır:

![Kesme noktasının isabet olduğunu Vurgula](media/debugging-image2.png)

Kodunuzda neler olduğunu öğrenmek için, bu noktada, nesnelerin değerlerini incelemek üzere kullanılan hata ayıklama araçları ile ilgili daha fazla bilgi edinebilirsiniz:

![Görselleştirmeler hatalarını ayıklama](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Koşullu kesme noktaları

Ayrıca, bir kesme noktası olması gereken koşulları görüntüleyen kuralları ayarlayabilirsiniz, bu durum, *koşullu kesme noktası*ekleme olarak bilinir. Koşullu kesme noktası ayarlamak için  **kesme noktası Özellikler penceresi**erişin ve bu iki şekilde yapılabilir:

* Yeni bir koşullu kesme noktası eklemek için, bir kesme noktası ayarlamak istediğiniz kodun sol tarafındaki Düzenleyici kenar boşluğuna sağ tıklayın ve yeni kesme noktası ' nı seçin:

 ![Kesme noktası bağlam menüsü](media/debugging-image4.png)

* Varolan bir kesme noktasına koşul eklemek için, kesme noktasına sağ tıklayın ve  **kesme noktası özellikleri**' ni seçin ya da  **kesme noktaları panelinde**aşağıda gösterilen kesme noktasını Düzenle düğmesini seçin:

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

## <a name="change-which-statement-is-executed-next"></a>Sonraki hangi deyimin yürütüleceğini Değiştir

Hata ayıklayıcı duraklatıldığında, kenar boşluğundaki bir ok yürütülecek sonraki kod satırını gösterir. Yürütülecek deyimi değiştirmek için başka bir kod satırına oku tıklayıp sürükleyebilirsiniz. Ayrıca, bir kod satırına sağ tıklayıp bağlam menüsünden **sonraki Ifadeyi ayarla** ' yı seçerek aynı şeyi elde edebilirsiniz.

![Sonraki ifadeyi ayarlamak için sürükle ve bırak oku](media/debugger-drag-setnextstatement.gif)

> [!CAUTION]
> Geçerli yürütme satırını değiştirmek, bir uygulamada beklenmeyen davranışlara neden olabilir. Ayrıca, sonraki deyimin yürütülmesi için değiştirilmesinin mümkün olmadığı bazı koşullar da vardır. Örneğin, oku bir yöntemden başka bir yönteme sürüklemek işe alınacaktır. Bu desteklenmeyen durumlarda Mac için Visual Studio, geçerli yürütme satırını değiştiremediğini bilmenizi sağlayan bir iletişim kutusu görüntüler. 

## <a name="debugging-monos-class-libraries"></a>Mono sınıf kitaplıklarında hata ayıklama

Xamarin ürünleri, mono 'ın sınıf kitaplıkları için kaynak kodla birlikte görüntülenir ve bu işlemi hata ayıklayıcıdan tek adımda kullanarak nesnelerin bir alt bölümünde nasıl çalıştığını inceleyebilirsiniz.

Bu özellik hata ayıklama sırasında daha fazla bellek tükettiği için varsayılan olarak kapalıdır.

Bu özelliği etkinleştirmek için,  **Mac için Visual Studio > tercihleri > hata ayıklayıcıya** gidin ve aşağıda gösterildiği gibi "**dış koda adımla**" seçeneğinin **seçildiğinden**emin olun:

![Dış koda adımla seçeneği](media/debugging-image8.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da hata ayıklama (Windows üzerinde)](/visualstudio/debugger/)
