---
title: Mac için Visual Studio ile hata ayıklama
description: Hata ayıklama, programlamanın yaygın ve gerekli bir parçasıdır. Olgun bir IDE olarak, Mac için Visual Studio hata ayıklama kolaylaştırmak için özellikleri bir bütün paketi içerir. Güvenli hata ayıklama, veri görselleştirme, bu makalede Mac için Visual Studio hata ayıklama tam potansiyelini nasıl kullanılacağını açıklayacağız.
author: therealjohn
ms.author: johmil
ms.date: 12/13/2019
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.openlocfilehash: 8a12880c25e980d668351ef4c24ced1e479577d4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75397985"
---
# <a name="debugging-with-visual-studio-for-mac"></a>Mac için Visual Studio ile hata ayıklama

Mac için Visual Studio .Net Core, .NET Framework, Unity ve Xamarin uygulamaları için destek veren hata ayıklayıcılara sahiptir.

Mac için Visual Studio Mono [*Soft Debugger*](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/)kullanır , Mono çalışma süresi içine uygulanan, Mac için Visual Studio tüm platformlarda yönetilen kod hata ayıklamak için izin.

## <a name="the-debugger"></a>Hata Ayıklama

Mac için Visual Studio, tüm Xamarin uygulamalarında yönetilen (C# veya F#) kodunu hata ayıklamak için Mono Soft Debugger kullanır. Mono Soft hata ayıklayıcı, Mono çalışma süresi yerleşik bir kooperatif hata ayıklayıcı olması durumunda normal hata ayıklayıcılar farklıdır; oluşturulan kod ve Mono çalışma süresi hata ayıklama deneyimi sağlamak için IDE ile işbirliği yapar. Mono çalışma süresi, [Mono belgelerinde](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/)hakkında daha fazla bilgi edinebileceğiniz bir tel protokolü aracılığıyla hata ayıklama işlevini ortaya çıkarır.

[LLDB]( http://lldb.llvm.org/index.html) veya [GDB]( https://www.gnu.org/software/gdb/)gibi sert hata ayıklayıcılar, debugged programın bilgisi veya işbirliği olmadan bir programı kontrol, ancak yerel iOS veya Android kodu hata ayıklama gerektiğinde Xamarin uygulamaları hata ayıklama hala yararlı olabilir.

.NET Core ve ASP.NET Core uygulamaları için, Mac için Visual Studio .NET Core hata ayıklama kullanır. Bu hata ayıklama aynı zamanda bir işbirliği hata ayıklama ve .NET çalışma zamanı ile çalışır.

## <a name="using-the-debugger"></a>Hata ayıklamayı kullanma

Herhangi bir uygulamanın hata ayıklamaya başlamak için, yapılandırmanın **hata ayıklama**olarak ayarlı olduğundan her zaman emin olun. Hata ayıklama yapılandırması, kesme noktaları, veri görselleştiricileri kullanma ve çağrı yığınını görüntüleme gibi hata ayıklamayı destekleyen yararlı bir araç kümesi sağlar:

![Hata ayıklama yapılandırması](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Kesme noktası ayarlama

IDE'nizde bir kesme noktası ayarlamak için, sonvermek istediğiniz kodun satır numarasının yanındaki düzenleyicinizin kenar boşluğu alanını tıklatın:

![Kenar boşluğunda kesme noktası ayarlama](media/debugging-image0.png)

**Kesme Noktaları defterine**giderek kodunuzda ayarlanan tüm kesme noktalarını görüntüleyebilirsiniz:

![Kesme noktaları listesi](media/debugging-image0a.png)

## <a name="start-debugging"></a>Hata ayıklama yı başlatma

Hata ayıklamaya başlamak için hedef tarayıcıyı, cihazı veya simülatör/emülatörünü seçin:

![Hata ayıklama yapılandırmahedef](media/debugging-image_0.png)
![aygıtı seçin](media/debugging-image1.png)

Daha sonra **Play** butonuna veya Cmd + return tuşuna basarak uygulamanızı **dağıtın.** Bir kesme noktasına bastığınızda, kod sarı olarak vurgulanır:

![Kesme noktasının vurulduğunu gösteren vurgu](media/debugging-image2.png)

Nesnelerin değerlerini denetlemek için kullanılan gibi hata ayıklama araçları, bu noktada kodunuzda neler olup bittiği hakkında daha fazla bilgi almak için kullanılabilir:

![Hata ayıklama görselleştirmeleri](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Koşullu kesme noktaları

Ayrıca, bir kesme noktasının oluşması gereken koşulları belirleyen kurallar ayarlayabilirsiniz, bu *koşullu kesme noktası*ekleme olarak bilinir. Koşullu bir kesme noktası ayarlamak için, iki şekilde yapılabilecek **Breakpoint Özellikleri penceresine**erişin:

* Yeni bir koşullu kesme noktası eklemek için, bir kesme noktası ayarlamak istediğiniz kod için satır numarasının soluna düzenleyici kenar boşluğuna sağ tıklayın ve Yeni Kesme Noktası'nı seçin:

 ![Breakpoint bağlam menüsü](media/debugging-image4.png)

* Varolan bir kesme noktasına koşul eklemek için, kesme noktasına sağ tıklayın ve **Kesme Noktası Özellikleri'ni**seçin veya **Kesme Noktaları Defteri'nde**aşağıda gösterilen Breakpoint düğmesini seçin:

 ![Breakpoints Pad'de varolan Breakpoint'i edin](media/debugging-image5.png)

Daha sonra kesme noktasının oluşmasını istediğiniz durumu girebilirsiniz:

 ![Kesme Noktası koşullarını edin](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Kodda basma

Bir kesme noktasına ulaşıldığında, Hata Ayıklama araçları programın yürütülmesi üzerinde denetim elde etmenizi sağlar. Mac için Visual Studio, kodu çalıştırmanızı ve adım atmanızı sağlayan dört düğme görüntüler. Mac için Visual Studio'da aşağıdakigibi görünecektir:

 ![Kodda adım atmak için düğmeler](media/debugging-image7.png)

İşte dört düğme:

* **Play** - Bu, bir sonraki kesme noktasına kadar kodu yürütmeye başlayacaktır.
* **Adım Adım** - Bu bir sonraki kod satırını yürütecektir. Bir sonraki satır bir işlev çağrısıysa, Step Over işlevi yürütür ve işlevden *sonra* bir sonraki kod satırında durur.
* **Step Into** - Bu da bir sonraki kod satırını yürütecektir. Bir sonraki satır bir işlev çağrısıysa, Adım Adım işlevin ilk satırında durarak işlevin satır satır hata ayıklamasına devam etmenizi sağlar. Bir sonraki satır bir işlev değilse, Adım Atla aynı şekilde çalışır.
* **Dışarı Adım** - Bu, geçerli işlevin çağrıldığı satıra geri döner.

## <a name="debugging-monos-class-libraries"></a>Mono'nun sınıf kitaplıklarını hata ayıklama

Xamarin ürünleri Mono sınıf kütüphaneleri için kaynak kodu ile gemi ve bu başlık altında nasıl çalıştığını incelemek için hata ayıklayıcı tek bir adım için kullanabilirsiniz.

Bu özellik hata ayıklama sırasında daha fazla bellek tüketir, varsayılan olarak kapatılır.

Bu özelliği etkinleştirmek **için, Mac > Tercihleri için Visual Studio'ya** > Hata Ayıklayıcı'ya göz atın ve aşağıda gösterildiği gibi "**Dış koda Adım**" seçeneğinin **seçildiğinden**emin olun:

![Harici kod seçeneğine geçme](media/debugging-image8.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama (Windows'da)](/visualstudio/debugger/)
