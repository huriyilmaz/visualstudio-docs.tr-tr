---
title: IntelliTrace kullanarak önceki uygulama durumunu görüntüleme
description: IntelliTrace geri adımını kullanarak anlık görüntü alma ve anlık görüntüleri görüntüleme hakkında bilgi alın
ms.custom: seodec18
ms.date: 09/19/2018
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0cb43e75f626f82a0b47bb76bc8be64615ccc333e40e3f22c94e90ff223e239d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121418953"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio-visual-studio-enterprise"></a>IntelliTrace geri adımını kullanarak önceki uygulama durumları Visual Studio (Visual Studio Enterprise)

IntelliTrace geri adımı, her kesme noktası ve hata ayıklayıcı adımı olayında otomatik olarak uygulamanın anlık görüntüsünü alır. Kaydedilen anlık görüntüler, önceki kesme noktalarına veya adımlara geri dönmenizin yanı sıra uygulamanın geçmişte olduğu gibi durumunu görüntülemeye olanak sağlar. IntelliTrace geri adımı önceki uygulama durumunu görmek istediğiniz ancak hata ayıklamayı yeniden başlatmak veya istenen uygulama durumunu yeniden oluşturmak istemeyebilirsiniz.

IntelliTrace geri adım geri Visual Studio Enterprise 2017 sürüm 15.5 ve üzeri sürümlerde kullanılabilir ve Yıldönümü Güncelleştirmesi Windows 10 gerektirir. Bu özellik şu anda ASP.NET, WinForms, WPF, yönetilen konsol uygulamaları ve yönetilen sınıf kitaplıklarında hata ayıklama için de destekleniyor. 2017 Visual Studio 15.7 Enterprise sürümünden itibaren, bu özellik ASP.NET Core ve .NET Core için de de desteklene sahiptir. 2017 Visual Studio sürüm 15.9 Önizleme 2'den başlayarak, bu özellik 201 Enterprise 7'yi Windows. UWP uygulamalarında hata ayıklama şu anda desteklenmiyor.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * IntelliTrace olaylarını ve anlık görüntülerini etkinleştirme
> * Geri adım ve ileri adım komutlarını kullanarak olaylara gidin
> * Olay anlık görüntülerini görüntüleme

## <a name="enable-intellitrace-events-and-snapshots-mode"></a>IntelliTrace olayları ve anlık görüntü modunu etkinleştirme

1. Projenizi Visual Studio Enterprise.

1. Araçlar **Seçenekleri**  >    >  **IntelliTrace ayarlarını** açın ve **IntelliTrace** olayları ve anlık görüntüleri seçeneğini belirleyin.

    2017 Visual Studio 15.9 Önizleme 2 Enterprise sürümünden itibaren bu seçenek **IntelliTrace anlık görüntüleridir (yönetilen** ve yerel).

    ![IntelliTrace Olayları ve Anlık Görüntüler modunu etkinleştirme](../debugger/media/intellitrace-enable-snapshots.png "IntelliTrace olaylarını ve anlık görüntü modunu etkinleştir")

1. Özel durumlarda anlık görüntüleri görüntüleme seçeneklerini yapılandırmak için Seçenekler iletişim kutusunda **IntelliTrace**  >  **Gelişmiş'i** seçin.

    Bu seçenekler 2017 Visual Studio 15.7 Enterprise kullanılabilir.

    ![Özel durumlarda anlık görüntüler için davranışı yapılandırma](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Olayları ve anlık görüntüleri etkinleştirdikten sonra özel durumlara anlık görüntü almak da varsayılan olarak etkindir. Özel durum olaylarda anlık görüntüler topla'nın seçimini **kaldırarak özel durumlarda anlık görüntüleri devre dışı layabilirsiniz.** Bu özellik etkinleştirildiğinde, işlanmamış özel durumlar için anlık görüntüler alınır. Ele alınan özel durumlar için anlık görüntüler yalnızca özel durum sızıyorsa ve daha önce atılan bir özel durumun yeniden oluşturması yoksa alınır. Açılan listeden bir değer seçerek özel durumlarda en fazla anlık görüntü sayısını seçebilirsiniz. Maksimum değer, uygulamanın kesme moduna girdiği her zaman (örneğin, uygulama bir kesme noktası olduğunda) için geçerlidir.

    > [!NOTE]
    > Anlık görüntüler yalnızca IntelliTrace tarafından kaydedilen özel durum olayları için alınır. Yönetilen kod için, Araçlar Seçenekleri IntelliTrace Olayları'ı seçerek   >    >  **IntelliTrace kayıtlarını hangi olayları belirtebilirsiniz.**

1. Projenize bir veya daha fazla kesme noktası ayarlayın ve hata ayıklamaya başlayabilir **(F5** tuşuna basın) veya kodunuz (**F10** veya **F11)** adım hata ayıklamaya başlayabilirsiniz.

    IntelliTrace her hata ayıklayıcı adım, kesme noktası olayı ve işlanmamış özel durum olayında uygulama işleminin anlık görüntüsünü alır. Bu olaylar, diğer  IntelliTrace **olaylarıyla** Tanılama Araçları penceresindeki Olaylar sekmesine kaydedilir. Bu pencereyi açmak için Hata **ayıkla'Windows**  >    >  **Show Tanılama Araçları**.

    Anlık görüntülerin kullanılabilir olduğu olayların yanında kamera simgesi görünür.

    ![Anlık görüntülerin yer alan Olaylar sekmesi](../debugger/media/intellitrace-events-tab-with-snapshots.png "Kesme noktaları ve adımlarda anlık görüntülerle olaylar sekmesi")

    Performans nedenleriyle, çok hızlı bir şekilde adım atarak anlık görüntüler alınmaz. Adımın yanında kamera simgesi yoksa daha yavaş adımlamayı deneyin.

## <a name="navigate-and-view-snapshots"></a>Anlık görüntülerde gezinme ve görüntüleme

1. Hata Ayıklama araç çubuğundaki Geri Adım **(Alt + [)** ve İleri Adım **(Alt + ])** düğmelerini kullanarak olaylar arasında gezinebilirsiniz.

    Bu düğmeler, uygulama penceresinin **Olaylar sekmesinde** görünen Tanılama Araçları **gezinebilirsiniz.** Bir olayda geri veya ileri adımlama, seçili [olayda geçmiş hata ayıklamayı](../debugger/historical-debugging.md) otomatik olarak etkinleştirir.

    ![Geri ve İleri Adım düğmeleri](../debugger/media/intellitrace-step-back-icons-description.png "Geri adımla ve adım Ileri düğmeleri")

    Geri adım atarak veya ileri doğru ilerlerken Visual Studio hata ayıklama moduna girer. Bu modda, hata ayıklayıcının bağlamı seçilen olayın kaydedi olduğu zamanlara geçer. Visual Studio, işaretçiyi kaynak penceresinde karşılık gelen kod satırına da taşır.

    Bu görünümden Çağrı Yığını, Yereller, Otomatikler ve İzleme **pencerelerinde** değerleri **inceebilirsiniz.**  Ayrıca Değişkenlerin üzerine gelerek DataTips'i görüntüleyebilirsiniz ve Hemen penceresinde ifade değerlendirmesi **gerçekleştirebilirsiniz.** Gördüğünüz veriler, uygulama işleminin o anda alınan anlık görüntüsünden alınır.

    Örneğin, bir kesme noktası isabet ettiy ve Bir Adım (**F10)** aldıysanız, Geri Adım düğmesi Visual Studio kesme noktasıyla ilgili kod satırına geçmiş moduna koyar. 

    ![Anlık görüntü ile bir olayda geçmiş modunu etkinleştirme](../debugger/media/intellitrace-historical-mode-with-snapshot.png "Anlık görüntü ile bir olayda geçmiş modunu etkinleştirme")

2. Canlı yürütmeye geri dönmek için Devam **(F5)** öğesini seçin veya bilgi çubuğuna Canlı Hata Ayıklamaya Geri Dön bağlantısına tıklayın. 

3. Bir anlık görüntüyü Olaylar sekmesinden de **görüntüleyebilirsiniz.** Bunu yapmak için anlık görüntüyle bir olay seçin ve Geçmiş Hata Ayıklamayı **Etkinleştir'e tıklayın.**

    ![Bir olayda Geçmiş Hata Ayıklamayı etkinleştirme](../debugger/media/intellitrace-activate-historical-debugging.png "Bir olayda geçmiş hata ayıklamayı etkinleştirin")

    Sonraki Deyimi **Ayarla komutunun** aksine, anlık görüntüyü görüntülemek kodunuzu yeniden çalıştırmaz; Uygulamanın geçmişteki bir noktadaki durumunun statik bir görünümünü sağlar.

    ![IntelliTrace geri adıma genel bakış](../debugger/media/intellitrace-step-back-overview.png "IntelliTrace adım geri 'ye Genel Bakış")

    Uygulama içinde değişkenleri inceleme hakkında daha fazla bilgi Visual Studio [bkz. Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)

## <a name="frequently-asked-questions"></a>Sık Sorulan Sorular

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>IntelliTrace geri adımını yalnızca IntelliTrace olayları modundan nasıl farklı?

Yalnızca olaylar modunda IntelliTrace, hata ayıklayıcı adımlarında ve kesme noktalarında geçmiş hata ayıklamayı etkinleştirmenizi sağlar. Ancak IntelliTrace yalnızca Windows açıksa **Yereller** ve Otomatikler pencerelerinde verileri yakalar ve yalnızca genişletilmiş ve görünümde olan verileri yakalar.  Yalnızca olaylar modunda, genellikle değişkenlerin ve karmaşık nesnelerin tam bir görünümünüz olmaz. Ayrıca, ifade değerlendirme ve İzleme **penceresindeki** verileri görüntüleme desteklenmiyor.

Olaylar ve anlık görüntüler modunda IntelliTrace, karmaşık nesneler de dahil olmak üzere uygulama işleminin tüm anlık görüntüsünü yakalar. Bir kod satırda, bir kesme noktası durdurulmuş gibi aynı bilgileri görebilir (ve bilgileri daha önce genişletip genişlet olmadığı önemli değildir). Bir anlık görüntü görüntüde ifade değerlendirmesi de de desteklenmeli.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Bu özelliğin performans etkisi nedir? 

Genel adımlama performansı üzerindeki etki, uygulamanıza bağlıdır. Anlık görüntü alma yükü 30 ms kadardır. Anlık görüntü alınca uygulamanın işlemi askıya alınır ve bu kopya askıya alınır. Bir anlık görüntüyü görüntü Visual Studio kopyanın kopyaya ekli olduğunu varsayabilirsiniz. Her anlık görüntü Visual Studio tabloyu kopyalar ve sayfaları yazmada kopyalanır olarak ayarlar. Yığındaki nesneler ilişkili anlık görüntülerle hata ayıklayıcı adımları arasında değişirse, ilgili sayfa tablosu kopyalanır ve bu da minimum bellek maliyetine neden olur. Bu Visual Studio anlık görüntü almak için yeterli bellek olmadığını algılarsa, bir bellek almaz.

## <a name="known-issues"></a>Bilinen Sorunlar
* IntelliTrace olayları ve anlık görüntüler modunu Windows 10 Fall Creators Update'den (RS3) daha eski Windows sürümlerinde kullanıyorsanız ve uygulamanın hata ayıklama platformu hedefi x86 olarak ayarlanırsa IntelliTrace anlık görüntü almaz.

    Geçici çözümler:
  * Windows 10 Yıldönümü Güncelleştirmesi (RS1) ve 10.0.14393.2273 sürümünün altındaysanız [KB4103720 'yi yükleyin.](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720)
  * Windows 10 Creators Update (RS2) ve 10.0.15063.1112 sürümünün altındaysanız [KB4103722 yükleyin.](https://support.microsoft.com/help/4103722/windows-10-update-4103722)
  * Windows 10 Fall Creators Update (RS3) yükleyin veya yükseltin.
  * Alternatif olarak:
    1. Visual Studio yükleyicisinden masaüstü için VC++ 2015.3 v140 araç seti (x86, x64) bileşenini yükleyin.
    2. Hedef uygulamayı derleyin.
    3. Komut satırına editbin aracını kullanarak hedef yürütülebilir `Largeaddressaware` dosyanın bayrağını ayarlayın. Örneğin, şu komutu kullanabilirsiniz (yolu güncelleştirdikten sonra): "C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application\app.exe".
    4. Hata ayıklamayı başlatmak için **F5 tuşuna basın.** Artık, hata ayıklayıcı adımlarını ve kesme noktalarında anlık görüntüler alınır.

       > [!Note]
       > `Largeaddressaware`Yürütülebilir dosya her değişiklikle yeniden çalıştırılabilirse bayrağı ayar gerekir.

* Kalıcı bellek eşlenmiş bir dosya kullanan bir uygulamada uygulama işleminin anlık görüntüsü alınırsa, anlık görüntüye sahip işlem, bellekle eşlenen dosyada (üst işlem kilidi serbest bıraksa bile) özel bir kilit tutar. Diğer işlemler yine de belleğe eşlenmiş dosyaya okuyabilir, ancak yazamıyor.

  Geçici çözüm:
  * Hata ayıklama oturumunu sonlandırarak tüm anlık görüntülerin temizlerini alın.

* Çok sayıda DLL yüke sahip bir uygulama gibi çok sayıda benzersiz bellek bölgesi olan bir uygulamada hata ayıklaması sırasında, anlık görüntülerin etkinleştirildiğinde adımlama performansı etkilenebilir. Bu sorun, gelecekteki bir sürümde ele Windows. Bu sorunla karşılaşıyorsanız, ile bize stepback@microsoft.com ulaşabilirsiniz.

* IntelliTrace > ile bir dosyayı **> IntelliTrace** oturumunu olaylar ve anlık görüntüler modunda kaydedin. Anlık görüntülerden yakalanan ek veriler .itrace dosyasında kullanılamaz. Kesme noktası ve adım olaylarında, dosyayı yalnızca IntelliTrace olayları moduna kaydedilmiş gibi aynı bilgileri görüyorsunuz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, IntelliTrace geri adımını kullanmayı öğrendiniz. Diğer IntelliTrace özellikleri hakkında daha fazla bilgi edinmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [IntelliTrace özellikleri](../debugger/intellitrace-features.md)
