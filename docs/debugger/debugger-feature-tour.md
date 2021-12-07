---
title: Hata ayıklayıcıya ilk bakış
description: Visual Studio hata ayıklayıcısını kullanarak uygulamaları hata ayıklamaya başlama
ms.topic: conceptual
ms.date: 09/23/2021
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ce5685e4563d99d57490761869cca35791a3470c
ms.sourcegitcommit: 7a300823cf1bd3355be03bde561cf2777bc09eae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "133977793"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcıya ilk bakış

Bu konuda Visual Studio tarafından sunulan hata ayıklayıcı araçları tanıtılmaktadır. Visual Studio bağlamında, uygulamanızda *hata ayıklarken*, genellikle uygulamayı hata ayıklayıcı ekli (hata ayıklayıcı modunda) çalıştırdığınız anlamına gelir. Bunu yaptığınızda, hata ayıklayıcı kodun çalışırken ne yaptığını görmek için birçok yol sunar. Kodunuzda saklanan değerlere bakabilir ve değişkenlerde depolanan değerlere bakabilirsiniz, değerlerin ne zaman değişiklik olduğunu görmek için, değişkenlerinizin yürütme yolunu inceleyebilirsiniz. Kodu ilk kez ayıklamaya çalıştığınızda, bu konuya geçmeden önce [mutlak yeni başlayanlar Için hata ayıklama](../debugger/debugging-absolute-beginners.md) işlemini okumak isteyebilirsiniz.

burada açıklanan özellikler, C#, C++, Visual Basic, JavaScript ve Visual Studio tarafından desteklenen diğer diller için geçerlidir (aksi belirtilmedikçe).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Kesme noktası ayarlama ve hata ayıklayıcıyı başlatma

Kesme noktaları, kod satırını veya çalışma zamanında ayrıntılı olarak incelemek istediğiniz kod bölümünü bildiğiniz yararlı bir özelliktir. Koşullu kesme noktaları ve işlev kesme noktaları gibi farklı kesme noktaları türleri hakkında daha fazla bilgi için bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md).

Hata ayıklamak için, uygulama işlemine eklenmiş hata ayıklayıcı ile uygulamanızı başlatmanız gerekir. **F5** (**hata ayıklama > hata ayıklamayı Başlat**) bunu yapmanın en yaygın yoludur. Ancak, artık uygulama kodunuzu incelemek için herhangi bir kesme noktası ayarlanmamış olabilirsiniz; bu nedenle, önce bunu yapacağız ve ardından hata ayıklamayı başlatacak. Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. bir kesme noktası Visual Studio, çalışan kodunuzun nerede askıya alınacağını gösterir; böylece değişkenlerin değerlerine veya bellek davranışına ya da kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz.

Kod Düzenleyicisi 'nde açık bir dosyanız varsa, bir kod satırının solundaki kenar boşluğuna tıklayarak bir kesme noktası ayarlayabilirsiniz.

::: moniker range=">= vs-2022"
![Kesme noktası ayarlama](../debugger/media/vs-2022/dbg-tour-set-a-breakpoint.png "Kesme noktası ayarlama")
::: moniker-end
::: moniker range="<= vs-2019"
![Kesme noktası ayarlama](../debugger/media/dbg-tour-set-a-breakpoint.gif "Kesme noktası ayarlama")
::: moniker-end

**F5** tuşuna basın (hata ayıklama **> başlatma hata** ayıklaması) veya hata **ayıklamayı Başlat** düğmesi hata ayıklama araç çubuğunda ![başlatılır](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") ve hata ayıklayıcı karşılaştığı ilk kesme noktasına çalışır. Uygulama henüz çalışmıyorsa, F5 hata ayıklayıcıyı başlatır ve ilk kesme noktasında durmaktadır.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a> Adım komutlarını kullanarak hata ayıklayıcıda kodda gezinin

Çoğu komut için klavye kısayolları sağlıyoruz, çünkü uygulama kodunuzun daha hızlı bir şekilde gezinmesine dikkat edin. (Menü komutları gibi eşdeğer komutlar parantez içinde gösterilir.) Adım komutlarını kullanma hakkında daha fazla bilgi için bkz. [hata ayıklayıcıdaki koda gitme](../debugger/navigating-through-code-with-the-debugger.md).

Uygulamanızı hata ayıklayıcı eklenmiş olarak başlatmak için, **F11** tuşuna basın (**hata ayıklama > adımla**). F11, **adımla** komutuna ve aynı anda uygulama yürütmeyi tek bir ifadeye ilerletir. Uygulamayı F11 ile başlattığınızda, hata ayıklayıcı yürütülen ilk deyimde kesilir.

::: moniker range=">= vs-2022"
![F11 step INTO](../debugger/media/vs-2022/dbg-tour-f11.png "F11 Içine Adımla")
::: moniker-end
::: moniker range="<= vs-2019"
![F11 step INTO](../debugger/media/dbg-tour-f11.png "F11 Içine Adımla")
::: moniker-end

Sarı ok, hata ayıklayıcının duraklatıldığı ifadeyi temsil eder ve aynı noktada uygulama yürütmeyi de askıya alır (Bu bildirim henüz yürütülmemiştir).

F11, yürütme akışını en ayrıntılı incelemek için iyi bir yoldur. (Kod üzerinden daha hızlı hareket etmek için diğer bazı seçenekleri de göstereceğiz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan koddan atlar (daha fazla ayrıntı istiyorsanız, bkz. [yalnızca kendi kodum](../debugger/just-my-code.md)).

>[!NOTE]
> Yönetilen kodda, özellikleri ve işleçleri (varsayılan davranış) üzerinde otomatik olarak adımla uyarılmak isteyip istemediğinizi soran bir iletişim kutusu görürsünüz. Ayarı daha sonra değiştirmek istiyorsanız, **hata ayıklama** altındaki **Araçlar > seçenekler** menüsünde **Özellikler ve işleçler üzerinde adımla** ayarını devre dışı bırakın.

## <a name="step-over-code-to-skip-functions"></a>İşlevleri atlamak için kodun üzerinde adımla

Bir işlev veya yöntem çağrısı olan bir kod satırından olduğunuzda, **F11 (** **Hata Ayıkla > Step Over**) tuşuna basarak F11 yerine + tuşlarına basabilirsiniz.

F10 uygulama kodunuzda işlevlere veya yöntemlere adımla hata ayıklayıcıyı ilerletir (kod yine de çalıştırılır). F10 tuşuna basarak, ilgilenmediğiniz kodu atlayabilirsiniz. Bu şekilde, daha fazla ilgilendiğiniz koda hızlı bir şekilde ulaşabilirsiniz. Adım komutlarını kullanma hakkında daha fazla bilgi için bkz. [hata ayıklayıcıdaki koda gitme](../debugger/navigating-through-code-with-the-debugger.md).

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Fareyi kullanarak kodunuzda bir noktaya hızla çalışma

**Tıklama Için Çalıştır** düğmesinin kullanılması geçici bir kesme noktası ayarlamaya benzer. Bu komut, uygulama kodunun görünür bir bölgesinde hızlıca elde etmek için de kullanışlıdır. **Çalıştır ' ı** kullanarak herhangi bir açık dosyayı tıklatabilirsiniz. Bu özellik ve benzer gezinme özellikleri hakkında daha fazla bilgi için bkz. [kodunuzda belirli bir konuma çalıştırma](../debugger/navigating-through-code-with-the-debugger.md#run-to-a-specific-location-or-function).

hata ayıklayıcı sırasında,  ![ Visual Studio hata ayıklayıcısından tıklama düğmesine tıklayarak (yürütmeyi buraya çalıştır) düğme ekran görüntüsü olan bir kod satırının üzerine gelin. Düğme, yürütmenin düğmenin yerleştirildiği satıra çalışacağını belirtir.](../debugger/media/dbg-tour-run-to-click.png) Sol tarafta görüntülenir.

::: moniker range=">= vs-2022"
![işlev çağrısının yalnızca solunda görüntülenen tıklama düğmesine tıklayarak Visual Studio hata ayıklayıcının ekran görüntüsü.](../debugger/media/vs-2022/dbg-tour-run-to-click-2.png)
::: moniker-end
::: moniker range="<= vs-2019"
![işlev çağrısının yalnızca solunda görüntülenen tıklama düğmesine tıklayarak Visual Studio hata ayıklayıcının ekran görüntüsü.](../debugger/media/dbg-tour-run-to-click-2.png)
::: moniker-end

> [!NOTE]
> **Tıklama Için Çalıştır** (yürütmeyi buraya kadar Çalıştır) düğmesi, ' den itibaren kullanılabilir [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

**Çalıştırmak Için Çalıştır** ' a tıklayın (yürütmeyi buraya kadar Çalıştır) düğmesine tıklayın. Hata ayıklayıcı, tıklattığınız kod satırına ilerler.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Hata ayıklayıcıyı geçerli işlevin dışına ilerletin

Bazen hata ayıklama oturumunuzu devam ettirmek, ancak hata ayıklayıcıyı geçerli işlev aracılığıyla ilerletmek isteyebilirsiniz.

**SHIFT + F11** tuşlarına basın (veya **hata ayıklama > Step Out**).

Bu komut, geçerli işlev dönene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerletir).

## <a name="run-to-cursor"></a>İmlece kadar Çalıştır

Kodu düzenlediğinizde (hata ayıklayıcıda duraklama yerine), uygulamanızdaki bir kod satırına sağ tıklayın ve **Imlece git** ' i seçin (veya **CTRL** + **F10** tuşlarına basın). Bu komut, hata ayıklamaya başlar ve geçerli kod satırında geçici bir kesme noktası ayarlar. Bu özellik ve benzer gezinme özellikleri hakkında daha fazla bilgi için bkz. [kodunuzda belirli bir konuma çalıştırma](../debugger/navigating-through-code-with-the-debugger.md#run-to-a-specific-location-or-function).

::: moniker range=">= vs-2022"
![Imlece kadar Çalıştır](../debugger/media/vs-2022/dbg-tour-run-to-cursor.png "İmleç'e Çalıştır")
::: moniker-end
::: moniker range="<= vs-2019"
![Imlece kadar Çalıştır](../debugger/media/dbg-tour-run-to-cursor.png "İmleç'e Çalıştır")
::: moniker-end

Kesme noktaları ayarladıysanız, hata ayıklayıcı, isabet eden ilk kesme noktasında duraklatılır.

**Imlece çalıştırmayı** seçtiğiniz kod satırına ulaşana kadar **F5** tuşuna basın.

Bu komut, kodu düzenlediğinizde ve hızlı bir şekilde geçici bir kesme noktası ayarlamak ve hata ayıklayıcıyı aynı anda başlatmak istediğinizde yararlıdır.

> [!NOTE]
> Hata ayıklarken **çağrı yığını** penceresinde **imlece imlecini** kullanabilirsiniz.

## <a name="restart-your-app-quickly"></a>Uygulamanızı hızlıca yeniden başlatın

Hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![Başlat](../debugger/media/dbg-tour-restart.png "Uygulamayı Yeniden Başlatma") düğmesine tıklayın (veya **CTRL + SHIFT + F5** tuşlarına basın).

**Yeniden Başlat**'a bastığınızda, uygulamanın durdurulması ve hata ayıklayıcının yeniden başlatılması ile zaman kazandırır. Hata ayıklayıcı, kodu yürüterek vuran ilk kesme noktasında duraklatılır.

Hata ayıklayıcıyı durdurmak ve kod düzenleyicisine geri dönmek istiyorsanız, **Yeniden Başlat** yerine kırmızı Durdur ![hata ayıklamayı Durdur](../debugger/media/dbg-tour-stop-debugging.png "Hata Ayıklamayı Durdurma") düğmesine basabilirsiniz.

::: moniker range=">= vs-2022"
## <a name="live-code-editing"></a>Canlı kod düzenlemesi

Visual Studio 2022, hata ayıklarken canlı kod düzenlemesini destekler. Ayrıntılı bilgi için bkz.

- [Çalışan kodu yazma ve hata ayıklama](hot-reload.md)
- [Xaml dinamik yeniden yüklemesine çalışan XAML kodu yazma ve hata ayıklama](../xaml-tools/xaml-hot-reload.md)
- [Düzenle ve Devam Et](../debugger/edit-and-continue.md)

::: moniker-end
::: moniker range="<= vs-2019"
## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Kodunuzu düzenleyin ve hata ayıklamaya devam edin (C#, VB, C++, XAML)

Visual Studio tarafından desteklenen çoğu dilde, kodunuzu hata ayıklama oturumunun ortasında düzenleyebilir ve hata ayıklamaya devam edebilirsiniz. Bu özelliği kullanmak için, hata ayıklayıcıda duraklama, düzenleme yapın ve hata ayıklamaya devam etmek için **F5**, **F10** veya **F11** tuşuna basın. Bu özelliği ve özellik sınırlamalarını kullanma hakkında daha fazla bilgi için bkz. [Düzenle ve devam et](../debugger/edit-and-continue.md).

![Düzenle ve hata ayıklamayı Sürdür](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Bir hata ayıklama oturumu sırasında XAML kodunu değiştirmek için bkz. xaml [üzerinde çalışan xaml kodunu yazma ve hata ayıklama xaml çalışırken yeniden yükleme](../xaml-tools/xaml-hot-reload.md).
::: moniker-end

## <a name="inspect-variables-with-data-tips"></a>Veri ipuçları ile değişkenleri inceleyin

Biraz kısa bir süre içinde sizi öğrenmiş olduğunuza göre, uygulama durumunu (değişkenler) hata ayıklayıcıyla araştırmanız için iyi bir fırsattır. Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en faydalı özelliklerinden bazılarıdır ve bunu yapmak için farklı yollar vardır. Genellikle, bir sorunu ayıklamaya çalıştığınızda, değişkenlerin belirli bir uygulama durumunda olmasını istediğiniz değerleri depolayıp depoladığını bulmaya çalışıyorsunuz. Veri ipuçlarını kullanma hakkında ayrıntılı bilgi için bkz. veri [İpuçlarında veri değerlerini görüntüleme](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

Hata ayıklayıcıda duraklalarken, fare ile bir nesnenin üzerine gelin ve değerini ya da varsayılan özellik değerini görürsünüz.

::: moniker range=">= vs-2022"
![Veri Ipucunu görüntüleme](../debugger/media/vs-2022/dbg-tour-data-tips.png "Veri ipucu görüntüleme")
::: moniker-end
::: moniker range="<= vs-2019"
![Veri Ipucunu görüntüleme](../debugger/media/dbg-tour-data-tips.gif "Veri ipucu görüntüleme")
::: moniker-end

Değişkenin özellikleri varsa, tüm özelliklerini görmek için nesnesini genişletebilirsiniz.

Genellikle, hata ayıklarken, nesnelerdeki özellik değerlerini denetlemek için hızlı bir yol istersiniz ve veri ipuçları bunu yapmanın iyi bir yoludur.

> [!TIP]
> Desteklenen çoğu dilde kodu bir hata ayıklama oturumunun ortasında düzenleyebilirsiniz. Daha fazla bilgi için bkz. [Düzenle ve devam et](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Oto ve Yereller pencerelerinde değişkenleri İnceleme

**Oto** penceresinde, değişkenleri geçerli değerleri ve türleri ile birlikte görürsünüz. **Oto** penceresi, geçerli satırda veya önceki satırda kullanılan tüm değişkenleri gösterir (C++ ' da, pencerede önceki üç kod satırındaki değişkenler gösterilir. Dile özgü davranışın belgelerini denetleyin). Bu pencereleri kullanma hakkında daha fazla bilgi için, [Bkz. Otomatikler ve Yereller pencerelerinde değişkenleri inceleme.](../debugger/autos-and-locals-windows.md)

Hata ayıklama sırasında, kod **düzenleyicisinin** en altındaki Otomatikler penceresine bakın.

::: moniker range=">= vs-2022"
![Otomatikler Penceresi](../debugger/media/vs-2022/dbg-tour-autos-window.png "Otomatik değişkenler penceresi")
::: moniker-end
::: moniker range="<= vs-2019"
![Otomatikler Penceresi](../debugger/media/dbg-tour-autos-window.png "Otomatik değişkenler penceresi")
::: moniker-end

> [!NOTE]
> JavaScript'te **Yereller** penceresi desteklene, ancak Otomatikler **penceresi desteklanmaz.**

Ardından Yereller **penceresine** bakın. **YerelLer** penceresinde, şu anda kapsamda olan değişkenler gösterilir.

::: moniker range=">= vs-2022"
![YerelLer Penceresi](../debugger/media/vs-2022/dbg-tour-locals-window.png "Yerel öğeler penceresi")
::: moniker-end
::: moniker range="<= vs-2019"
![YerelLer Penceresi](../debugger/media/dbg-tour-locals-window.png "Yerel öğeler penceresi")
::: moniker-end

Bu örnekte, `this` nesnesi ve nesnesi `f` kapsamdadır. Daha fazla bilgi için, [bkz. Inspect Variables in the Autos and Locals Windows.](../debugger/autos-and-locals-windows.md)

## <a name="set-a-watch"></a>Saat ayarlama

İzleme penceresi **kullanarak** göz tutmak istediğiniz bir değişken (veya ifade) belirtebilirsiniz. Ayrıntılı bilgi için [bkz. Watch ve QuickWatch](../debugger/watch-and-quickwatch-windows.md)kullanarak watch Windows.

Hata ayıklama sırasında bir nesneye sağ tıklayın ve İzleme **Ekle'yi seçin.**

::: moniker range=">= vs-2022"
![İzleme Penceresi](../debugger/media/vs-2022/dbg-tour-watch-window.png "Gözcü penceresi")
::: moniker-end
::: moniker range="<= vs-2019"
![İzleme Penceresi](../debugger/media/dbg-tour-watch-window.png "Gözcü penceresi")
::: moniker-end

Bu örnekte nesnesinde bir izleme kümesi vardır ve hata ayıklayıcıda ilerlerken değerinin değişmesini sebilirsiniz. Diğer değişken pencerelerinin aksine, **İzle** pencereleri her zaman izlediğiniz değişkenleri gösterir (kapsam dışındayken bunlar gri renkte görünür).

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleme

Çağrı **Yığını** penceresi, yöntemlerin ve işlevlerin çağrıldığı sırayı gösterir. Üst satır geçerli işlevi gösterir. İkinci satırda işlevi veya işlevin çağrıldı olduğu özellik gibi bir şey yer almaktadır. Çağrı yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yol sağlar. Ayrıntılı bilgi için [bkz. Nasıl: Çağrı Yığınını Inceleme.](../debugger/how-to-use-the-call-stack-window.md)

> [!NOTE]
> Çağrı **Yığını penceresi,** Eclipse gibi bazı IDE'lerde Hata Ayıklama perspektifi ile benzerdir.

Hata **ayıklama sırasında,** varsayılan olarak sağ alt bölmede açık olan Çağrı Yığını penceresine tıklayın.

::: moniker range=">= vs-2022"
![Çağrı Yığınını Inceleme](../debugger/media/vs-2022/dbg-tour-call-stack.png "Çağrı yığınını inceleme")
::: moniker-end
::: moniker range="<= vs-2019"
![Çağrı Yığınını Inceleme](../debugger/media/dbg-tour-call-stack.png "Çağrı yığınını inceleme")
::: moniker-end

Bir kod satırına çift tıklar ve bu koda göz atabilir ve hata ayıklayıcı tarafından denetlenen geçerli kapsamı da değiştirir. Bu, hata ayıklayıcıyı ilerleten bir işlem değildir.

Başka şeyler yapmak için Çağrı Yığını penceresinden sağ **tıklama** menülerini de kullanabilirsiniz. Örneğin, belirli işlevlere kesme noktaları ekler, İmleçte Çalıştır'ı kullanarak uygulamanızı yeniden başlatabilir ve kaynak kodu incelemeye gidebilirsiniz.

## <a name="inspect-an-exception"></a><a name="exception"></a> Özel durumu inceleme

Uygulamanız bir özel durum atarsa, hata ayıklayıcı sizi özel durumu başlatan kod satırına alır. Ayrıntılı bilgi için [bkz. Özel Durum Yardımcı'sı kullanarak bir özel durumu inceleme.](../debugger/exception-helper.md)

::: moniker range=">= vs-2022"
![Özel Durum Yardımcı](../debugger/media/vs-2022/dbg-tour-exception-helper.png "Özel Durum Yardımcı")

Bu örnekte, Özel **Durum Yardımcı nesne** başvurusu nesnenin bir örneğine ayar olmadığını söyleyen bir özel durum ve hata iletisi `System.NullReferenceException` gösterir. Ayrıca, yöntemini çağırmayı dene denediğimiz zaman dize değerinin null olduğunu `Trim` söyler.
::: moniker-end
::: moniker range="<= vs-2019"
![Özel Durum Yardımcı](../debugger/media/dbg-tour-exception-helper.png "Özel Durum Yardımcı")

Bu örnekte, Özel **Durum Yardımcısı** size bir özel durum ve yolun yasal bir form olmadığını `System.Argument` söyleyen bir hata iletisi gösterir. Bu nedenle hatanın bir yöntem veya işlev bağımsız değişkende olduğunu biliyoruz.

Bu örnekte `DirectoryInfo` çağrısı, değişkende depolanan boş dizede hata `value` verdi.
::: moniker-end

Özel Durum Yardımcı, hatalarda hata ayıklamanıza yardımcı olan harika bir özelliktir. Ayrıca hata ayrıntılarını görüntüleme ve Özel Durum Yardımcı'dan izleme ekleme gibi şeyler de ebilirsiniz. Veya gerekirse, belirli bir özel durumu atma koşullarını değiştirebilirsiniz. Kodundaki özel durumları işleme hakkında daha fazla bilgi için bkz. [Hata ayıklama teknikleri ve araçları.](../debugger/write-better-code-with-visual-studio.md)

Bu özel **durum Ayarlar** işleme hakkında daha fazla seçenek görmek için Özel Durum Kümesi düğümünü genişletin, ancak bu tur için hiçbir şeyi değiştirmeniz gerekmeyecek!

## <a name="configure-debugging"></a>Hata ayıklamayı yapılandırma

Projenizi Hata Ayıklama veya Yayın yapılandırması [olarak](../debugger/how-to-set-debug-and-release-configurations.md)derlemek, hata ayıklama için proje özelliklerini yapılandırmak veya hata ayıklama için [genel ayarları](../debugger/how-to-specify-debugger-settings.md) yapılandırmak üzere yapılandırabilirsiniz. Ayrıca hata ayıklayıcıyı [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) özniteliği veya C/C++ için NatVis çerçevesi gibi özellikleri kullanarak özel bilgileri [görüntüleyebilirsiniz.](create-custom-views-of-native-objects.md)

Hata ayıklama özellikleri her proje türüne özeldir. Örneğin, uygulamayı başlatarak uygulamaya geçeceği bir bağımsız değişken belirtebilirsiniz. projesinde projeye sağ tıklar ve Özellikler'i seçerek Çözüm Gezgini özelliklere **erişebilirsiniz.** Hata ayıklama özellikleri genellikle belirli bir **proje** **türüne** bağlı olarak Derleme veya Hata Ayıklama sekmesinde görünür.

::: moniker range=">= vs-2022"
2022'den başlayarak .NET projeleri için Hata Ayıklama sekmesi, hata ayıklamayla ilgili özellikleri ayarlayarak hata ayıklama başlatma profilleri kullanıcı arabirimine bir bağlantı sağlar. Visual Studio 

![Project özellikleri](../debugger/media/vs-2022/dbg-tour-project-properties.png "Proje özellikleri")
::: moniker-end
::: moniker range="<= vs-2019"
![Project özellikleri](../debugger/media/dbg-tour-project-properties.png "Proje özellikleri")
::: moniker-end

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Azure App Service'ASP.NET canlı Azure App Service

bu **Snapshot Debugger,** ilgilendiğiniz kod yürütülürken üretim uygulamalarınıza bir anlık görüntü alır. Hata ayıklayıcıya anlık görüntü alma talimatı almak için kodunda anlık görüntü noktaları ve günlük noktaları ayarlayın. Hata ayıklayıcısı, üretim uygulama trafiğinizi etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Bu Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için gereken zamanı önemli ölçüde azaltmanıza yardımcı olabilir.

::: moniker range="<= vs-2019"
![Anlık görüntü hata ayıklayıcısını başlatma](../debugger/media/snapshot-launch.png "Anlık görüntü hata ayıklayıcısını başlatma")
::: moniker-end

Anlık görüntü koleksiyonu, ASP.NET çalışan uygulamalar için Azure App Service. ASP.NET uygulamaların .NET Framework 4.6.1 veya sonraki bir ASP.NET Core üzerinde, ASP.NET Core uygulamalarının da Windows üzerinde .NET Core 2.0 veya sonraki bir Windows.

Daha fazla bilgi için [bkz. ASP.NET kullanarak canlı Snapshot Debugger.](../debugger/debug-live-azure-applications.md)

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>IntelliTrace geri adım atarak anlık görüntüleri görüntüleme (Visual Studio Enterprise)

**IntelliTrace geri adımı,** her kesme noktası ve hata ayıklayıcı adımı olayında otomatik olarak uygulamanın anlık görüntüsünü alır. Kaydedilen anlık görüntüler, önceki kesme noktalarına veya adımlara geri dönmenizin yanı sıra uygulamanın geçmişte olduğu gibi durumunu görüntülemeye olanak sağlar. IntelliTrace geri adımı önceki uygulama durumunu görmek istediğiniz ancak hata ayıklamayı yeniden başlatmak veya istenen uygulama durumunu yeniden oluşturmak istemeyebilirsiniz.

Hata Ayıklama araç çubuğundaki Geri Adım ve İleri **Adım** düğmelerini **kullanarak** anlık görüntülerde gezinebilirsiniz ve görüntüleyebilirsiniz. Bu düğmeler, Tanılama Araçları **penceresindeki** Olaylar **sekmesinde görünen Tanılama Araçları** gezinebilirsiniz.

::: moniker range="<= vs-2019"
![Geri ve İleri Adım Düğmeleri](../debugger/media/intellitrace-step-back-icons-description.png  "Geri ve İleri Adım düğmeleri")
::: moniker-end

Daha fazla bilgi için [IntelliTrace kullanarak önceki uygulama eyaletlerini inceleme sayfasına](../debugger/view-historical-application-state.md) bakın.

## <a name="debug-performance-issues"></a>Performans sorunlarını ayıklama

Uygulamanız çok yavaş çalışıyorsa veya çok fazla bellek kullanıyorsa, profil oluşturma araçlarıyla erkenden test etmek zorundayabilirsiniz. CPU Kullanımı aracı ve Bellek Çözümleyicisi gibi profil oluşturma araçları hakkında daha fazla bilgi için bkz. Profil oluşturma [araçlarına ilk bakış.](../profiling/profiling-feature-tour.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, birçok hata ayıklayıcı özelliğine hızlı bir bakış edindi. Kesme noktaları gibi bu özelliklerden birini daha ayrıntılı bir şekilde görmek istiyor olabilir.

> [!div class="nextstepaction"]
> [Kesme noktaları kullanmayı öğrenin](../debugger/using-breakpoints.md)
