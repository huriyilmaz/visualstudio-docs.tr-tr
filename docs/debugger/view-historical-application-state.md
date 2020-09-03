---
title: IntelliTrace kullanarak önceki uygulama durumunu görüntüleme
description: Anlık görüntü alma ve IntelliTrace adım geri alma ile anlık görüntüleri görüntüleme hakkında bilgi edinin
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825523"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio-visual-studio-enterprise"></a>Visual Studio 'da IntelliTrace adım geri 'yi kullanarak önceki uygulama durumlarını İnceleme (Visual Studio Enterprise)

IntelliTrace adım geri alma, her kesme noktası ve hata ayıklayıcı adım olayında uygulamanızın bir anlık görüntüsünü otomatik olarak alır. Kaydedilen anlık görüntüler, önceki kesme noktalarına veya adımlara geri dönmenize ve uygulamanın geçmişte olduğu gibi durumunu görüntülemenize imkan tanır. IntelliTrace adım geri dönüş, önceki uygulama durumunu görmek istediğinizde, ancak hata ayıklamayı yeniden başlatmak veya istenen uygulama durumunu yeniden oluşturmak istemediğinizde size zaman kazandırabilir.

IntelliTrace adım geri 'yi Visual Studio Enterprise 2017 sürüm 15,5 ve üzeri sürümlerde ve Windows 10 yıldönümü güncelleştirmesi veya üstünü gerektirir. Özelliği şu anda ASP.NET, WinForms, WPF, yönetilen konsol uygulamaları ve yönetilen sınıf kitaplıklarında hata ayıklama için desteklenmektedir. Visual Studio 2017 Enterprise sürüm 15,7 ' den itibaren, özellik ASP.NET Core ve .NET Core için de desteklenir. Visual Studio 2017 Enterprise sürüm 15,9 Preview 2 ' den itibaren, özelliği Windows 'u hedefleyen yerel uygulamalar için de desteklenir. UWP uygulamalarında hata ayıklama Şu anda desteklenmiyor.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * IntelliTrace olaylarını ve anlık görüntülerini etkinleştir
> * Geri adım ve adım ileri komutlarını kullanarak olaylara gitme
> * Olay anlık görüntülerini görüntüle

## <a name="enable-intellitrace-events-and-snapshots-mode"></a>IntelliTrace olaylarını ve anlık görüntü modunu etkinleştir

1. Projenizi Visual Studio Enterprise açın.

1. **Araçlar**  >  **Seçenekler**  >  **IntelliTrace** ayarları ' nı açın ve **IntelliTrace olayları ve anlık görüntüleri**seçeneğini belirleyin.

    Visual Studio 2017 Enterprise sürüm 15,9 Preview 2 ' den başlayarak, bu seçenek **IntelliTrace anlık görüntüleridir (yönetilen ve yerel)**.

    ![IntelliTrace olaylarını ve anlık görüntü modunu etkinleştir](../debugger/media/intellitrace-enable-snapshots.png "IntelliTrace olaylarını ve anlık görüntü modunu etkinleştir")

1. Özel durumların anlık görüntülerini görüntüleme seçeneklerini yapılandırmak istiyorsanız, **IntelliTrace**  >  **Seçenekler** iletişim kutusundan IntelliTrace**Gelişmiş** ' i seçin.

    Bu seçenekler, Visual Studio 2017 Enterprise sürüm 15,7 ' den itibaren kullanılabilir.

    ![Özel durumlarda anlık görüntüler için davranışı yapılandırma](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Olayları ve anlık görüntüleri etkinleştirdiğinizde, özel durumlarla ilgili anlık görüntülerin alınması de varsayılan olarak etkindir. **Özel durum olaylarında anlık görüntü toplamayı**devre dışı bırakarak özel durumlarda anlık görüntüleri devre dışı bırakabilirsiniz. Bu özellik etkinleştirildiğinde, işlenmemiş özel durumlar için anlık görüntüler alınır. İşlenmiş özel durumlar için, anlık görüntüler yalnızca özel durum oluşturulursa ve daha önce oluşturulan bir özel durumun yeniden oluşturulması durumunda alınır. Özel durumlar üzerinde, açılan listeden bir değer seçerek en fazla sayıda anlık görüntü ayarlayabilirsiniz. En büyük değer, uygulamanız kesme moduna girdiğinde (örneğin, uygulamanız bir kesme noktasına rastlarsa) her seferinde geçerlidir.

    > [!NOTE]
    > Anlık görüntüler yalnızca IntelliTrace 'in kaydettiği özel durum olayları için alınır. Yönetilen kod için, **Araçlar**  >  **Seçenekler**  >  **IntelliTrace olayları**' nı seçerek hangi olayların IntelliTrace 'in kayıt yaptığını belirtebilirsiniz.

1. Projenizde bir veya daha fazla kesme noktası ayarlayın ve hata ayıklamayı başlatın ( **F5**tuşuna basın) veya kodunuzda (**F10** veya **F11**) adımlayarak hata ayıklamaya başlayın.

    IntelliTrace, her hata ayıklayıcı adımı, kesme noktası olayı ve işlenmemiş özel durum olayında uygulamanın işleminin anlık görüntüsünü alır. Bu olaylar, diğer IntelliTrace olaylarıyla birlikte **Tanılama araçları** penceresindeki **Olaylar** sekmesine kaydedilir. Bu pencereyi açmak için, **Hata Ayıkla**  >  **Windows**  >  **göster tanılama araçları**seçin.

    Anlık görüntülerin kullanılabildiği olayların yanında bir kamera simgesi görüntülenir.

    ![Anlık görüntülerle olaylar sekmesi](../debugger/media/intellitrace-events-tab-with-snapshots.png "Kesme noktaları ve adımlarda anlık görüntülerle olaylar sekmesi")

    Performans nedenleriyle, çok hızlı bir şekilde ilerlebilmeniz için anlık görüntüler alınmaz. Adımın yanında kamera simgesi görünürse daha yavaş adımlamayı deneyin.

## <a name="navigate-and-view-snapshots"></a>Anlık görüntülere git ve görüntüle

1. Hata ayıklama araç çubuğundaki **geri adım (alt + [)** ve **adım ileri (alt +])** düğmelerini kullanarak olaylar arasında gezinin.

    Bu düğmeler **Tanılama araçları penceresindeki** **Olaylar** sekmesinde görüntülenen olaylara gider. Bir olaya geri veya ileri dönmek, seçili olayda [geçmiş hata ayıklamayı](../debugger/historical-debugging.md) otomatik olarak etkinleştirir.

    ![Geri adımla ve Ilet düğmeleri](../debugger/media/intellitrace-step-back-icons-description.png "Geri adımla ve adım Ileri düğmeleri")

    Geri döndüğünüzde veya ileri adımla, Visual Studio geçmiş hata ayıklama moduna girer. Bu modda, hata ayıklayıcının bağlamı seçili olayın kaydedildiği zamana geçer. Visual Studio Ayrıca işaretçiyi kaynak penceredeki ilgili kod satırına da taşımayın.

    Bu görünümden, **çağrı yığını**, **Yereller**, **oto**ve **izleme** pencerelerinde değerleri inceleyebilirsiniz. Ayrıca, veri Ipuçlarını görüntülemek ve **komut** penceresinde ifade değerlendirmesi gerçekleştirmek için değişkenlerin üzerine gelin. Gördüğünüz veriler, uygulamanın o anda geçen işlemin anlık görüntüsünden alınmıştır.

    Bu nedenle, örneğin, bir kesme noktasına ulaşırsanız ve bir adım (**F10**) aldıysanız, **geri adım** düğmesi Visual Studio 'yu kesme noktasına karşılık gelen kod satırına geçmiş moduna geçirir.

    ![Anlık görüntü ile bir olayda geçmiş modunu etkinleştirme](../debugger/media/intellitrace-historical-mode-with-snapshot.png "Anlık görüntü ile bir olayda geçmiş modunu etkinleştirme")

2. Canlı yürütmeye dönmek için devam ' ı **(F5)** veya bilgi çubuğu 'Ndaki **canlı hata ayıklama bağlantısına dön** ' ü seçin.

3. Ayrıca, **Olaylar** sekmesinden bir anlık görüntü görüntüleyebilirsiniz. Bunu yapmak için, anlık görüntü içeren bir olay seçin ve **geçmiş hata ayıklamayı etkinleştir**' e tıklayın.

    ![Bir olayda geçmiş hata ayıklamayı etkinleştirin](../debugger/media/intellitrace-activate-historical-debugging.png "Bir olayda geçmiş hata ayıklamayı etkinleştirin")

    **Sonraki Ifadeyi ayarla** komutundan farklı olarak, anlık görüntüyü görüntülemek kodunuzu yeniden çalıştırmaz; Bu, geçmişte gerçekleştiği zaman bir noktada uygulamanın durumunun statik görünümünü sağlar.

    ![IntelliTrace adım geri 'ye Genel Bakış](../debugger/media/intellitrace-step-back-overview.png "IntelliTrace adım geri 'ye Genel Bakış")

    Visual Studio 'da değişkenlerin nasıl inceleneceği hakkında daha fazla bilgi edinmek için bkz [. hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)

## <a name="frequently-asked-questions"></a>Sık Sorulan Sorular

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>IntelliTrace 'in yalnızca IntelliTrace olayları modundan farkı nasıl farklıdır?

Yalnızca olaylar modundaki IntelliTrace, hata ayıklayıcı adımlarında ve kesme noktalarında geçmiş hata ayıklamayı etkinleştirmenizi sağlar. Ancak IntelliTrace yalnızca **Yereller** ve **oto** içindeki verileri yakalar ve Windows açık ise yalnızca genişletilmiş ve görüntüleme içinde verileri yakalar. Yalnızca olaylar modunda, genellikle değişkenlerin ve karmaşık nesnelerin tamamen bir görünümüne sahip olursunuz. Ayrıca, **izleme** penceresindeki ifade değerlendirmesi ve verileri görüntüleme desteklenmez.

Olaylar ve anlık görüntüler modunda, IntelliTrace karmaşık nesneler de dahil olmak üzere uygulamanın işleminin tüm anlık görüntüsünü yakalar. Bir kod satırında, bir kesme noktasında durdurulmuş gibi aynı bilgileri görebilirsiniz (ve daha önce bilgileri genişletmenizden bağımsız olarak). Bir anlık görüntü görüntülenirken ifade değerlendirmesi de desteklenir.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Bu özelliğin performans etkisi nedir? 

Genel Adımlama performansının etkisi uygulamanıza bağlıdır. Anlık görüntü alma ek yükü 30 MS 'nin üzerinde. Anlık görüntü alındığında, uygulamanın süreci ele alınır ve bu kopya askıya alınır. Bir anlık görüntüyü görüntülediğinizde, Visual Studio işlemin çatallanmış kopyasına ekleniyor. Her anlık görüntü için, Visual Studio yalnızca sayfa tablosunu kopyalar ve sayfaları, yazma kopyalama olarak ayarlar. Yığındaki nesneler ilişkili anlık görüntülerle hata ayıklayıcı adımları arasında değişiklik yapmışsa ilgili sayfa tablosu daha sonra kopyalanır ve bu da en az bellek maliyetine yol açar. Visual Studio bir anlık görüntü almak için yeterli bellek olmadığını algılarsa, bir tane almaz.

## <a name="known-issues"></a>Bilinen Sorunlar
* Windows 10 Fall Creators Update (RS3) sürümünden önceki Windows sürümlerinde IntelliTrace olayları ve anlık görüntü modu kullanıyorsanız ve uygulamanın hata ayıklama platformu hedefi x86 olarak ayarlandıysa, IntelliTrace anlık görüntü almaz.

    Geçici çözümler:
  * Windows 10 yıldönümü Güncelleştirmesi (RS1) ve sürümü 10.0.14393.2273 ' de çalışıyorsanız, KB4103720 ' yi [yükleyebilirsiniz](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720).
  * Windows 10 Creators Update (RS2) ve 10.0.15063.1112 sürüm ' de çalışıyorsanız, KB4103722 ' yi [yükleyebilirsiniz](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
  * Windows 10 Fall Creators Update ' e (RS3) yükler veya yükseltin.
  * Alternatif olarak:
    1. Visual Studio yükleyicisinden masaüstü için VC++ 2015.3 v140 araç seti (x86, x64) bileşenini yükleyin.
    2. Hedef uygulamayı derleyin.
    3. Hedef yürütülebilirin bayrağını ayarlamak için komut satırından editbin aracını kullanın `Largeaddressaware` . Örneğin, bu komutu (yolu güncelleştirdikten sonra) kullanabilirsiniz: "C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe"/LARGEADDRESSAWARE "C:\Path\To\Application\app.exe".
    4. Hata ayıklamayı başlatmak için **F5**'e basın. Şimdi, anlık görüntüler hata ayıklayıcı adımlarında ve kesme noktalarında alınır.

       > [!Note]
       > `Largeaddressaware`Her çalıştırılabilir dosyanın değişikliklerle yeniden oluşturulması durumunda bayrak ayarlanmalıdır.

* Kalıcı bir bellek eşlemeli dosya kullanan bir uygulamada uygulama işleminin bir anlık görüntüsü yapıldığında, anlık görüntüye sahip işlem, bellek eşlemeli dosyada (üst işlem kilidi serbest bırakıldıktan sonra bile) özel bir kilit barındırır. Diğer süreçler yine de bellek eşlemeli dosyayı okuyabilir, ancak yazamayacak.

  Geçici çözüm:
  * Hata ayıklama oturumunu sona erdirerek tüm anlık görüntüleri temizleyin.

* İşlemi, çok sayıda dll yükleyen bir uygulama gibi yüksek sayıda benzersiz bellek bölgesine sahip olan bir uygulamada hata ayıklarken, anlık görüntüler etkinken daha fazla performans etkilenebilir. Bu sorun, Windows 'un gelecek bir sürümünde değinilecek. Bu sorunla karşılaşıyorsanız, bizden bize ulaşın stepback@microsoft.com .

* Bir dosya **hata ayıklama > IntelliTrace ile kaydedilirken > IntelliTrace oturumunu** olaylar ve anlık görüntüler modu altına Kaydet ' in altında, anlık görüntülerden yakalanan ek veriler. iTrace dosyasında kullanılamaz. Kesme noktası ve adım olayları ' nda, dosyayı yalnızca IntelliTrace olayları modunda kaydettiğinizden aynı bilgileri görürsünüz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, IntelliTrace adım geri 'yi nasıl kullanacağınızı öğrendiniz. Diğer IntelliTrace özellikleri hakkında daha fazla bilgi edinmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [IntelliTrace Özellikleri](../debugger/intellitrace-features.md)
