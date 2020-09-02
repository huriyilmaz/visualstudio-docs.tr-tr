---
title: Grafik Tanılama genel bakış | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ddd429d9-ac70-4ac4-9e69-299c6ea2df09
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2dc0d0bf4efd8c30d874a24e94d3933d2eef713a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186562"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama’ya Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio *Grafik tanılama* , Direct3D uygulamalarında işleme ve performans sorunlarını kaydetmek ve analiz etmek için bir araç kümesidir. Grafik Tanılama, Windows bilgisayarınızda, Windows cihaz öykünücüsünde veya uzak bir bılgısayarda veya cihazda yerel olarak çalışan uygulamalarda kullanılabilir.

## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>İşleme sorunlarında hata ayıklamak için Grafik Tanılama'yı kullanma
 Grafik açısından zengin bir uygulamada işleme sorunları hatalarının ayıklanması, hata ayıklayıcıyı başlatıp herhangi bir kodda adım adım ilerlemek kadar basit işlem değildir. Her kare içinde, her biri karmaşık bir durum, veri, parametre ve kod kümesine göre olmak üzere yüz binlerce benzersiz piksel üretilirken, tanılamaya çalıştığınız sorunu bunlar arasında belki de yalnızca birkaç piksel sergileyecektir. He bir pikseli üreten kodun, yüzlerce pikseli paralel olarak işlemden geçiren özel amaçlı donanımlarda yürütülmesi meseleyi daha da karmaşık bir hale getirir. Çok fazla veriyle karşı karşıya kalındığında, iş parçacıklarının yoğun olmadığı kodlarda bile yarar sağlanması zor olan geleneksel hata ayıklama araçları ve teknikleri etkisiz kalmaktadır.

 İçindeki Grafik Tanılama araçları, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uygulamanın kendi kaynak kodunda yalnızca ilgili gölgelendirici kodu, ardışık düzen aşamaları, çizim çağrıları, kaynaklar ve cihaz durumu üzerine odaklanarak sorunun kaynağına geri dönerek işleme sorunlarını bulmanıza yardımcı olmak üzere tasarlanmıştır.

## <a name="directx-version-compatibility"></a>DirectX sürümü uyumluluğu
 Grafik Tanılama Direct3D 12, Direct3D 11 ve Direct3D 10 kullanan uygulamaları destekler ve Direct2D kullanan uygulamalar için sınırlı destek sağlar. Direct3D, DirectDraw veya diğer grafik API'lerinin önceki sürümlerini kullanan uygulamaları desteklemez.

### <a name="windows-10-and-direct3d-12"></a>Windows 10 ve Direct3D 12
 Windows 10, Direct3D 10 ve Direct3D 11 ' den önemli ölçüde farklı olan Direct3D, Direct3D *12*' nin bir sonraki sürümünü sunmaktadır. Bu farklılıklar, DirectX 'i modern grafik donanımı ile hizalı hale getirir ve tam potansiyelini açığa çıkarır, ancak büyük API değişikliklerini de getirir ve kaynak yaşam sürelerini ve çekişmeyi yönetmek için programcıya daha fazla sorumluluk yerleştirir. Grafik programcıların bu geçişi yapmasına yardımcı olmak için harika hata ayıklama araçlarının olması çok önemlidir. bu nedenle, Visual Studio 2015 ' deki Grafik Tanılama, başlangıçtan itibaren Direct3D12 hakkını destekler. Bu farklılıklara rağmen, Direct3D 12 ile Grafik Tanılama, Çerçeve Analizi özelliğinin geçerli özel durumu ile, Direct3D 11,2 ile Grafik Tanılama özellik eşliği sağlar. Yakında Direct3D 12 ' de çerçeve analizine yönelik destek eklenecektir ve sonra Direct3D 12 ' de karşılaşabileceğiniz yeni hata türlerini çözmenize yardımcı olacak yeni tanılama araçları eklenir.

 Windows 10 Ayrıca, Direct3D 'nin önceki sürümleri ve bunlara dayanan Oyunlar ve uygulamalar için destek sağlar. Visual Studio 2015 ' de Grafik Tanılama, Windows 10 ' da Direct3D 10 ve Direct3D 11 ' i desteklemeye devam eder, ayrıca Windows 8.1.

### <a name="windows-81-and-direct3d-112"></a>Windows 8.1 ve Direct3D 11,2
 [!INCLUDE[win81](../includes/win81-md.md)]' De DirectX 11,2, çalışma zamanı aracılığıyla grafik bilgilerini yakalamaya yönelik destek içeren yeni özellikler sunar. [!INCLUDE[win81](../includes/win81-md.md)] , yalnızca destekleyen tüm DirectX sürümleri için *güçlü yakalama*olarak bilinen yeni çalışma zamanı tabanlı yakalamayı kullanır [!INCLUDE[win81](../includes/win81-md.md)] . Sağlam yakalama Ayrıca Direct3D 11,2 'nin yeni özelliklerini de destekler.

### <a name="limited-direct2d-support"></a>Sınırlı Direct2D desteği
 Direct2D, Direct3D üzerine kurulu bir kullanıcı modu API'si olduğundan, Direct2D kullanan uygulamalarda işleme sorunlarındaki hataları ayıklamaya yardımcı olması için Grafik Tanılama'yı kullanabilirsiniz. Bununla birlikte, üst düzey Direct2D olayları yerine yalnızca temeli oluşturan Direct3D olayları kaydedildiğinden, Direct2D olayları Grafik Olay Listesi'nde görünmez. Ayrıca, Direct2D olayları ve sonuç Direct3D olayları arasındaki ilişki her zaman net olmadığından, Direct2D kullanan uygulamalarda işleme sorunları hatalarını ayıklamak için Grafik Tanılama kullanılması her zaman basit değildir. Yine de, Direct2D kullanan uygulamalarda düşük düzeyli işleme sorunları hakkında bilgi almak için Grafik Tanılama'yı kullanabilirsiniz.

## <a name="graphics-diagnostics-features-in-visual-studio"></a>Visual Studio 'da Grafik Tanılama Özellikleri
 Grafik Tanılama, işleme sorunlarını tanılamak için özel bir arabirime sahiptir — grafik Çözümleyicisi penceresi, ancak Visual Studio arabirimine bazı araçlar da ekler.

### <a name="the-graphics-toolbar-visual-studio"></a>Grafik araç çubuğu (Visual Studio)
 Grafik araç çubuğu Grafik Tanılama komutlara hızlı erişim sağlar.

 **Tanılamayı Başlat** düğmesi grafik tanılama altında uygulamayı çalıştırır. Grafik Tanılama altında bir uygulama çalıştığında, **sonraki işlenen çerçeveyi yakala** düğmesi etkinleştirilir.

### <a name="diagnostics-capture-interface"></a>Tanılama yakalama arabirimi
 Uygulamanızı Grafik Tanılama altında çalıştırdığınızda, Visual Studio çerçeveleri yakalamak için kullanabileceğiniz ve aynı zamanda geçerli CPU ve GPU yükünü görüntüleyen bir Tanılama oturumu arabirimini görüntüler. CPU ve GPU yükü, hataları işlemek yerine, performans özellikleri nedeniyle yakalamak isteyebileceğiniz çerçeveleri belirlemenize yardımcı olacak şekilde görüntülenir.

 Bu, ancak çerçeveleri yakalamaya yönelik tek yoldur. Ayrıca, Programlı yakalama arabirimini kullanarak veya dxcap.exe komut satırı yakalama programını kullanarak çerçeveler yakalayabilirsiniz.

 Daha fazla bilgi için bkz. [grafik bilgilerini yakalama](../debugger/capturing-graphics-information.md) .

### <a name="gpu-usage"></a>GPU Kullanımı
 Grafik Tanılama Ayrıca Direct3D uygulamanızın performansını da düzenleyebilir. Profil oluşturma verileri grafik olaylarının ayrıntıları kaydederek çarpılacağından, bu, grafik Çözümleyicisi ile incelenerek kullanılacak çerçeveleri yakalamaktan farklıdır.

 Daha fazla bilgi için bkz. [GPU kullanımı](../debugger/gpu-usage.md) .

### <a name="directx-control-panel"></a>DirectX denetim masası
 DirectX denetim masası, DirectX'in davranış şeklini değiştirmek için kullanabileceğiniz bir DirectX bileşenidir; örneğin, DirectX çalışma zamanı bileşenlerinin hata ayıklama sürümünü etkinleştirebilir, raporlanan hata ayıklama iletilerinin türünü seçebilir ve daha düşük kapasiteli donanımlara öykünmek için belirli grafik donanımı yeteneklerinin kullanılmasına izin vermeyebilirsiniz. DirectX üzerinde bu düzeyde bir denetim DirectX uygulamanızda hata ayıklamanıza ve uygulamayı test etmenize yardımcı olabilir. DirectX denetim masasına Visual Studio'dan erişebilirsiniz.

##### <a name="to-open-the-directx-control-panel"></a>DirectX denetim masasını açmak için

- Menü çubuğunda **Hata Ayıkla**, **grafikler**, **DirectX Denetim Masası**' nı seçin.

## <a name="graphics-analyzer"></a>Grafik Çözümleyicisi
 Visual Studio Grafik Çözümleyicisi, zaten yakaladığınız çerçevelerdeki işleme ve performans sorunlarını incelemek için ayrılmış bir arabirimdir. Grafik Çözümleyicisi 'nin içinde uygulamanızın işleme davranışını keşfetmenize ve anlamanıza yardımcı olacak çeşitli araçlar bulacaksınız. Her araç, incelenmekte olan çerçeve hakkında farklı türde bir bilgi sunar ve araçlar, bir işleme sorununun kaynağı üzerinde, framebuffer 'ın görünümüyle başlayarak bir işleme sorunu durumunda kullanılmak üzere tasarlanmıştır.

 Bu çizimde, grafik Çözümleyicisi 'ndeki araçların tipik bir düzeni gösterilmektedir.

 ![Tüm grafik hata ayıklayıcısı pencereleri](../debugger/media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")

### <a name="the-graphics-toolbar-graphics-analyzer"></a>Grafik araç çubuğu (grafik Çözümleyicisi)
 Grafik araç çubuğu, grafik Çözümleyicisi araç pencereleri için hızlı erişim sağlar.

 ![Grafik tanılama modundaki grafik araç çubuğu](../debugger/media/vsg-toolbar.png "vsg_toolbar")

### <a name="graphics-log-document"></a>Grafik günlük belgesi
 Grafik Çözümleyicisi 'nin içinde grafik günlük belgesi en belirgin araç penceresidir. Bu pencere, Grafik Tanılama altında uygulamanızı çalıştırarak yakaladığınız tüm kareleri temsil eder. Buradan, piksel geçmişi aracıyla incelemek istediğiniz belirli bir pikseli incelemek veya seçmek için farklı bir çerçeve seçebilirsiniz. Bu belgede görüntülenen framebuffer görüntüsü, framebuffer 'ın zaman içinde nasıl etkilendiğini görebilmeniz için, şu anda seçili olan olayı yansıtacak şekilde değişir.

 [Grafik günlük belgesi](../debugger/graphics-log-document.md) Ayrıca, oluşturma işlemi belirli yönlerinin yapılandırılıp orijinal ile karşılaştırılacağı kıyaslama sonuçları değiştirilerek bir çerçevenin performansını anlamanıza yardımcı olan Çerçeve Analizi aracına giriş noktasıdır.

### <a name="event-list"></a>Olay listesi
 Grafik olayları her Direct3D API çağrısını ve Kullanıcı tanımlı olayları işaretler.

 [Olay listesi](../debugger/graphics-event-list.md) , incelediğiniz çerçeve sırasında kaydedilen tüm grafik olaylarını gösterir. Ne önemli olduğunu bulmanıza yardımcı olmak için olay listesi, sonraki çizim çağrısının altındaki son durum değişiklikleri ile ya da bir zaman çizelgesi olarak hiyerarşik olarak görüntülenebilir. Ayrıca, olaylar ait oldukları sıraya göre renk kodludur ve yalnızca ilgilendiğiniz olayları içerecek şekilde listeye filtre uygulayabilirsiniz.

 Listede bir olay seçtiğinizde, grafik çözümleme araçlarının geri kalanı bu olay sırasında çerçevenin durumunu yansıtır. Bu şekilde, herhangi bir etkinliğin GPU üzerinde etkisini görebilirsiniz. Örneğin, sonraki çizim çağrıları tarafından gizlense bile, framebuffer üzerinde herhangi bir çizim çağrısının hemen etkisini görebilirsiniz. Ayrıca, bazı olaylarda, parametreleri veya ilgili kaynak nesneleri hakkında daha fazla ayrıntı görmek için izleyebileceğiniz köprüler de vardır.

### <a name="pipeline-stages"></a>Ardışık düzen aşamaları
 Uygulamanızdaki her çizim çağrısı, Direct3D tarafından sunulan grafik işlem hattı üzerinden geçer. İşlem hattının her aşamasında, önceki aşamadaki çıkış, gölgelendirici olarak adlandırılan küçük bir program tarafından dönüştürülür ve son olarak ekrana işlenene kadar sonraki aşamaya geçirilir. Çıkış biçimi bir sonraki aşamanın beklediği tarihten farklı olduğunda veya herhangi bir aşama hatalı sonuçlar ürettiğinden, çok sayıda işleme hatası ardışık düzen aşamaları arasındaki sınırda oluşur. Normalde, ekranınızda gördüğünüz gibi yalnızca nihai sonuçları elde edersiniz ve hata hattının nerede oluştuğunu kolayca anlayabilirsiniz.

 [Ardışık düzen aşamaları](../debugger/graphics-pipeline-stages.md) penceresi, her aşamanın sonucunu bağımsız olarak görselleştirir, böylece bir işleme sorununun ilk olarak hangi aşamada göründüğünü daha kolay bir şekilde belirleyebilmenizi sağlayabilirsiniz. Hangi aşamayı olduğunu belirledikten sonra, ardışık düzen aşamaları penceresinden gölgelendiricisinin hata ayıklamasını başlatabilirsiniz.

### <a name="graphics-state"></a>Grafik Durumu
 İşleme işlemleri, genellikle birden çok nesne arasında yayılan büyük bir duruma bağlıdır. Birçok tür işleme sorunu, yanlış yapılandırılmış durum nedeniyle oluşur.

 [Durum](../debugger/graphics-state.md) penceresi, her çizim çağrısıyla ilgili durum bilgilerini tek bir yerde toplayıp daha kolay bulunur ve ayrıca önceki çizim çağrısından bu yana gerçekleşen durum değişikliklerinin vurgulanmasını sağlar.

### <a name="pixel-history"></a>Piksel geçmişi
 Karmaşık sahneler içinde, bir pikselin tek bir karede birden çok kez gölgelendirilme yaygın olmayan bir durumdur. Bazen önceki rengin üzerine yazılır, ancak saydamlık gibi etkilere ulaşmak için renkler birlikte birleştirilir. Bunları birlikte birleştirmenin sonucu doğru görünüme sahip olmadığında, renklerin yanlış olduğunu veya birleştirilme yöntemiyle ilgili bir sorun olup olmadığını kolayca anlayabilirsiniz. Başka bir deyişle, pikselin katkısı bazı nedenlerle reddedildiği için bir nesne eksik görünebilir.

 [Piksel geçmişi](../debugger/graphics-pixel-history.md) penceresi, kabul edilecek katılımlar dahil olmak üzere, çerçevedeki her pikselin tam gölgelendirici geçmişini görselleştirir. Reddedilmeyen katkılar için, ham gölgelendirici sonuçlarını ve her yeni rengin öncekiyle birlikte nasıl birleştirildiğini görüntüler. Bu bilgilerle, hata kaynağını, gölgelendirici sonuçlarının karışdığı piksellerde veya bir işlenen nesne eksik olduğunda bulmak çok daha kolaydır çünkü pikselin katkısı yanlış bir şekilde reddediliyordu.

### <a name="event-call-stack"></a>Olay çağrısı yığını
 Gölgelendirici kodu, bir Direct3D uygulamasındaki işleme sorunlarının tek kaynağı değildir, bazen uygulamanızın kaynak kodu yanlış parametreyi geçirir ya da Direct3D 'yi doğrudan yapılandırmaz. Daha önce tartışılan özelliğin, piksel geçmişinin, tüm pikselleri reddedildiği için bir işlenen nesne eksik olduğu durumlarda, daha önce ele alınan bir hata türü. Bu tür bir hata, genellikle derinlik testinin nasıl gerçekleştirileceğini denetleyen bir ayarı yanlış yapılandırdığınızda oluşur ve genellikle yanlışlıkla hatalı nesnenin çizim çağrısının çağrı yığınında bir yerde bulunabilir.

 [Olay çağrı yığını](../debugger/graphics-event-call-stack.md) penceresi, olay listesindeki her grafik olayının tüm çağrı yığınını görüntüler, hatta hata ayıklama bilgisi varsa uygulamanızın kaynak koduna atlamanızı sağlar. Bu, GPU 'da, uygulamanın kaynak kodunda kaynaklandığı yere geri doğru bir hata takip etmek için güçlü bir araçtır.

### <a name="object-table"></a>Nesne tablosu
 Uygulamanızın oluşturduğu her çerçeve muhtemelen yüzlerce veya hatta binlerce kaynak nesnesi tarafından desteklenir. Bunlar, geri arabellekleri ve işleme hedeflerini, dokuları, köşe arabellekleri, dizin arabellekleri, genel arabellekleri içerebilir. neredeyse her şey Direct3D anımsar bir nesnedir.

 [Nesne tablosu](../debugger/graphics-object-table.md) , olay listesinde seçilen grafik olayı sırasında var olan tüm nesneleri görüntüler. Tipik bir uygulamadaki çoğu nesne dokularından olduğundan, bir bakışta görüntülerle ilgili ayrıntıları göstermek için olay listesi en iyi duruma getirilir. Tür sütunu, her satırda ne tür bir nesne olduğunu söyler ve biçim sütunu nesnenin alt türünü veya sürümünü gösterir. Diğer ayrıntılar da gösterilir. Bazı nesneler aynı zamanda, nesneyi daha özelleştirilmiş bir Görüntüleyici (örneğin, dokuyu bir resim olarak görüntüleyebilirsiniz) veya arabellekler gibi daha özel bir görüntüleyiciyle görüntülemek için kullanabileceğiniz köprülere sahiptir (arabellek biçimini tanımlayarak, arabellek görüntüleyicisinin ham arabellek baytlarını nasıl ayrıştırıp görüntüleyeceğini seçebilirsiniz).

### <a name="frame-analysis"></a>Çerçeve Analizi
 Uygulamanızın grafiklerin doğru olması gerekmez; bunlar hızlı bir şekilde olmalıdır. Tümleşik grafik veya cep telefonlarına sahip dizüstü bilgisayarlar gibi daha güçlü cihazlarda bile. Ayrıca, hala harika bir bakmaları gerekir.

 [Çerçeve Analizi](../debugger/graphics-frame-analysis.md) Aracı, uygulamanın Direct3D kullanma şeklini otomatik olarak değiştirerek ve karşılaştırma için kıyaslama sonuçları sağlayarak olası performans iyileştirmelerini araştırır. Örneğin, Çerçeve Analizi her dokuda MIP eşlemeyi etkinleştirebilir ve bu da MIP eşlemesinin avantajlarından faydalanabilecek ancak şu anda etkin olmayan dokuları açığa çıkarmayabilir. Bunu destekleyen donanımda, Çerçeve Analizi GPU 'nun performans sayaçlarından toplanan bilgileri de gösterir. bu bilgi düzeyi, yüksek sayıda doku getirme takılması veya önbellek isabetsizliği gibi donanım düzeyinde performans sorunlarını tanımlayabilir.

 Ancak Çerçeve Analizi yalnızca hızlı bir şekilde değil, en az sayıda görsel kalite elde edilirken en iyi performansı elde eteceğiz. Bazen büyük bir ekran üzerinde harika görünen pahalı bir efekt, daha basit bir etkinin pili boşaltmadan daha iyi görünebileceği bir telefonun küçük ekranında görüntülendiklerinde aynı etkiyi yapmaz. Grafik analizinin sağladığı otomatik değişiklikler ve değerlendirmeler, uygulamanız için bir dizi cihaz genelinde doğru olan dengeyi bulmanıza yardımcı olabilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Komut satırı yakalama aracı](../debugger/command-line-capture-tool.md) [HLSL hata ayıklayıcısı](../debugger/hlsl-shader-debugger.md)
