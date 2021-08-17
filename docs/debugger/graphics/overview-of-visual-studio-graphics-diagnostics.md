---
title: Grafik tanılama 'ya genel bakış | Microsoft Docs
description: Visual Studio Grafik Tanılama, Direct3D etkinliğini günlüğe kaydetmek için bir araç kümesidir ve işleme ve performans sorunlarını gidermek için günlükleri analiz eder.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8a84700548af7db2281d666cd51bd6293bd884b4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090856"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama’ya Genel Bakış
Visual Studio *Grafik Tanılama* , Direct3D uygulamalarında işleme ve performans sorunlarını kaydetmek ve analiz etmek için bir araç kümesidir. Grafik Tanılama, Windows PC 'nizde veya uzak bir bilgisayarda ya da cihazda yerel olarak çalışan uygulamalarda kullanılabilir.

## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>İşleme sorunlarında hata ayıklamak için Grafik Tanılama'yı kullanma
 Grafik açıdan zengin bir uygulamada işleme sorunlarının hata ayıklaması, bir hata ayıklayıcıyı başlatıp bazı kodlar arasında geçiş yapmak kadar basit değildir. Her kare içinde, her biri karmaşık bir durum, veri, parametre ve kod kümesine göre olmak üzere yüz binlerce benzersiz piksel üretilirken, tanılamaya çalıştığınız sorunu bunlar arasında belki de yalnızca birkaç piksel sergileyecektir. He bir pikseli üreten kodun, yüzlerce pikseli paralel olarak işlemden geçiren özel amaçlı donanımlarda yürütülmesi meseleyi daha da karmaşık bir hale getirir. Çok fazla veriyle karşı karşıya kalındığında, iş parçacıklarının yoğun olmadığı kodlarda bile yarar sağlanması zor olan geleneksel hata ayıklama araçları ve teknikleri etkisiz kalmaktadır.

 İçindeki Grafik Tanılama araçları, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uygulamanın kendi kaynak kodunda yalnızca ilgili gölgelendirici kodu, ardışık düzen aşamaları, çizim çağrıları, kaynaklar ve cihaz durumu üzerine odaklanarak sorunun kaynağına geri dönerek işleme sorunlarını bulmanıza yardımcı olmak üzere tasarlanmıştır.

## <a name="directx-version-compatibility"></a>DirectX sürümü uyumluluğu
 Grafik Tanılama, Direct3D 10 veya üzerini kullanan uygulamaları destekler ve Direct2D kullanan uygulamalar için sınırlı destek sağlar. Direct3D, DirectDraw veya diğer grafik API'lerinin önceki sürümlerini kullanan uygulamaları desteklemez.

### <a name="windows-10-and-direct3d-12"></a>Windows 10 ve Direct3D 12
> [!NOTE]
> Visual Studio, DirectX 12 oyunları Windows için pıx ' i önerir. [Windows pıx](https://aka.ms/PIXonWindows) , DirectX 12 ' nin tam olarak desteklediği bir performans ayarlama ve hata ayıklama aracıdır. [Daha fazla bilgi edinin](visual-studio-graphics-diagnostics-directx-12.md) veya [buradan indirin](https://aka.ms/downloadPIX).


 Windows 10 direct3d 10 ve direct3d 11 ' den önemli ölçüde farklı olan *direct3d 12*' yi sunmuştur. Bu farklılıklar, DirectX 'i modern grafik donanımı ile hizalı hale getirir ve tam potansiyelini açığa çıkarır, ancak büyük API değişikliklerini de getirir ve kaynak yaşam sürelerini ve çekişmeyi yönetmek için programcıya daha fazla sorumluluk yerleştirir. Farklılıklara, Direct3D 12 ile Grafik Tanılama, Direct3D 11,2 ile Grafik Tanılama özellik eşliği sağlar.

 Windows 10 ayrıca, daha önceki Direct3D sürümleri ve bunlara dayanan oyunlar ve uygulamalar için destek sağlar. Visual Studio Grafik Tanılama Windows 10 direct3d 10 ve direct3d 11 ' i desteklemeye devam etmektedir.

### <a name="limited-direct2d-support"></a>Sınırlı Direct2D desteği
 Direct2D, Direct3D üzerinde oluşturulmuş bir Kullanıcı modu API 'SI olduğundan, Direct2D kullanan uygulamalardaki işleme sorunlarını ayıklamanıza yardımcı olmak için Grafik Tanılama kullanabilirsiniz. Bununla birlikte, üst düzey Direct2D olayları yerine yalnızca temeli oluşturan Direct3D olayları kaydedildiğinden, Direct2D olayları Grafik Olay Listesi'nde görünmez. Ayrıca, Direct2D olayları ve sonuç Direct3D olayları arasındaki ilişki her zaman net olmadığından, Direct2D kullanan uygulamalarda işleme sorunları hatalarını ayıklamak için Grafik Tanılama kullanılması her zaman basit değildir. Yine de, Direct2D kullanan uygulamalarda düşük düzeyli işleme sorunları hakkında bilgi almak için Grafik Tanılama'yı kullanabilirsiniz.

## <a name="graphics-diagnostics-features-in-visual-studio"></a>Visual Studio Grafik Tanılama Özellikler
 Grafik Tanılama, işleme sorunlarını tanılamak için özel bir arabirime sahiptir-grafik çözümleyicisi penceresi, ancak aynı zamanda Visual Studio arabirimine bazı araçlar ekler.

### <a name="the-graphics-toolbar-visual-studio"></a>Grafik araç çubuğu (Visual Studio)
 Grafik araç çubuğu Grafik Tanılama komutlara hızlı erişim sağlar.

 **Tanılamayı Başlat** düğmesi grafik tanılama altında uygulamayı çalıştırır. Grafik Tanılama altında bir uygulama çalıştığında, **sonraki işlenen çerçeveyi yakala** düğmesi etkinleştirilir.

### <a name="diagnostics-capture-interface"></a>Tanılama yakalama arabirimi
 uygulamanızı Grafik Tanılama altında çalıştırdığınızda, Visual Studio çerçeveleri yakalamak için kullanabileceğiniz ve ayrıca geçerli CPU ve GPU yükünü görüntüleyen bir tanılama oturumu arabirimini görüntüler. CPU ve GPU yükü, hataları işlemek yerine, performans özellikleri nedeniyle yakalamak isteyebileceğiniz çerçeveleri belirlemenize yardımcı olacak şekilde görüntülenir.

 Bu, ancak çerçeveleri yakalamaya yönelik tek yoldur. Ayrıca, Programlı yakalama arabirimini kullanarak veya dxcap.exe komut satırı yakalama programını kullanarak çerçeveler yakalayabilirsiniz.

 Daha fazla bilgi için bkz. [grafik bilgilerini yakalama](capturing-graphics-information.md) .

### <a name="gpu-usage"></a>GPU Kullanımı
 Grafik Tanılama Ayrıca Direct3D uygulamanızın performansını da düzenleyebilir. Profil oluşturma verileri grafik olaylarının ayrıntıları kaydederek çarpılacağından, bu, grafik Çözümleyicisi ile incelenerek kullanılacak çerçeveleri yakalamaktan farklıdır.

 Daha fazla bilgi için bkz. [GPU kullanımı](../../profiling/gpu-usage.md) .

### <a name="directx-control-panel"></a>DirectX denetim masası
 DirectX denetim masası, DirectX'in davranış şeklini değiştirmek için kullanabileceğiniz bir DirectX bileşenidir; örneğin, DirectX çalışma zamanı bileşenlerinin hata ayıklama sürümünü etkinleştirebilir, raporlanan hata ayıklama iletilerinin türünü seçebilir ve daha düşük kapasiteli donanımlara öykünmek için belirli grafik donanımı yeteneklerinin kullanılmasına izin vermeyebilirsiniz. DirectX üzerinde bu düzeyde bir denetim DirectX uygulamanızda hata ayıklamanıza ve uygulamayı test etmenize yardımcı olabilir. DirectX denetim masasına Visual Studio'dan erişebilirsiniz.

#### <a name="to-open-the-directx-control-panel"></a>DirectX denetim masasını açmak için

- Menü çubuğunda **Hata Ayıkla**, **grafikler**, **DirectX Denetim Masası**' nı seçin.

## <a name="graphics-analyzer"></a>Grafik Çözümleyicisi
 Visual Studio grafik çözümleyicisi, zaten yakaladığınız çerçevelerdeki işleme ve performans sorunlarını incelemek için ayrılmış bir arabirimdir. Grafik Çözümleyicisi 'nin içinde uygulamanızın işleme davranışını keşfetmenize ve anlamanıza yardımcı olacak çeşitli araçlar bulacaksınız. Her araç, incelenmekte olan çerçeve hakkında farklı türde bir bilgi sunar ve araçlar, bir işleme sorununun kaynağı üzerinde, framebuffer 'ın görünümüyle başlayarak bir işleme sorunu durumunda kullanılmak üzere tasarlanmıştır.

 Bu çizimde, grafik Çözümleyicisi 'ndeki araçların tipik bir düzeni gösterilmektedir.

 ![Tüm grafik hata ayıklayıcısı pencereleri](media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")

### <a name="the-graphics-toolbar-graphics-analyzer"></a>Grafik araç çubuğu (grafik Çözümleyicisi)
 Grafik araç çubuğu, grafik Çözümleyicisi araç pencereleri için hızlı erişim sağlar.

 ![Grafik tanılama modundaki grafik araç çubuğu](media/vsg_toolbar.png "vsg_toolbar")

### <a name="graphics-log-document"></a>Grafik günlük belgesi
 Grafik Çözümleyicisi 'nin içinde grafik günlük belgesi en belirgin araç penceresidir. Bu pencere, Grafik Tanılama altında uygulamanızı çalıştırarak yakaladığınız tüm kareleri temsil eder. Buradan, piksel geçmişi aracıyla incelemek istediğiniz belirli bir pikseli incelemek veya seçmek için farklı bir çerçeve seçebilirsiniz. Bu belgede görüntülenen framebuffer görüntüsü, framebuffer 'ın zaman içinde nasıl etkilendiğini görebilmeniz için, şu anda seçili olan olayı yansıtacak şekilde değişir.

 [Grafik günlük belgesi](graphics-log-document.md) Ayrıca, oluşturma işlemi belirli yönlerinin yapılandırılıp orijinal ile karşılaştırılacağı kıyaslama sonuçları değiştirilerek bir çerçevenin performansını anlamanıza yardımcı olan Çerçeve Analizi aracına giriş noktasıdır.

### <a name="event-list"></a>Olay listesi
 Grafik olayları her Direct3D API çağrısını ve Kullanıcı tanımlı olayları işaretler.

 [Olay listesi](graphics-event-list.md) , incelediğiniz çerçeve sırasında kaydedilen tüm grafik olaylarını gösterir. Ne önemli olduğunu bulmanıza yardımcı olmak için olay listesi, sonraki çizim çağrısının altındaki son durum değişiklikleri ile ya da bir zaman çizelgesi olarak hiyerarşik olarak görüntülenebilir. Ayrıca, olaylar ait oldukları sıraya göre renk kodludur ve yalnızca ilgilendiğiniz olayları içerecek şekilde listeye filtre uygulayabilirsiniz.

 Listede bir olay seçtiğinizde, grafik çözümleme araçlarının geri kalanı bu olay sırasında çerçevenin durumunu yansıtır. Bu şekilde, herhangi bir etkinliğin GPU üzerinde etkisini görebilirsiniz. Örneğin, sonraki çizim çağrıları tarafından gizlense bile, framebuffer üzerinde herhangi bir çizim çağrısının hemen etkisini görebilirsiniz. Ayrıca, bazı olaylarda, parametreleri veya ilgili kaynak nesneleri hakkında daha fazla ayrıntı görmek için izleyebileceğiniz köprüler de vardır.

### <a name="pipeline-stages"></a>Ardışık düzen aşamaları
 Uygulamanızdaki her çizim çağrısı, Direct3D tarafından sunulan grafik işlem hattı üzerinden geçer. İşlem hattının her aşamasında, önceki aşamadaki çıkış, gölgelendirici olarak adlandırılan küçük bir program tarafından dönüştürülür ve son olarak ekrana işlenene kadar sonraki aşamaya geçirilir. Çıkış biçimi bir sonraki aşamanın beklediği tarihten farklı olduğunda veya herhangi bir aşama hatalı sonuçlar ürettiğinden, çok sayıda işleme hatası ardışık düzen aşamaları arasındaki sınırda oluşur. Normalde, ekranınızda gördüğünüz gibi yalnızca nihai sonuçları elde edersiniz ve hata hattının nerede oluştuğunu kolayca anlayabilirsiniz.

 [Ardışık düzen aşamaları](graphics-pipeline-stages.md) penceresi, her aşamanın sonucunu bağımsız olarak görselleştirir, böylece bir işleme sorununun ilk olarak hangi aşamada göründüğünü daha kolay bir şekilde belirleyebilmenizi sağlayabilirsiniz. Hangi aşamayı olduğunu belirledikten sonra, ardışık düzen aşamaları penceresinden gölgelendiricisinin hata ayıklamasını başlatabilirsiniz.

### <a name="graphics-state"></a>Grafik Durumu
 İşleme işlemleri, genellikle birden çok nesne arasında yayılan büyük bir duruma bağlıdır. Birçok tür işleme sorunu, yanlış yapılandırılmış durum nedeniyle oluşur.

 [Durum](graphics-state.md) penceresi, her çizim çağrısıyla ilgili durum bilgilerini tek bir yerde toplayıp daha kolay bulunur ve ayrıca önceki çizim çağrısından bu yana gerçekleşen durum değişikliklerinin vurgulanmasını sağlar.

### <a name="pixel-history"></a>Piksel geçmişi
 Karmaşık sahneler içinde, bir pikselin tek bir karede birden çok kez gölgelendirilme yaygın olmayan bir durumdur. Bazen önceki rengin üzerine yazılır, ancak saydamlık gibi etkilere ulaşmak için renkler birlikte birleştirilir. Bunları birlikte birleştirmenin sonucu doğru görünüme sahip olmadığında, renklerin yanlış olduğunu veya birleştirilme yöntemiyle ilgili bir sorun olup olmadığını kolayca anlayabilirsiniz. Başka bir deyişle, pikselin katkısı bazı nedenlerle reddedildiği için bir nesne eksik görünebilir.

 [Piksel geçmişi](graphics-pixel-history.md) penceresi, kabul edilecek katılımlar dahil olmak üzere, çerçevedeki her pikselin tam gölgelendirici geçmişini görselleştirir. Reddedilmeyen katkılar için, ham gölgelendirici sonuçlarını ve her yeni rengin öncekiyle birlikte nasıl birleştirildiğini görüntüler. Bu bilgilerle, hata kaynağını, gölgelendirici sonuçlarının karışdığı piksellerde veya bir işlenen nesne eksik olduğunda bulmak çok daha kolaydır çünkü pikselin katkısı yanlış bir şekilde reddediliyordu.

### <a name="event-call-stack"></a>Olay çağrısı yığını
 Gölgelendirici kodu, bir Direct3D uygulamasındaki işleme sorunlarının tek kaynağı değildir, bazen uygulamanızın kaynak kodu yanlış parametreyi geçirir ya da Direct3D 'yi doğrudan yapılandırmaz. Daha önce tartışılan özelliğin, piksel geçmişinin, tüm pikselleri reddedildiği için bir işlenen nesne eksik olduğu durumlarda, daha önce ele alınan bir hata türü. Bu tür bir hata, genellikle derinlik testinin nasıl gerçekleştirileceğini denetleyen bir ayarı yanlış yapılandırdığınızda oluşur ve genellikle yanlışlıkla hatalı nesnenin çizim çağrısının çağrı yığınında bir yerde bulunabilir.

 [Olay çağrı yığını](graphics-event-call-stack.md) penceresi, olay listesindeki her grafik olayının tüm çağrı yığınını görüntüler, hatta hata ayıklama bilgisi varsa uygulamanızın kaynak koduna atlamanızı sağlar. Bu, GPU 'da, uygulamanın kaynak kodunda kaynaklandığı yere geri doğru bir hata takip etmek için güçlü bir araçtır.

### <a name="object-table"></a>Nesne tablosu
 Uygulama işlemesi yapılan her çerçeve büyük olasılıkla yüzlerce, hatta binlerce kaynak nesnesi tarafından de desteklene sahiptir. Bunlar geri arabellekleri ve işleme hedeflerini, dokuları, köşe arabelleklerini, dizin arabelleklerini, genel arabellekleri içerebilir. Direct3D'nin hatırlayacağı neredeyse her şey bir nesnedir.

 Nesne [Tablosu,](graphics-object-table.md) olay listesinde seçilen grafik olayı sırasında mevcut olan tüm nesneleri görüntüler. Tipik bir uygulamadaki nesnelerin çoğu doku olduğundan, olay listesi görüntülerle ilgili ayrıntıları bir bakışta göstermek için en iyi duruma getirilmiştir. Tür sütunu size her satırda ne tür bir nesne olduğunu söyler ve Biçim sütunu daha sonra nesnenin alt türünü veya sürümünü gösterir. Diğer ayrıntılar da gösterilir. Bazı nesneler, dokular (dokuyu görüntü olarak görüntüleyebilirsiniz) veya arabellekler (arabellek biçimini tanımlayarak arabellek görüntüleyicinin ham arabellek baytlarını ayrıştırma ve görüntüleme biçimini seçebilirsiniz) gibi daha özel bir görüntüleyiciye sahip nesneyi görüntülemek için izleyebilirsiniz köprülere de sahiptir.

### <a name="frame-analysis"></a>Çerçeve analizi
 Uygulama grafiğinizin yalnızca doğru olması değil hızlı olması da gerekir. Tümleşik grafiklere veya cep telefonlarına sahip dizüstü bilgisayarlar gibi daha az güçlü cihazlarda bile. Ayrıca yine de harika bir görünüme sahip olmak zorundalar.

 Çerçeve [Analizi aracı,](graphics-frame-analysis.md) uygulamanın Direct3D kullanma yolunu otomatik olarak değiştirerek ve karşılaştırma için karşılaştırma sonuçları sağlayarak olası performans iyileştirmelerini keşfeder. Örneğin, Çerçeve Analizi her dokuda mip eşlemeyi etkinleştirip mip eşlemeden yararlanabilecek dokuları ortaya çıkarabilecek ancak şu anda etkinleştirilmemiş olabilir. Çerçeve Analizi, bunu destekleyen donanımlarda GPU'nun performans sayaçlarından toplanan bilgileri de sunar; bu bilgi düzeyi, çok sayıda doku getirme durakları veya önbellek isabet isabeti gibi donanım düzeyinde performans sorunlarını tanımlayabilir.

 Ancak Çerçeve Analizi yalnızca hızlı olmakla ilgili değil, en az miktarda görsel kalitesini bırakarak en yüksek performansı elde etmektir. Bazen büyük ekranda harika görünen pahalı bir etki, bir telefonun küçük ekranında görüntüleniyorsa aynı etkiye neden olmaz ve pil boşaltmadan daha basit bir etki de aynı şekilde iyi görünür. Grafik Analizi'nin sağladığı otomatik değişiklikler ve karşılaştırmalar, çeşitli cihazlarda uygulamanıza uygun bakiyeyi bulamanıza yardımcı olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Komut Satırı Yakalama Aracı](command-line-capture-tool.md)
- [HLSL Hata Ayıklayıcısı](hlsl-shader-debugger.md)
