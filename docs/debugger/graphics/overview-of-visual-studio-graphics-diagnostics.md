---
title: Grafik tanılama bilgilerine genel | Microsoft Docs
description: Visual Studio Grafik Tanılama, Direct3D etkinliğini günlüğe kaydeden ve işleme ve performans sorunlarını gidermek için günlükleri analiz etmek için bir araç kümesidir.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24b67b9585db973e6cbef3b1c28c6068e7c37034
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386208"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama’ya Genel Bakış
Visual Studio *Grafik Tanılama,* Direct3D uygulamaları içinde işleme ve performans sorunlarını kaydetmeye ve analize yönelik bir araç kümesidir. Grafik Tanılama, Windows bilgisayarınızda veya uzak bir bilgisayarda veya cihazda yerel olarak çalışan uygulamalarda kullanılabilir.

## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>İşleme sorunlarında hata ayıklamak için Grafik Tanılama'yı kullanma
 Grafik açısından zengin bir uygulamada işleme sorunlarını ayıklamak, bir hata ayıklayıcıyı başlatma ve bazı kodlarda adımlama kadar kolay değildir. Her kare içinde, her biri karmaşık bir durum, veri, parametre ve kod kümesine göre olmak üzere yüz binlerce benzersiz piksel üretilirken, tanılamaya çalıştığınız sorunu bunlar arasında belki de yalnızca birkaç piksel sergileyecektir. He bir pikseli üreten kodun, yüzlerce pikseli paralel olarak işlemden geçiren özel amaçlı donanımlarda yürütülmesi meseleyi daha da karmaşık bir hale getirir. Çok fazla veriyle karşı karşıya kalındığında, iş parçacıklarının yoğun olmadığı kodlarda bile yarar sağlanması zor olan geleneksel hata ayıklama araçları ve teknikleri etkisiz kalmaktadır.

 'daki Grafik Tanılama araçları, sorunu belirten görsel yapıtlarla başlayarak ve ardından uygulamanın kendi kaynak kodunda yalnızca ilgili gölgelendirici koduna, işlem hattı aşamalarına, çekme çağrıları, kaynaklar ve cihaz durumuna odaklanarak sorunun kaynağına geri dönerek işleme sorunlarını bulumaya yardımcı olmak için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tasarlanmıştır.

## <a name="directx-version-compatibility"></a>DirectX sürümü uyumluluğu
 Grafik Tanılama, Direct3D 10 veya daha büyük bir kullanan uygulamaları destekler ve Direct2D kullanan uygulamalar için sınırlı destek sağlar. Direct3D, DirectDraw veya diğer grafik API'lerinin önceki sürümlerini kullanan uygulamaları desteklemez.

### <a name="windows-10-and-direct3d-12"></a>Windows 10 ve Direct3D 12
> [!NOTE]
> Visual Studio DirectX 12 oyunları için Windows'da PIX önerilir. [Windows'da PIX,](https://aka.ms/PIXonWindows) DirectX 12'yi tam olarak destekleyen bir performans ayarlama ve hata ayıklama aracıdır. [Daha fazla bilgi için buraya bakın](visual-studio-graphics-diagnostics-directx-12.md) veya [indirin.](https://aka.ms/downloadPIX)


 Windows 10 *Direct3D 10 ve Direct3D 11'den* önemli ölçüde farklı olan Direct3D 12'yi tanıttık. Bu farklar DirectX'i modern grafik donanımıyla yeniden hizalamaya ve tam potansiyelini ortaya çıkarmanın yanı sıra büyük API değişiklikleri de getirir ve programcının kaynak yaşam sürelerini ve içeriğini yönetmeye yönelik daha büyük sorumluluklar getirir. Farklılıklara rağmen, Direct3D 12 ile Grafik Tanılama, Direct3D 11.2 ile Grafik Tanılama eşlik sağlar.

 Windows 10, Direct3D'nin önceki sürümleri ve onlara bağlı olan oyun ve uygulamalar için de destek sağlar. Grafik Tanılama Visual Studio direct3D 10 ve Direct3D 11'i desteklemeye devam Windows 10.

### <a name="limited-direct2d-support"></a>Sınırlı Direct2D desteği
 Direct2D, Direct3D üzerinde yerleşik bir kullanıcı modu API'si olduğundan, Direct2D kullanan uygulamalarda işleme sorunlarının Grafik Tanılama hata ayıklamaya yardımcı olmak için Grafik Tanılama kullanabilirsiniz. Bununla birlikte, üst düzey Direct2D olayları yerine yalnızca temeli oluşturan Direct3D olayları kaydedildiğinden, Direct2D olayları Grafik Olay Listesi'nde görünmez. Ayrıca, Direct2D olayları ve sonuç Direct3D olayları arasındaki ilişki her zaman net olmadığından, Direct2D kullanan uygulamalarda işleme sorunları hatalarını ayıklamak için Grafik Tanılama kullanılması her zaman basit değildir. Yine de, Direct2D kullanan uygulamalarda düşük düzeyli işleme sorunları hakkında bilgi almak için Grafik Tanılama'yı kullanabilirsiniz.

## <a name="graphics-diagnostics-features-in-visual-studio"></a>Grafik Tanılama özellikleri Visual Studio
 Grafik Tanılama sorunları tanılamak için Grafik Çözümleyicisi penceresi gibi ayrılmış bir arabirime sahiptir, ancak aynı zamanda grafik arabirimine bazı Visual Studio ekler.

### <a name="the-graphics-toolbar-visual-studio"></a>Grafik araç çubuğu (Visual Studio)
 Grafik araç çubuğu, komutlara hızlı Grafik Tanılama sağlar.

 Tanılamayı **Başlat düğmesi** uygulamayı uygulamanın altında Grafik Tanılama. Bir uygulama, bir Grafik Tanılama altında **çalıştırıldığında, Sonraki işlenmiş çerçeveyi yakala** düğmesi etkinleştirilir.

### <a name="diagnostics-capture-interface"></a>Tanılama yakalama arabirimi
 Uygulamanızı Grafik Tanılama Visual Studio çerçeveleri yakalamak için kullanabileceğiniz ve geçerli CPU ve GPU yükünü de görüntüleyen bir tanılama oturumu arabirimi görüntülenir. CPU ve GPU yükü, hataları işleme yerine performans özellikleri nedeniyle yakalamak istediğiniz kareleri tanımlamanıza yardımcı olmak için görüntülenir.

 Ancak kareleri yakalamanın tek yolu bu değildir. Ayrıca, programlı yakalama arabirimini kullanarak veya komut satırı yakalama programını kullanarak çerçeveleri dxcap.exe.

 Daha [fazla bilgi için bkz.](capturing-graphics-information.md) Grafik Bilgilerini Yakalama.

### <a name="gpu-usage"></a>GPU Kullanımı
 Grafik Tanılama, Direct3D uygulama performansının profilini de oluşturmanızı sağlar. Profil oluşturma verileri grafik olaylarının ayrıntıları kaydederek çarpıtılanaca, grafik çözümleyicisi ile incelenecek kareleri yakalamaktan ayrıdır.

 Daha [fazla bilgi için bkz. GPU](../../profiling/gpu-usage.md) Kullanımı.

### <a name="directx-control-panel"></a>DirectX denetim masası
 DirectX denetim masası, DirectX'in davranış şeklini değiştirmek için kullanabileceğiniz bir DirectX bileşenidir; örneğin, DirectX çalışma zamanı bileşenlerinin hata ayıklama sürümünü etkinleştirebilir, raporlanan hata ayıklama iletilerinin türünü seçebilir ve daha düşük kapasiteli donanımlara öykünmek için belirli grafik donanımı yeteneklerinin kullanılmasına izin vermeyebilirsiniz. DirectX üzerinde bu düzeyde bir denetim DirectX uygulamanızda hata ayıklamanıza ve uygulamayı test etmenize yardımcı olabilir. DirectX denetim masasına Visual Studio'dan erişebilirsiniz.

#### <a name="to-open-the-directx-control-panel"></a>DirectX denetim masasını açmak için

- Menü çubuğunda Hata Ayıkla,  **Grafikler,** **DirectX ve Denetim Masası.**

## <a name="graphics-analyzer"></a>Grafik Çözümleyicisi
 Bu Visual Studio Grafik Çözümleyicisi, zaten yakaladığımız karelerde işleme ve performans sorunlarını incelemeye yönelik ayrılmış bir arabirimdir. Grafik Çözümleyicisi'nin içinde, uygulama işleme davranışını keşfetmenize ve anlamanıza yardımcı olacak çeşitli araçlar bulabilirsiniz. Her araç inceleyen çerçeve hakkında farklı türlerde bilgiler sunar ve araçlar çerçevenin içinde görünümünden başlayarak işleme sorununun kaynağında sezgisel olarak daraltmak için birlikte kullanılacak şekilde tasarlanmıştır.

 Bu çizimde, Grafik Çözümleyicisi'nin tipik bir araç düzeni gösterilir.

 ![Tüm grafik hata ayıklayıcısı pencereleri](media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")

### <a name="the-graphics-toolbar-graphics-analyzer"></a>Grafik araç çubuğu (Grafik Çözümleyicisi)
 Grafik araç çubuğu, Grafik Çözümleyicisi araç pencerelerine hızlı erişim sağlar.

 ![Grafik tanılama modundaki Grafik araç çubuğu](media/vsg_toolbar.png "vsg_toolbar")

### <a name="graphics-log-document"></a>Grafik günlüğü belgesi
 Grafik Çözümleyicisi'nin içinde grafik günlüğü belgesi en öne çıkan araç penceresidir. Bu pencere, uygulamalarınızı uygulama altında çalıştırarak yakaladığınız tüm kareleri Grafik Tanılama. Buradan, Piksel Geçmişi aracıyla incelemek istediğiniz belirli bir pikseli incelemek veya seçmek için farklı bir kareyi seçin. Bu belgede görüntülenen framebuffer görüntüsü, seçili durumdaki Olayı yansıtacak şekilde değişir, böylece framebuffer'ın zaman içinde nasıl etkilendiğini görebilirsiniz.

 Grafik [Günlüğü Belgesi](graphics-log-document.md) ayrıca Çerçeve Analizi aracının giriş noktasıdır. Bu, işlemenin belirli yönlerinin yapılandırılması yolunu değiştirerek ve özgünle karşılaştırıldığında karşılaştırma sonuçları sağlayarak çerçevenin performansını anlamanıza yardımcı olur.

### <a name="event-list"></a>Olay listesi
 Grafik olayları her Direct3D API çağrısını ve kullanıcı tanımlı olayı işaretler.

 Olay [Listesi,](graphics-event-list.md) inceleyeni çerçeve sırasında kaydedilen tüm grafik olaylarını gösterir. Önemli olan şeyi bulanıza yardımcı olmak için olay listesi hiyerarşik olarak(sonraki çizim çağrısının altında son durum değişiklikleriyle) veya bir zaman çizelgesi olarak ekleyebilirsiniz. Buna ek olarak, olaylar ait olduğu kuyruğa göre renk kodludur ve listeyi yalnızca ilgilendiğiniz olayları içerecek şekilde filtreleyebilirsiniz.

 Listeden bir olay seçerek Grafik Analizi araçlarının geri kalanı ilgili olay sırasında çerçevenin durumunu gösterir. Bu şekilde, herhangi bir olayın GPU üzerindeki etkisini görebilir. Örneğin, sonraki çizim çağrıları tarafından belirsiz hale gelse bile kare kasası üzerinde herhangi bir çizim çağrısının hemen etkisini görüntülebilirsiniz. Bazı olaylar, parametreleri veya ilgili kaynak nesneleri hakkında daha fazla ayrıntı görmek için takip etmek istediğiniz köprülere de sahiptir.

### <a name="pipeline-stages"></a>İşlem hattı aşamaları
 Uygulamanıza yönelik her çizim çağrısı, Direct3D tarafından sağlanan grafik işlem hattına gider. İşlem hattında her aşamada, önceki aşamadan gelen çıkış gölgelendirici olarak adlandırılan küçük bir program tarafından dönüştürülerek son olarak ekrana işlenene kadar sonraki aşamaya geçirildi. Çıkış biçimi bir sonraki aşamanın beklediğinizden farklı olduğunda veya herhangi bir aşama yanlış sonuçlar ürettiğinde işlem hattı aşamaları arasındaki sınırda birçok işleme hatası oluşur. Normalde, yalnızca ekranda gördüğünüz gibi son sonuçları alırsınız ve işlem hattında hatanın nerede olduğunu kolayca söylemek mümkün değil.

 İşlem [Hattı Aşamaları](graphics-pipeline-stages.md) penceresi, bir işleme sorununun ilk olarak hangi aşamada görüntülendiğinden daha kolay bir şekilde belirleyesiniz için her aşamanın sonucu bağımsız olarak görselleştiri. Hangi aşamanın olduğunu belirlediktan sonra, gölgelendiricisinde hata ayıklamaya hemen İşlem Hattı Aşamaları penceresinden başlayabilirsiniz.

### <a name="graphics-state"></a>Grafik Durumu
 İşleme işlemleri genellikle birden çok nesne arasında yayılan çok sayıda duruma bağlıdır. Birçok tür işleme sorunu yanlış yapılandırılmış durumdan kaynaklandı.

 Durum [penceresi,](graphics-state.md) her çizim çağrısıyla ilgili durum bilgilerini tek bir yerde toplar, böylece daha kolay bulunacaktır ve ayrıca önceki çizim çağrısından bu yana meydana gelen durum değişikliklerini vurgular.

### <a name="pixel-history"></a>Piksel geçmişi
 Karmaşık sahnelerde bir pikselin tek bir karede birden çok kez gölgelendirmesi yaygın bir durumdur. Bazen önceki rengin üzerine yazılır, ancak bazen saydamlık gibi etkiler elde etmek için renkler bir araya gelir. Bunları birleştirmenin sonucu doğru görünüme sahip değilken renklerin yanlış olması veya birleştirildikleriyle ilgili bir sorun olup olmadığını kolayca anlayabilirsiniz. Diğer durumlarda, piksele olan katkısı herhangi bir nedenle reddedilmesi nedeniyle bir nesne eksik gibi görünebilir.

 Piksel [Geçmişi penceresi,](graphics-pixel-history.md) reddedilen katkılar dahil olmak üzere çerçevede her pikselin tam gölgelendirici geçmişini görselleştirin. Reddedilen katkılar için ham gölgelendirici sonuçlarını ve her yeni rengin önceki renkle nasıl birleştirildiklerini görüntüler. Bu bilgilerle piksel cinsinden blend gölgelendiricisi sonuçlarına neden olan hataların kaynağını bulmak veya piksele olan katkısı hatalı bir şekilde reddedilmesi nedeniyle işlenmiş bir nesnenin eksik olması çok daha kolaydır.

### <a name="event-call-stack"></a>Olay çağrı yığını
 Gölgelendirici kodu, Direct3D uygulamasındaki işleme sorunlarının tek kaynağı değil, bazen de uygulamanın kaynak kodu yanlış parametreyi geçer veya Direct3D'yi doğru yapılandırmaz. Daha önce tartışılan Piksel Geçmişi özelliğinin, işlenmiş bir nesnenin eksik olduğu ve tüm piksellerinin reddedilmesi gibi bir hatanın size yardımcı olduğu bir hata türü vardır. Bu tür hatalar genellikle derinlik testinin nasıl gerçekleştirileceklerini kontrol eden ayar gibi bir ayarı yanlış yapılandırarak gerçekleşir ve hatanızı genellikle eksik nesnenin draw çağrısının çağrı yığınında bulabilirsiniz.

 Olay [Çağrı Yığını penceresi,](graphics-event-call-stack.md) Olay Listesi'nin tüm grafik olaylarının çağrı yığınını görüntüler ve hatta hata ayıklama bilgileri varsa uygulamanın kaynak koduna atlamanıza olanak sağlar. Bu, GPU'da ilk göründüğü yerden, uygulamanın kaynak kodunda geldiği yere geri dönarak bir hatayı takip etmek için güçlü bir araçtır.

### <a name="object-table"></a>Nesne tablosu
 Uygulama işlemesi yapılan her çerçeve büyük olasılıkla yüzlerce, hatta binlerce kaynak nesnesi tarafından de desteklene sahiptir. Bunlar geri arabellekleri ve işleme hedeflerini, dokuları, köşe arabelleklerini, dizin arabelleklerini, genel arabellekleri içerebilir. Direct3D'nin hatırlayacağı neredeyse her şey bir nesnedir.

 Nesne [Tablosu,](graphics-object-table.md) olay listesinde seçilen grafik olayı sırasında mevcut olan tüm nesneleri görüntüler. Tipik bir uygulamadaki nesnelerin çoğu doku olduğundan, olay listesi görüntülerle ilgili ayrıntıları bir bakışta göstermek için en iyi duruma getirilmiştir. Tür sütunu size her satırda ne tür bir nesne olduğunu söyler ve Biçim sütunu daha sonra nesnenin alt türünü veya sürümünü gösterir. Diğer ayrıntılar da gösterilir. Bazı nesnelerin, dokular (dokuyu görüntü olarak görüntüleyebilirsiniz) veya arabellekler (arabellek görüntüleyicinin arabellek biçimini tanımlayarak ham arabellek baytlarını ayrıştırma ve görüntülemesini seçebilirsiniz) gibi daha özel bir görüntüleyiciye sahip nesneyi görüntülemek için iz izleyebilirsiniz köprüleri de vardır.

### <a name="frame-analysis"></a>Çerçeve analizi
 Uygulama grafiğinizin yalnızca doğru olması değil, hızlı olması da gerekir. Tümleşik grafiklere veya cep telefonlarına sahip dizüstü bilgisayarlar gibi daha az güçlü cihazlarda bile. Ayrıca yine de harika bir görünüme sahip olmak zorundalar.

 Çerçeve [Analizi aracı,](graphics-frame-analysis.md) uygulamanın Direct3D kullanma yolunu otomatik olarak değiştirerek ve karşılaştırma için karşılaştırma sonuçları sağlayarak olası performans iyileştirmelerini keşfeder. Örneğin, Çerçeve Analizi her dokuda mip eşlemeyi etkinleştirip mip eşlemeden yararlanabilecek dokuları ortaya çıkarabilecek ancak şu anda etkinleştirilmemiş olabilir. Çerçeve Analizi, bunu destekleyen donanımlarda GPU'nun performans sayaçlarından toplanan bilgileri de sunar. Bu bilgi düzeyi, çok sayıda doku getirme durakları veya önbellek isabet isabeti gibi donanım düzeyinde performans sorunlarını tanımlayabilir.

 Ancak Çerçeve Analizi yalnızca hızlı olmakla ilgili değil, en az miktarda görsel kalitesini bırakarak en yüksek performansı elde etmektir. Bazen büyük ekranda harika görünen pahalı bir etki, bir telefonun küçük ekranında görüntüleniyorsa aynı etkiye neden olmaz ve pil boşaltmadan daha basit bir etki de aynı şekilde iyi görünür. Grafik Analizi'nin sağladığı otomatik değişiklikler ve karşılaştırmalar, çeşitli cihazlarda uygulamanıza uygun bakiyeyi bulamanıza yardımcı olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Komut Satırı Yakalama Aracı](command-line-capture-tool.md)
- [HLSL Hata Ayıklayıcısı](hlsl-shader-debugger.md)
