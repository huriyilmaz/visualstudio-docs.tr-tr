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
ms.openlocfilehash: 416f49e5c02ffddfb4dfff449a1e21986b828c9d
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970769"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcıya ilk bakış

Bu konuda Visual Studio tarafından sunulan hata ayıklayıcı araçları tanıtılmaktadır. Visual Studio bağlamında, uygulamanızda *hata ayıklarken*, genellikle uygulamayı hata ayıklayıcı ekli (hata ayıklayıcı modunda) çalıştırdığınız anlamına gelir. Bunu yaptığınızda, hata ayıklayıcı kodun çalışırken ne yaptığını görmek için birçok yol sunar. Kodunuzda saklanan değerlere bakabilir ve değişkenlerde depolanan değerlere bakabilirsiniz, değerlerin ne zaman değişiklik olduğunu görmek için, değişkenlerinizin yürütme yolunu inceleyebilirsiniz. Kodu ilk kez ayıklamaya çalıştığınızda, bu konuya geçmeden önce [mutlak yeni başlayanlar Için hata ayıklama](../debugger/debugging-absolute-beginners.md) işlemini okumak isteyebilirsiniz.

burada açıklanan özellikler, C#, C++, Visual Basic, JavaScript ve Visual Studio tarafından desteklenen diğer diller için geçerlidir (aksi belirtilmedikçe).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Kesme noktası ayarlama ve hata ayıklayıcıyı başlatma

Kesme noktaları, kod satırını veya çalışma zamanında ayrıntılı olarak incelemek istediğiniz kod bölümünü bildiğiniz yararlı bir özelliktir. Koşullu kesme noktaları ve işlev kesme noktaları gibi farklı kesme noktaları türleri hakkında daha fazla bilgi için bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md).

Hata ayıklamak için, uygulama işlemine eklenmiş hata ayıklayıcı ile uygulamanızı başlatmanız gerekir. **F5** (**hata ayıklama > hata ayıklamayı Başlat**) bunu yapmanın en yaygın yoludur. Ancak, artık uygulama kodunuzu incelemek için herhangi bir kesme noktası ayarlanmamış olabilirsiniz; bu nedenle, önce bunu yapacağız ve ardından hata ayıklamayı başlatacak. Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. bir kesme noktası Visual Studio, çalışan kodunuzun nerede askıya alınacağını gösterir; böylece değişkenlerin değerlerine veya bellek davranışına ya da kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz.

Kod Düzenleyicisi 'nde açık bir dosyanız varsa, bir kod satırının solundaki kenar boşluğuna tıklayarak bir kesme noktası ayarlayabilirsiniz.

![Kesme noktası ayarlama](../debugger/media/dbg-tour-set-a-breakpoint.gif "Kesme noktası ayarlama")

**F5** tuşuna basın (hata ayıklama **> başlatma hata** ayıklaması) veya hata **ayıklamayı Başlat** düğmesi hata ayıklama araç çubuğunda ![başlatılır](../debugger/media/dbg-tour-start-debugging.png "Hata ayıklamayı Başlat") ve hata ayıklayıcı karşılaştığı ilk kesme noktasına çalışır. Uygulama henüz çalışmıyorsa, F5 hata ayıklayıcıyı başlatır ve ilk kesme noktasında durmaktadır.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a> Adım komutlarını kullanarak hata ayıklayıcıda kodda gezinin

Çoğu komut için klavye kısayolları sağlıyoruz, çünkü uygulama kodunuzun daha hızlı bir şekilde gezinmesine dikkat edin. (Menü komutları gibi eşdeğer komutlar parantez içinde gösterilir.) Adım komutlarını kullanma hakkında daha fazla bilgi için bkz. [hata ayıklayıcıdaki koda gitme](../debugger/navigating-through-code-with-the-debugger.md).

Uygulamanızı hata ayıklayıcı eklenmiş olarak başlatmak için, **F11** tuşuna basın (**hata ayıklama > adımla**). F11, **adımla** komutuna ve aynı anda uygulama yürütmeyi tek bir ifadeye ilerletir. Uygulamayı F11 ile başlattığınızda, hata ayıklayıcı yürütülen ilk deyimde kesilir.

![F11 step INTO](../debugger/media/dbg-tour-f11.png "F11 step INTO")

Sarı ok, hata ayıklayıcının duraklatıldığı ifadeyi temsil eder ve aynı noktada uygulama yürütmeyi de askıya alır (Bu bildirim henüz yürütülmemiştir).

F11, yürütme akışını en ayrıntılı incelemek için iyi bir yoldur. (Kod üzerinden daha hızlı hareket etmek için diğer bazı seçenekleri de göstereceğiz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan koddan atlar (daha fazla ayrıntı istiyorsanız, bkz. [yalnızca kendi kodum](../debugger/just-my-code.md)).

>[!NOTE]
> Yönetilen kodda, özellikleri ve işleçleri (varsayılan davranış) üzerinde otomatik olarak adımla uyarılmak isteyip istemediğinizi soran bir iletişim kutusu görürsünüz. Ayarı daha sonra değiştirmek istiyorsanız, **hata ayıklama** altındaki **Araçlar > seçenekler** menüsünde **Özellikler ve işleçler üzerinde adımla** ayarını devre dışı bırakın.

## <a name="step-over-code-to-skip-functions"></a>İşlevleri atlamak için kodun üzerinde adımla

Bir işlev veya yöntem çağrısı olan bir kod satırından olduğunuzda, **F11 (** **Hata Ayıkla > Step Over**) tuşuna basarak F11 yerine + tuşlarına basabilirsiniz.

F10 uygulama kodunuzda işlevlere veya yöntemlere adımla hata ayıklayıcıyı ilerletir (kod yine de çalıştırılır). F10 tuşuna basarak, ilgilenmediğiniz kodu atlayabilirsiniz. Bu şekilde, daha fazla ilgilendiğiniz koda hızlı bir şekilde ulaşabilirsiniz. Adım komutlarını kullanma hakkında daha fazla bilgi için bkz. [hata ayıklayıcıdaki koda gitme](../debugger/navigating-through-code-with-the-debugger.md).

## <a name="step-into-a-property"></a>Bir özelliğe adımla

Daha önce belirtildiği gibi, hata ayıklayıcı yönetilen özellikleri ve alanları atlar, ancak **belirli komuta adım** bu davranışı geçersiz kılmanıza olanak tanır.

Bir özellik veya alana sağ tıklayın ve **belirli bir adımla**' i seçin, sonra da kullanılabilir seçeneklerden birini belirleyin.

![Visual Studio hata ayıklayıcının vurgulanmış bir kod satırıyla ilgili ekran görüntüsü. Bağlam menüsünde belirli bir adımla seçilir ve Path. set yöntemi seçilidir.](../debugger/media/dbg-tour-step-into-specific.png)

Bu örnekte, **belirli bir adımla** ilgili kodu bize alır `Path.set` .

![Path. set kodunu gösteren Visual Studio hata ayıklayıcının ekran görüntüsü. Küme işlevini çevreleyen küme ayraçları sarı renkle vurgulanır.](../debugger/media/dbg-tour-step-into-specific-2.png)

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Fareyi kullanarak kodunuzda bir noktaya hızla çalışma

**Tıklama Için Çalıştır** düğmesinin kullanılması geçici bir kesme noktası ayarlamaya benzer. Bu komut, uygulama kodunun görünür bir bölgesinde hızlıca elde etmek için de kullanışlıdır. **Çalıştır ' ı** kullanarak herhangi bir açık dosyayı tıklatabilirsiniz. Bu özellik ve benzer gezinme özellikleri hakkında daha fazla bilgi için bkz. [kodunuzda belirli bir konuma çalıştırma](../debugger/navigating-through-code-with-the-debugger.md#run-to-a-specific-location-or-function).

hata ayıklayıcı sırasında,  ![ Visual Studio hata ayıklayıcısından tıklama düğmesine tıklayarak (yürütmeyi buraya çalıştır) düğme ekran görüntüsü olan bir kod satırının üzerine gelin. Düğme, yürütmenin düğmenin yerleştirildiği satıra çalışacağını belirtir.](../debugger/media/dbg-tour-run-to-click.png) Sol tarafta görüntülenir.

![Visual Studio hata ayıklayıcının, yalnızca Update işlevine yapılan çağrının solunda görüntülenen tıklama düğmesini gösteren ekran görüntüsü.](../debugger/media/dbg-tour-run-to-click-2.png)

> [!NOTE]
> **Tıklama Için Çalıştır** (yürütmeyi buraya kadar Çalıştır) düğmesi, ' den itibaren kullanılabilir [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

**Çalıştırmak Için Çalıştır** ' a tıklayın (yürütmeyi buraya kadar Çalıştır) düğmesine tıklayın. Hata ayıklayıcı, tıklattığınız kod satırına ilerler.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Hata ayıklayıcıyı geçerli işlevin dışına ilerletin

Bazen hata ayıklama oturumunuzu devam ettirmek, ancak hata ayıklayıcıyı geçerli işlev aracılığıyla ilerletmek isteyebilirsiniz.

**SHIFT + F11** tuşlarına basın (veya **hata ayıklama > Step Out**).

Bu komut, geçerli işlev dönene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerletir).

## <a name="run-to-cursor"></a>İmlece kadar Çalıştır

Kodu düzenlediğinizde (hata ayıklayıcıda duraklama yerine), uygulamanızdaki bir kod satırına sağ tıklayın ve **Imlece git** ' i seçin (veya **CTRL** + **F10** tuşlarına basın). Bu komut, hata ayıklamaya başlar ve geçerli kod satırında geçici bir kesme noktası ayarlar. Bu özellik ve benzer gezinme özellikleri hakkında daha fazla bilgi için bkz. [kodunuzda belirli bir konuma çalıştırma](../debugger/navigating-through-code-with-the-debugger.md#run-to-a-specific-location-or-function).

![Imlece kadar Çalıştır](../debugger/media/dbg-tour-run-to-cursor.png "Imlece kadar Çalıştır")

Kesme noktaları ayarladıysanız, hata ayıklayıcı, isabet eden ilk kesme noktasında duraklatılır.

**Imlece çalıştırmayı** seçtiğiniz kod satırına ulaşana kadar **F5** tuşuna basın.

Bu komut, kodu düzenlediğinizde ve hızlı bir şekilde geçici bir kesme noktası ayarlamak ve hata ayıklayıcıyı aynı anda başlatmak istediğinizde yararlıdır.

> [!NOTE]
> Hata ayıklarken **çağrı yığını** penceresinde **imlece imlecini** kullanabilirsiniz.

## <a name="restart-your-app-quickly"></a>Uygulamanızı hızlıca yeniden başlatın

Hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![Başlat](../debugger/media/dbg-tour-restart.png "Uygulamayı yeniden Başlat") düğmesine tıklayın (veya **CTRL + SHIFT + F5** tuşlarına basın).

**Yeniden Başlat**'a bastığınızda, uygulamanın durdurulması ve hata ayıklayıcının yeniden başlatılması ile zaman kazandırır. Hata ayıklayıcı, kodu yürüterek vuran ilk kesme noktasında duraklatılır.

Hata ayıklayıcıyı durdurmak ve kod düzenleyicisine geri dönmek istiyorsanız, **Yeniden Başlat** yerine kırmızı Durdur ![hata ayıklamayı Durdur](../debugger/media/dbg-tour-stop-debugging.png "Hata ayıklamayı Durdur") düğmesine basabilirsiniz.

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>Kodunuzu düzenleyin ve hata ayıklamaya devam edin (C#, VB, C++, XAML)

Visual Studio tarafından desteklenen çoğu dilde, kodunuzu hata ayıklama oturumunun ortasında düzenleyebilir ve hata ayıklamaya devam edebilirsiniz. Bu özelliği kullanmak için, hata ayıklayıcıda duraklama, düzenleme yapın ve hata ayıklamaya devam etmek için **F5**, **F10** veya **F11** tuşuna basın. Bu özelliği ve özellik sınırlamalarını kullanma hakkında daha fazla bilgi için bkz. [Düzenle ve devam et](../debugger/edit-and-continue.md).

![Düzenle ve hata ayıklamayı Sürdür](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Bir hata ayıklama oturumu sırasında XAML kodunu değiştirmek için bkz. xaml [üzerinde çalışan xaml kodunu yazma ve hata ayıklama xaml çalışırken yeniden yükleme](../xaml-tools/xaml-hot-reload.md).

## <a name="inspect-variables-with-data-tips"></a>Veri ipuçları ile değişkenleri inceleyin

Biraz kısa bir süre içinde sizi öğrenmiş olduğunuza göre, uygulama durumunu (değişkenler) hata ayıklayıcıyla araştırmanız için iyi bir fırsattır. Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en faydalı özelliklerinden bazılarıdır ve bunu yapmak için farklı yollar vardır. Genellikle, bir sorunu ayıklamaya çalıştığınızda, değişkenlerin belirli bir uygulama durumunda olmasını istediğiniz değerleri depolayıp depoladığını bulmaya çalışıyorsunuz. Veri ipuçlarını kullanma hakkında ayrıntılı bilgi için bkz. veri [İpuçlarında veri değerlerini görüntüleme](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

Hata ayıklayıcıda duraklalarken, fareyle bir nesnenin üzerine gelin ve varsayılan özellik değerini görürsünüz (Bu örnekte, dosya adı `market 031.jpg` varsayılan özellik değeridir).

![Veri Ipucunu görüntüleme](../debugger/media/dbg-tour-data-tips.gif "Veri ipucunu görüntüleme")

Tüm özelliklerini görmek için nesneyi genişletin ( `FullPath` Bu örnekteki özelliği gibi).

Genellikle, hata ayıklarken, nesnelerdeki özellik değerlerini denetlemek için hızlı bir yol istersiniz ve veri ipuçları bunu yapmanın iyi bir yoludur.

> [!TIP]
> Desteklenen çoğu dilde kodu bir hata ayıklama oturumunun ortasında düzenleyebilirsiniz. Daha fazla bilgi için bkz. [Düzenle ve devam et](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Oto ve Yereller pencerelerinde değişkenleri İnceleme

**Oto** penceresinde, değişkenleri geçerli değerleri ve türleri ile birlikte görürsünüz. **Oto** penceresi, geçerli satırda veya önceki satırda kullanılan tüm değişkenleri gösterir (C++ ' da, pencerede önceki üç kod satırındaki değişkenler gösterilir. Dile özgü davranışın belgelerini denetleyin). Bu pencereleri kullanma hakkında daha fazla bilgi için bkz. [oto ve Yereller pencerelerinde değişkenleri İnceleme](../debugger/autos-and-locals-windows.md).

Hata ayıklarken, kod düzenleyicisinin alt kısmındaki **oto** penceresine bakın.

![Oto penceresi](../debugger/media/dbg-tour-autos-window.png "Otomatik değişkenler penceresi")

> [!NOTE]
> JavaScript 'te, **Yereller** penceresi desteklenir, ancak **oto** penceresi desteklenmez.

Sonra, **Yereller** penceresine bakın. **Yereller** penceresi, şu anda kapsamda olan değişkenleri gösterir.

![Yereller penceresi](../debugger/media/dbg-tour-locals-window.png "Yerel öğeler penceresi")

Bu örnekte, `this` nesnesi ve nesnesi `f` kapsamdadır. Daha fazla bilgi için bkz. [oto ve yereller Windows değişkenleri İnceleme](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>İzleme ayarlama

Bir gözü tutmak istediğiniz bir değişken (veya bir ifade) belirtmek için bir **Gözcü** penceresi kullanabilirsiniz. Ayrıntılı bilgi için bkz. [izleme ve hızlı izleme Windows kullanarak Izleme ayarlama](../debugger/watch-and-quickwatch-windows.md).

Hata ayıklarken, bir nesneye sağ tıklayın ve **Gözcü Ekle**' yi seçin.

![Gözcü penceresi](../debugger/media/dbg-tour-watch-window.png "Gözcü penceresi")

Bu örnekte, nesnesinde bir izleme kümesi vardır `f` ve hata ayıklayıcıda geçiş yaparken değer değişikliğini görebilirsiniz. Diğer değişken pencerelerinin aksine, **Watch** Windows her zaman izlemekte olduğunuz değişkenleri gösterir (kapsam dışında gri renkte bulunur).

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleyin

Çağrı yığını penceresi, yöntemlerin ve işlevlerin hangi sırada **çağrılacağını** gösterir. Üstteki satırda geçerli işlev ( `Update` Bu örnekteki yöntem) gösterilir. İkinci satır, `Update` `Path.set` özelliğinden çağrılan ve bu şekilde devam eden gösterir. Çağrı yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yoldur. Ayrıntılı bilgi için bkz. [nasıl yapılır: çağrı yığınını İnceleme](../debugger/how-to-use-the-call-stack-window.md).

> [!NOTE]
> **Çağrı yığını** penceresi, tutulma gibi bazı NDES 'Teki hata ayıklama perspektifine benzer.

Hata ayıklarken **çağrı yığını** penceresine, varsayılan olarak sağ alt bölmede da açık ' a tıklayın.

![Çağrı yığınını inceleyin](../debugger/media/dbg-tour-call-stack.png "Çağrı yığınını inceleyin")

Bir kod satırına çift tıklayarak bu kaynak koda bakabilir ve ayrıca hata ayıklayıcı tarafından incelenen geçerli kapsamı da değiştirebilirsiniz. Bu, hata ayıklayıcıyı ilerlemez.

Ayrıca, **çağrı yığını** penceresindeki diğer işlemleri yapmak için sağ tıklama menülerini de kullanabilirsiniz. Örneğin, belirli işlevlere kesme noktaları ekleyebilirsiniz, uygulamayı **Imlece Çalıştır**' ı kullanarak yeniden başlatabilir ve kaynak kodunu inceleyebilirsiniz.

## <a name="inspect-an-exception"></a><a name="exception"></a> Özel durum İnceleme

Uygulamanız bir özel durum oluşturduğunda, hata ayıklayıcı sizi özel durumu oluşturan kod satırına götürür. Ayrıntılı bilgi için bkz. [özel durum yardımcısını kullanarak özel durum İnceleme](../debugger/exception-helper.md).

![Özel durum Yardımcısı](../debugger/media/dbg-tour-exception-helper.png "Özel durum Yardımcısı")

Bu örnekte, **özel durum Yardımcısı** size bir `System.Argument` özel durum ve yolun geçerli bir form olmadığını belirten bir hata iletisi gösterir. Bu nedenle, bir yöntem veya işlev bağımsız değişkeninde oluşan hatayı biliyoruz.

Bu örnekte, çağrı, `DirectoryInfo` değişkende depolanan boş dizede hata verdi `value` .

Özel durum Yardımcısı, hata ayıklamanıza yardımcı olabilecek harika bir özelliktir. Hata ayrıntılarını görüntüle ve özel durum Yardımcısı 'ndan bir izleme ekleme gibi işlemler de yapabilirsiniz. Ya da gerekirse, belirli bir özel durumu oluşturma koşullarını değiştirebilirsiniz. Kodunuzda özel durumların nasıl işleneceği hakkında daha fazla bilgi için bkz. [hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md).

bu özel durum türünün nasıl işleneceği hakkında daha fazla seçenek görmek için **özel durum Ayarlar** düğümünü genişletin, ancak bu tur için herhangi bir şeyi değiştirmeniz gerekmez!

## <a name="configure-debugging"></a>Hata ayıklamayı yapılandırma

Projenizi hata ayıklama [veya sürüm yapılandırması](../debugger/how-to-set-debug-and-release-configurations.md)olarak derlemek, hata ayıklama için proje özelliklerini yapılandırmak veya hata ayıklama için [genel ayarları](../debugger/how-to-specify-debugger-settings.md) yapılandırmak üzere yapılandırabilirsiniz. Buna ek olarak, hata ayıklayıcıyı, [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) özniteliği gibi özellikleri kullanarak özel bilgileri görüntüleyecek şekilde veya C/C++, [Natvis çerçevesi](create-custom-views-of-native-objects.md)için de yapılandırabilirsiniz.

Hata ayıklama özellikleri her proje türüne özeldir. Örneğin, uygulamayı başlattığınızda uygulamaya geçirilecek bir bağımsız değişken belirtebilirsiniz. Projeye özgü özelliklere Çözüm Gezgini ' de projeye sağ tıklayıp **Özellikler**' i seçerek erişebilirsiniz. Hata ayıklama özellikleri, belirli proje türüne bağlı olarak genellikle **derleme** veya **hata ayıklama** sekmesinde görüntülenir.

![Project özellikleri](../debugger/media/dbg-tour-project-properties.png "Proje özellikleri")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Azure App Service içindeki canlı ASP.NET uygulamalarda hata ayıkla

**Snapshot Debugger** , yürütirken ilgilendiğiniz kodun yürütüldüğü üretim içi uygulamalarınızın anlık görüntüsünü alır. Hata ayıklayıcıya bir anlık görüntü almasını söylemek için kodunuzda anlık görüntü noktaları ve günlüğe kaydetme noktaları ayarlarsınız. Hata ayıklayıcı, üretim uygulamanızın trafiğini etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için geçen süreyi önemli ölçüde düşürmeye yardımcı olabilir.

![Snapshot Debugger 'ı başlatın](../debugger/media/snapshot-launch.png "Snapshot Debugger 'ı başlatın")

anlık görüntü koleksiyonu, Azure App Service çalıştıran ASP.NET uygulamalar için kullanılabilir. ASP.NET uygulamalar .NET Framework 4.6.1 veya sonraki bir sürümde çalışmalıdır ve ASP.NET Core uygulamaların Windows üzerinde .net Core 2,0 veya üzeri sürümlerde çalışıyor olması gerekir.

daha fazla bilgi için bkz. [Snapshot Debugger kullanarak canlı ASP.NET uygulamalarda hata ayıklama](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>IntelliTrace adım geri (Visual Studio Enterprise) ile anlık görüntüleri görüntüleme

**IntelliTrace adım geri** alma, her kesme noktası ve hata ayıklayıcı adım olayında uygulamanızın bir anlık görüntüsünü otomatik olarak alır. Kaydedilen anlık görüntüler, önceki kesme noktalarına veya adımlara geri dönmenize ve uygulamanın geçmişte olduğu gibi durumunu görüntülemenize imkan tanır. IntelliTrace adım geri dönüş, önceki uygulama durumunu görmek istediğinizde, ancak hata ayıklamayı yeniden başlatmak veya istenen uygulama durumunu yeniden oluşturmak istemediğinizde size zaman kazandırabilir.

Hata ayıklama araç çubuğundaki **geri** ve **adım ileri** düğmelerini kullanarak anlık görüntülerle gezinerek görüntüleyebilirsiniz. Bu düğmeler **Tanılama araçları** penceresindeki **Olaylar** sekmesinde görüntülenen olaylara gider.

![Geri adımla ve Ilet düğmeleri](../debugger/media/intellitrace-step-back-icons-description.png  "Geri adımla ve Ilet düğmeleri")

Daha fazla bilgi için bkz. [IntelliTrace kullanarak önceki uygulama durumlarını İnceleme](../debugger/view-historical-application-state.md) sayfası.

## <a name="debug-performance-issues"></a>Hata ayıklama performans sorunları

Uygulamanız çok yavaş çalışırsa veya çok fazla bellek kullanıyorsa, uygulamanızı önce profil oluşturma araçlarıyla test etmeniz gerekebilir. CPU kullanımı aracı ve bellek Çözümleyicisi gibi profil oluşturma araçları hakkında daha fazla bilgi için bkz. [profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide birçok hata ayıklayıcı özelliğine hızlı bir bakış sunuyoruz. Kesme noktaları gibi bu özelliklerden birine daha ayrıntılı bir bakış istemeniz gerekebilir.

> [!div class="nextstepaction"]
> [Kesme noktaları kullanmayı öğrenin](../debugger/using-breakpoints.md)
