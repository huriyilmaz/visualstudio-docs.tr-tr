---
title: IntelliTrace'i kullanarak önceki uygulama durumunu görüntüleme
description: Anlık görüntüleri nasıl çekeceğinizi öğrenin ve IntelliTrace adım geri siyle anlık görüntüleri görüntüleme
ms.custom: seodec18
ms.date: 09/19/2018
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83d444cb5e3345d79ca6e1422982c0ecd37e4287
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "67825523"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio-visual-studio-enterprise"></a>Visual Studio'da (Visual Studio Enterprise) IntelliTrace adım geri adım kullanarak önceki uygulama durumlarını inceleyin

IntelliTrace adım geri otomatik olarak her kesme noktası ve hata ayıklama adım olay uygulamanızın bir anlık alır. Kaydedilen anlık görüntüler, önceki kesme noktalarına veya adımlara geri dönmenizi ve uygulamanın durumunu geçmişte olduğu gibi görüntülemenizi sağlar. IntelliTrace adım geri önceki uygulama durumunu görmek istediğinizde zaman kazandırabilir, ancak hata ayıklama yeniden başlatmak veya istenen uygulama durumunu yeniden oluşturmak istemiyorum.

IntelliTrace adım geri Visual Studio Enterprise 2017 sürümü 15.5 ve üzeri başlayan kullanılabilir ve Windows 10 Anniversary Update veya üzeri gerektirir. Özellik şu anda hata ayıklama ASP.NET, WinForms, WPF, yönetilen konsol uygulamaları ve yönetilen sınıf kitaplıkları için desteklenir. Visual Studio 2017 Enterprise sürüm 15.7 ile başlayan özellik, ASP.NET Core ve .NET Core için de desteklenir. Visual Studio 2017 Enterprise sürüm 15.9 Preview 2 ile başlayan özellik, Windows'u hedefleyen yerel uygulamalar için de desteklenir. Hata ayıklama UWP uygulamaları şu anda desteklenmiyor.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * IntelliTrace olaylarını ve anlık görüntülerini etkinleştirin
> * Adım adım ve adım adım komutlarını kullanarak olaylarda gezinme
> * Olay anlık görüntülerini görüntüleme

## <a name="enable-intellitrace-events-and-snapshots-mode"></a>IntelliTrace olayları ve anlık görüntü modunu etkinleştirme

1. Visual Studio Enterprise'da projenizi açın.

1. **Araç** > **Seçenekleri** > **IntelliTrace** ayarlarını açın ve **IntelliTrace etkinlikleri ni ve anlık görüntüleri**seçeneğini seçin.

    Visual Studio 2017 Enterprise sürüm 15.9 Preview 2'den başlayarak bu seçenek **IntelliTrace anlık görüntüleridir (yönetilen ve yerel)**.

    ![IntelliTrace Olayları ve Anlık Görüntü modunu etkinleştirin](../debugger/media/intellitrace-enable-snapshots.png "IntelliTrace Olayları ve Anlık Görüntü modunu etkinleştirin")

1. Anlık görüntüleri özel durumlara göre görüntülemek için seçenekleri yapılandırmak istiyorsanız, **Seçenekler** iletişim**kutusundan** **Gelişmiş IntelliTrace'i** > seçin.

    Bu seçenekler Visual Studio 2017 Enterprise sürüm 15.7'den başlayarak mevcuttur.

    ![Özel durumlardaki anlık görüntüler için davranışı yapılandırma](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Olayları ve anlık görüntüleri etkinleştirdiğinizde, özel durumlar üzerinde anlık görüntü almak da varsayılan olarak etkinleştirilir. Özel durumlar için **anlık görüntü toplama'yı**seçerek anlık görüntüleri özel durumlar üzerinde devre dışı atabilirsiniz. Bu özellik etkinleştirildiğinde, işlenmemiş özel durumlar için anlık görüntüler alınır. İşlenen özel durumlar için anlık görüntüler yalnızca özel durum atılırsa ve daha önce atılmış bir özel durum yeniden atılmazsa alınır. Açılan listeden bir değer seçerek, özel durumlar alabilen en fazla anlık görüntü sayısını ayarlayabilirsiniz. Uygulamanızın kesme moduna her girdiği her zaman (örneğin, uygulamanız bir kesme noktasına ulaştığında) maksimum geçerlidir.

    > [!NOTE]
    > Anlık görüntüler yalnızca IntelliTrace'in kaydettiği özel durumlar için alınır. Yönetilen kod için, **Araçlar** > **Seçenekleri** > **IntelliTrace Olaylar**seçerek intelliTrace kayıtları hangi olayları belirtebilirsiniz.

1. Projenizde, bir veya daha fazla kesme noktası ayarlayın ve hata ayıklamaya başlayın **(F5**tuşuna basın), veya kodunuzu **(F10** veya **F11)** atarak hata ayıklamaya başlayın).

    IntelliTrace, her hata ayıklama adımında, kesme noktası olayında ve işlenmemiş özel durum olayında uygulamanın işleminin anlık görüntüsünü alır. Bu olaylar, diğer IntelliTrace olaylarıile birlikte **Tanılama Araçları** penceresindeki **Olaylar** sekmesine kaydedilir. Bu pencereyi açmak için **Hata Ayıklama** > **Windows** > **Show Tanılama Araçları'nı**seçin.

    Anlık görüntünün kullanılabildiği olayların yanında bir kamera simgesi görünür.

    ![Anlık görüntülerle olaylar sekmesi](../debugger/media/intellitrace-events-tab-with-snapshots.png "Kesme noktaları ve adımlardaki anlık görüntülerle olaylar sekmesi")

    Performans nedenleriyle, çok hızlı adım attığınızda anlık görüntüler alınmaz. Adımın yanında kamera simgesi görünmüyorsa, daha yavaş basmayı deneyin.

## <a name="navigate-and-view-snapshots"></a>Anlık görüntüde gezinme ve görüntüleme

1. Hata Ayıklama araç çubuğundaki **Geri Adım (Alt + [)** ve **İleri Adım (Alt + ])** düğmelerini kullanarak olaylar arasında gezinin.

    Bu **düğmeler, Tanılama Araçları penceresindeki** **Olaylar** sekmesinde görünen olaylarda gezinir. Bir olaya geri veya ileri adım atmak, seçili olaydaki [geçmiş hata ayıklamayı](../debugger/historical-debugging.md) otomatik olarak etkinleştirir.

    ![İleri adım ve İleri düğmeleri](../debugger/media/intellitrace-step-back-icons-description.png "Geri Adım ve İleri Adım düğmeleri")

    Geri adım attığınızda veya adım attığınızda, Visual Studio geçmiş hata ayıklama moduna girer. Bu modda, hata ayıklamanın bağlamı, seçili olayın kaydedildiği zamana geçer. Visual Studio ayrıca işaretçiyi kaynak penceredeki ilgili kod satırına taşır.

    Bu görünümden, **Arama Yığını,** **Yereller,** **Otomatikler**ve **Windows'u İzle'deki** değerleri inceleyebilirsiniz. DataTips'i görüntülemek ve **Hemen** penceresinde ifade değerlendirmesi gerçekleştirmek için değişkenlerin üzerine de bakabilirsiniz. Gördüğünüz veriler, uygulamanın o anda aldığı işlemin anlık görüntüsünden elde edilir.

    Örneğin, bir kesme noktasına ulaştıysanız ve bir Adım **(F10)** aldıysanız, **Step Backward** düğmesi Visual Studio'yu kesme noktasına karşılık gelen kod satırında geçmiş modda yer alar.

    ![Anlık görüntüyle bir etkinlikte geçmiş modu etkinleştirme](../debugger/media/intellitrace-historical-mode-with-snapshot.png "Anlık görüntüyle bir etkinlikte geçmiş modu etkinleştirme")

2. Yürütmeyi yaşamak için Devam **et (F5)** seçeneğini belirleyin veya bilgi çubuğundaki **Canlı Hata Ayıklama'ya Geri Dön** bağlantısını tıklatın.

3. **Etkinlikler** sekmesinden anlık görüntü de görüntüleyebilirsiniz. Bunu yapmak için anlık görüntü içeren bir olay seçin ve **Geçmiş Hata Ayıklama'yı etkinleştir'i**tıklatın.

    ![Bir etkinlikte Geçmiş Hata Ayıklama'yı etkinleştirme](../debugger/media/intellitrace-activate-historical-debugging.png "Bir etkinlikte Geçmiş Hata Ayıklama'yı etkinleştirme")

    Sonraki **Bildirimi Ayarla** komutundan farklı olarak, anlık görüntü görüntülemek kodunuzu yeniden çalışmaz; geçmişte meydana gelen bir noktada uygulamanın durumunun statik bir görünümünü verir.

    ![IntelliTrace adım geri genel bakış](../debugger/media/intellitrace-step-back-overview.png "IntelliTrace Adım Geri Genel Bakış")

    Visual Studio'da değişkenleri nasıl inceleyikarşıları hakkında daha fazla bilgi edinmek için hata [ayıklama bölümüne ilk bakışta](../debugger/debugger-feature-tour.md)

## <a name="frequently-asked-questions"></a>Sık Sorulan Sorular

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Nasıl IntelliTrace adım geri IntelliTrace olaylar sadece modu farklıdır?

IntelliTrace olaylarda yalnızca modu hata ayıklama adımları ve kesme noktalarında geçmiş hata ayıklama etkinleştirmek için izin verir. Ancak, IntelliTrace yalnızca windows açıksa **Yerel ler** ve **Otomatik ler** pencerelerinde veri yakalar ve yalnızca genişletilmiş ve görünümde olan verileri yakalar. Olaylar yalnızca modda, genellikle değişkenlerin ve karmaşık nesnelerin tam bir görünümü yoktur. Ayrıca, **İzleme** penceresinde ifade değerlendirme ve görüntüleme verileri desteklenmez.

Olaylar ve anlık görüntü modunda IntelliTrace, karmaşık nesneler de dahil olmak üzere uygulama sürecinin tüm anlık görüntüsünü yakalar. Bir kod satırında, aynı bilgileri bir kesme noktasında durdurulmuş gibi görebilirsiniz (ve bilgileri daha önce genişletip genişletmediğiniz önemli değildir). Anlık görüntü görüntülenirken ifade değerlendirmesi de desteklenir.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Bu özelliğin performans etkisi nedir? 

Genel adım performansı üzerindeki etkisi uygulamanıza bağlıdır. Anlık görüntü almanın yükü yaklaşık 30 ms'dir. Anlık görüntü alındığında, uygulamanın işlemi çatallanır ve çatallı kopya askıya alınır. Bir anlık görüntü görüntülediğinizde, Visual Studio işlemin çatallı kopyasına iliştiriyor. Her anlık görüntü için Visual Studio yalnızca sayfa tablosunu kopyalar ve sayfaları kopyalayıp yazmaya ayarlar. Yığındaki nesneler ilişkili anlık görüntülerle hata ayıklama adımları arasında değişirse, ilgili sayfa tablosu kopyalanır ve en az bellek maliyeti oluşur. Visual Studio anlık görüntü almak için yeterli bellek olmadığını algılarsa, bir tane almaz.

## <a name="known-issues"></a>Bilinen Sorunlar
* Windows 10 Fall Creators Update (RS3) daha eski Windows sürümlerinde IntelliTrace olayları ve anlık görüntü modunu kullanıyorsanız ve uygulamanın hata ayıklama platformu hedefi x86 olarak ayarlanmışsa, IntelliTrace anlık görüntü almaz.

    Geçici çözümler:
  * Windows 10 Yıldönümü Güncellemesi (RS1) ve sürüm 10.0.14393.2273'ün altındaysanız, [KB4103720'yi yükleyin.](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720)
  * Windows 10 Creators Update (RS2) ve sürüm 10.0.15063.1112 altında iseniz, [KB4103722 yükleyin.](https://support.microsoft.com/help/4103722/windows-10-update-4103722)
  * Windows 10 Fall Creators Update'e (RS3) yükleyin veya yükseltin.
  * Alternatif olarak:
    1. Visual Studio yükleyicisinden masaüstü için VC++ 2015.3 v140 araç seti (x86, x64) bileşenini yükleyin.
    2. Hedef uygulamayı derleyin.
    3. Komut satırından, yürütülebilir hedef için `Largeaddressaware` bayrağı ayarlamak için düzenleme kutusu aracını kullanın. Örneğin, bu komutu kullanabilirsiniz (yolu güncelledikten sonra): "C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application.exe".
    4. Hata ayıklamaya başlamak için **F5**tuşuna basın. Şimdi, anlık görüntü hata ayıklama adımları ve kesme noktalarında alınır.

       > [!Note]
       > Yürütülebilir `Largeaddressaware` değişikliklerle yeniden inşa edilen bayrak her zaman ayarlanmalıdır.

* Uygulamanın işleminin anlık görüntüsü, kalıcı bellek eşlenen dosyayı kullanan bir uygulamada alındığında, anlık görüntüyle birlikte bellek eşlenen dosyada özel bir kilit tutar (üst işlem kilitlerini serbest bıraktıktan sonra bile). Diğer işlemler, bellek eşlenen dosyaya hala okuyabilir, ancak yazamaz.

  Geçici çözüm:
  * Hata ayıklama oturumunu sonlayarak tüm anlık görüntüleri temizleyin.

* İşlemi çok sayıda DL's i yükleyen bir uygulama gibi çok sayıda benzersiz bellek bölgesine sahip olan bir uygulamanın hata ayıklanması ndan etkilenebilir. Bu sorun, Windows'un gelecekteki bir sürümünde ele alınacaktır. Bu sorunu yaşıyorsanız, bize stepback@microsoft.comulaşın.

* Hata **Ayıklama > IntelliTrace > IntelliTrace oturumunu** olaylar ve anlık görüntüler modu altında kaydederken, anlık görüntülerden yakalanan ek veriler .itrace dosyasında kullanılamaz. Kesme noktası ve adım olaylarında, dosyayı yalnızca IntelliTrace olayları modunda kaydetmiş gibi aynı bilgileri görürsünüz.

## <a name="next-steps"></a>Sonraki adımlar

Bu eğitimde, IntelliTrace adım geri nasıl kullanılacağını öğrendim. Diğer IntelliTrace özellikleri hakkında daha fazla bilgi edinmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [IntelliTrace özellikleri](../debugger/intellitrace-features.md)
