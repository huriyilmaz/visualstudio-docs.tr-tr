---
title: Bir performans sorununun giderilmeden olasılığını nasıl artırabilirsiniz?
description: Visual Studio'da performans sorunları göndermek için ek bilgiler ve en iyi uygulamalar
author: madskristensen
ms.author: madsk
ms.date: 11/19/2019
ms.topic: reference
ms.openlocfilehash: f5c83a145eb56dcb95c6e9a299c690ae960442c9
ms.sourcegitcommit: 4bcd6abb89feff1cf8251e3ded73fdc30b67e347
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81615041"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Bir performans sorununun giderilebilme olasılığını artırma

"[Bir sorun bildir](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019)" aracı, Visual Studio kullanıcıları tarafından çeşitli sorunları bildirmek için yaygın olarak kullanılır. Visual Studio ekibi, kullanıcı geri bildirimindeki çökme ve yavaşlık eğilimlerini fark eder ve geniş bir kullanıcı alanını etkileyen sorunları giderir. Belirli bir geri bildirim bileti ne kadar işlem yapılabilirse, ürün ekibi tarafından teşhis edilme ve hızlı bir şekilde çözülmesi o kadar olasıdır. Bu belge, çökme veya yavaşlık sorunlarını raporederken en iyi uygulamaları açıklar ve bunları daha işlemuygulanabilir hale getirilebilir hale getirmelidir.

## <a name="general-best-practices"></a>Genel en iyi uygulamalar

Visual Studio, çok sayıda dili, proje türünü, platformu ve daha fazlasını destekleyen büyük ve karmaşık bir platformdur. Nasıl performans, hangi bileşenlerin bir oturumda yüklü ve etkin olduğu, uzantıların yüklü olduğu, Visual Studio ayarları, makine yapılandırması ve son olarak düzenlenen kodun şeklidir. Değişken sayısı göz önüne alındığında, görünür belirti aynı olsa da, bir kullanıcıdan gelen sorun raporunun başka bir kullanıcıdan gelen sorun raporuyla aynı altta yatan soruna sahip olup olmadığını söylemek zordur. Bu göz önüne alındığında, burada özel sorun raporu tanısı olma olasılığı daha yüksek olduğundan emin olmak için bazı en iyi uygulamalar vardır.

**Mümkün olduğunca belirli bir başlık sağlayın**

Bildirilen sorun için farklı imzalar arayın ve başlık mümkün olduğunca ekleyin. Başlık açıklayıcı ysa, ilgisiz sorunları olan kullanıcıların (ancak aynı yüzeysel belirti) biletinizi oylama veya yorum yapma olasılığı daha düşüktür, böylece *sorunuzun* tanısını zorlaştırır.

**Şüpheye düştüğünüzde, yeni bir sorun raporu günlüğe kaydedin**

Birçok sorun, farklı bir imza veya çoğaltmak için adımlar olmayabilir. Bu gibi durumlarda, yeni bir rapor bir upvote veya benzer bir dış *belirti*rapor başka bir rapor, bir yorum daha iyidir. Raporun türüne bağlı olarak, bu belgede daha sonra açıklandığı şekilde raporunuza ek tanılama dosyaları ekleyin.

**Soruna özel en iyi uygulamalar**

Aşağıda iyi tanılama dosyaları olmadan tanılamak zor sorunlar açıklanmıştır. Sorununuzu en iyi açıklayan servis talebini tanımladıktan sonra, söz konusu servis talebine özgü geri bildirim adımlarını izleyin.

-   [Çöküyor:](#crashes) İşlem (Visual Studio) beklenmedik bir şekilde sona erdiğinde bir kilitlenme oluşur.

-   [Yanıt vermeme:](#unresponsiveness) VS uzun bir süre yanıt vermez hale gelir.

-   [Yavaşlık sorunları:](#slowness-and-high-cpu-issues) VS'deki belirli bir eylem istenenden daha yavaştır

-   [Yüksek Cpu:](#slowness-and-high-cpu-issues) Beklenmeyen yüksek CPU kullanımının uzun süreleri

-   [İşlem Dışı Sorunlar:](#out-of-process-issues) Visual Studio uydu işleminin neden olduğu bir sorun

## <a name="crashes"></a>Çökü -yor
İşlem (Visual Studio) beklenmedik bir şekilde sona erdiğinde bir kilitlenme oluşur.

**Doğrudan tekrarlanabilir çökmeler**

Doğrudan tekrarlanabilir çökmeler aşağıdaki tüm özelliklere sahip durumlardır:

- Bilinen bir dizi adımı izleyerek gözlemlenebilir

- Birden çok bilgisayarda görülebilir (varsa)

- Örnek kodda veya geri bildirimin bir parçası olarak bağlanabilen veya sağlanabilecek bir projede çoğaltılabilir (adımlar bir proje veya belgeyi açmayı içeriyorsa)

Bu sorunlar için , "[Sorun Nasıl Bildirilir](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)" deki adımları izleyin ve aşağıdakileri ekleyemin:

-   Sorunu yeniden oluşturma adımları

-   Yukarıda açıklandığı gibi bağımsız bir repro projesi. Bağımsız repro mümkün değilse, o zaman lütfen ekleyin:

    -   Açık projelerin dili (C\#, C++, vb.)

    -   Proje türü (Konsol Uygulaması, ASP.NET, vb.)


> [!NOTE]
> **En değerli geri bildirim:** Bu durumda, en değerli geri bildirim, sorunu örnek kaynak koduyla birlikte yeniden oluşturmak için gereken adımlar kümesidir.

**Bilinmeyen çöküyor**

Çökmelerinize neyin neden olduğundan emin değilseniz veya bunlar rasgele görünüyorsa, Visual Studio her çöktüğünde çöplükleri yerel olarak yakalayabilir ve bunları ayrı geri bildirim öğelerine ekleyebilirsiniz. Visual Studio çöktüğünde dökümleri yerel olarak kaydetmek için yönetici komut penceresinde aşağıdaki komutları çalıştırın:

```
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe" /v DumpType /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe" /v DumpCount /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"
```

Döküm sayısını ve döküm klasörünü uygun şekilde özelleştirin. Bu ayarlar hakkında daha fazla bilgiyi [burada](/windows/win32/wer/collecting-user-mode-dumps)bulabilirsiniz.

> [!NOTE]
> Görev Yöneticisi kullanılarak yakalanan çöplükler, büyük olasılıkla yanlış bitness'e sahip olur, bu da onları daha az kullanılabilir yapar. Yukarıda açıklanan yordam, bir yığın dökümü yakalamak için tercih edilen yoldur. Görev Yöneticisi'ni kullanmak istiyorsanız, şu anda çalışmakta olan görev yöneticisini kapatın,\\32bit Görev\\Yöneticisi'ni (windir% syswow64 taskmgr.exe) başlatın ve oradan bir yığın dökümü toplayın.

> [!NOTE] 
> Bu yöntemle üretilen her döküm dosyası 4 GB boyutuna kadar olacaktır. DumpFolder'ı yeterli sürücü alanına sahip bir konuma ayarladığınızı veya DumpCount'ı uygun şekilde ayarladıklıolun.

Visual Studio her çöktüğünde, devenv.exe bir döküm dosyası **oluşturur.[ yapılandırılmış konumda sayı].dmp** dosyası.

Ardından Visual Studio'nun "Bir Sorunu Bildir..." Özelliği. Bu uygun dökümü eklemek için izin verecektir.

1.  Bildirdiğiniz kilitlenme için döküm dosyasını bulun (doğru Oluşturma süresine sahip bir dosya arayın)

2.  Mümkünse, geri\*bildirim göndermeden önce boyutunu küçültmek için dosyayı (.zip) zip

3.  " Sorunu Nasıl Bildirilir " (Sorunu[Nasıl Bildirilir)](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)adlı adımlardan izleyin ve yığın dökümünün yeni bir geri bildirim öğesine eklenmesini sağlayın.

> [!NOTE] 
> **En değerli geri bildirim:** Bu durumda, en değerli geribildirim kaza sırasında yakalanan yığın dökümü dür.

## <a name="unresponsiveness"></a>Yanıt vermeme
VS uzun bir süre yanıt vermez hale gelir.

**Doğrudan tekrarlanabilir Yanıt sızması**

Çökmelerle ilgili ilgili bölümde açıklandığı gibi, kolayca çoğaltılabilen, birden çok makinede görülebilen ve küçük bir örnekte gösterilebilen sorunlar için, en değerli geri bildirim raporları sorunu yeniden oluşturma adımlarını içeren ve sorunu gösteren örnek kaynak kodu içeren raporlardır.

**Bilinmeyen Yanıt Verme**

Yanıt vermeme, öngörülemeyen bir şekilde kendini gösterirse, bir sonraki olayda, Visual Studio'nun yeni bir örneğini başlatın ve bu örnekten bir sorun bildirin.
["Kaydet" ekranında,](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019#record-a-repro)yanıt vermeyen Visual Studio oturumunu seçtiğinizden emin olun.

Yanıt vermeyen Visual Studio örneği Yönetici modunda başlatıldıysa, ikinci örneğin de Administrator modunda başlatılması gerekir.

>[!NOTE] 
> **En değerli geri bildirim:** Bu durumda, en değerli geribildirim Yanıtsizlik sırasında yakalanan yığın dökümüdür.

## <a name="slowness-and-high-cpu-issues"></a>Yavaşlık ve Yüksek CPU Sorunları

Yavaşlık veya yüksek CPU kullanım sorununu en çok işlem yapılabilir kılan şey, yavaş çalışma veya yüksek CPU olayı devam ederken yakalanan bir performans izlemesidir.

>[!NOTE] 
> Mümkün olduğunda, her senaryoyu ayrı, belirli bir geri bildirim raporunda yalıtın.
Örneğin, yazma ve gezinme nin her ikisi de yavaşsa, sorun başına bir kez aşağıdaki adımları izleyin. Bu, ürün ekibinin belirli sorunların nedenini yalıtmanıza yardımcı olur.

Performansı yakalamada en iyi sonuçları elde etmek için aşağıdaki adımları izleyin:

1.  Zaten çalışmıyorsa, sorunu yeniden oluşturacağınız Visual Studio'nun bir kopyasını açın

    -   Sorunu yeniden oluşturmak için her şeyi ayarlayın. Örneğin, belirli bir projenin açıkbir dosyayla yüklenmesi gerekiyorsa, devam etmeden önce bu adımların her ikisinin de tamamlandığından emin olun.

    -   Bir çözümü yüklemeye özgü bir sorun *bildirmiyorsanız,* performans izlemesini kaydetmeden önce çözümü açtıktan sonra 5-10 dakika (veya çözüm boyutuna bağlı olarak daha fazla) beklemeyi deneyin. Çözüm yükleme işlemi büyük miktarda veri üretir, bu nedenle birkaç dakika beklemek bildirdiğiniz belirli soruna odaklanmamıza yardımcı olur.

2.  Visual Studio'nun ikinci bir kopyasını *çözüm olmadan* başlatın

3.  Visual Studio'nun yeni kopyasında Sorun **Bildir** aracını açın

4.  "İzleme ve yığın dökümü (isteğe bağlı)" adımına ulaşana kadar [Sorunu Bildirme Adımlarını](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) izleyin.

5.  Visual Studio'nun (performans sorunuyla karşılaşan) ilk kopyasını kaydetmeyi ve kaydetmeye başlamayı seçin.

    -   Steps Kaydedici uygulaması görünür ve kaydetmeye başlar.

    -   **Kayıt sırasında,** Visual Studio'nun ilk kopyasında sorunlu eylemi gerçekleştirin. Kaydedilen süre içinde görünmüyorsa, belirli performans sorunlarını düzeltmek bizim için zordur.

    -   Eylem 30 saniyeden kısaysa ve kolayca tekrarlanabilirse, sorunu daha fazla göstermek için eylemi yineleyin.

    -   Çoğu durumda, sorunlu eylem 30 saniyeden fazla sürdü (veya tekrarlandı) özellikle sorunları göstermek için 60 saniyelik bir izleme yeterlidir. Süre, sabit olmasını istediğiniz davranışı yakalamak için gerektiği şekilde ayarlanabilir.

6.  Rapor etmek istediğiniz yavaş işlem veya yüksek CPU olayı biter bitmez Steps Recorder'daki "Kaydı Durdur"u tıklatın. Performans izleme işleminin işlenmesi birkaç dakika sürebilir.

7.  Tamamlandıktan sonra, geri bildiriminize birkaç ek olacaktır. Sorunun yeniden oluşturulmasına yardımcı olabilecek ek dosyalar (örnek bir proje, ekran görüntüleri, videolar, vb.) takın.

8.  Geri bildirimi gönderin.

Performans izleme kaydı yaparken, bildirdiğiniz yavaş işlem veya yüksek CPU sona ererse, kaydı hemen durdurun. Çok fazla bilgi toplanırsa, en eski bilgiler üzerine yazılır. İlginç işlemden sonra izleme kısa sürede (birkaç saniye içinde) durdurulmazsa, yararlı izleme verileri üzerine yazılır.

Geliştirici Topluluğu web sitesindeki mevcut geri bildirim öğelerine doğrudan performans izlemeleri eklemeyin. Ek bilgi istemek/sağlamak, Visual Studio'nun yerleşik Sorun Bildir aracında desteklenen bir iş akışıdır. Önceki bir geri bildirim öğesini çözmek için bir performans izleme gerekiyorsa, geri bildirim öğesinin durumunu yeni bir sorunu bildirmekle aynı şekilde yanıtlanabilecek "Daha Fazla Bilgiye İhtiyacım" olarak ayarlarız. Ayrıntılı talimat için lütfen Sorun Bildir aracının belgesindeki ["Daha Fazla Bilgiye İhtiyaç" bölümüne](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017?view=vs-2017#when-further-information-is-needed-need-more-info) bakın.

> [!NOTE] 
> **En değerli geri bildirim:** Hemen hemen tüm yavaşlık/yüksek CPU sorunları için, en değerli geri bildirim, bu süre içinde davranışı\*yakalayan performans izleme (.etl.zip) ile birlikte ne yapmaya çalıştığınızın üst düzey bir açıklamasıdır.

**Gelişmiş Performans İzleri**

Sorun Bildir aracındaki izleme toplama özellikleri çoğu senaryo için yeterlidir. Ancak, izleme koleksiyonu üzerinde daha fazla denetimin gerekli olduğu zamanlar vardır (örneğin, daha büyük bir arabellek boyutuyla izleme), bu durumda PerfView kullanmak için harika bir araçtır. PerfView aracını kullanarak performans izlemeyi el ile kaydetme [adımları, PerfView](https://github.com/dotnet/roslyn/wiki/Recording-performance-traces-with-PerfView) sayfasındaki Kayıt performans izlemelerinde bulunabilir.

## <a name="out-of-process-issues"></a>İşlem Dışı Sorunlar

> [!NOTE]
> Visual Studio 2019 sürüm 16.3 ile başlayarak, işlem dışı günlükler, Sorun Bildir aracı kullanılarak gönderilen geri bildirime otomatik olarak eklenir. Ancak, sorun doğrudan tekrarlanabilirse, aşağıdaki adımları izleyerek sorunu daha iyi tanılamaya yardımcı olmak için ek bilgi eklemenize yardımcı olabilir.

Visual Studio'ya paralel çalışan ve ana Visual Studio sürecinin dışından çeşitli özellikler sağlayan bir dizi uydu işlemi vardır. Bu uydu işlemlerinden birinde bir hata oluşursa genellikle Visual Studio tarafında bir 'StreamJsonRpc.RemoteInvocationException' veya 'StreamJsonRpc.ConnectionLostException' olarak görülür.

Bu tür sorunları en çok işlem yapılabilir kılan şey, aşağıdaki adımları izleyerek toplanabilecek ek günlükler sağlamaktır:

1.  Bu doğrudan tekrarlanabilir bir sorunsa, **%geçici%/servicehub/logs** klasörünü silerek başlayın. Bu sorunu yeniden oluşturamıyorsanız, lütfen bu klasörü bozulmadan tutun ve aşağıdaki madde işaretleri yoksayın:

    -   Küresel ortam değişkeni **ServiceHubTraceLevel'i** **Herkese** Ayarlama
    -   Sorunu yeniden üretin.

2.  Microsoft Visual Studio ve .NET Framework Log Collection Collection Aracını [buradan](https://www.microsoft.com/download/details.aspx?id=12493)indirebilirsiniz.
3.  Aracı çalıştırın. Bu% **temp% /vslogs.zip**bir zip dosyası çıktır. Lütfen bu dosyayı geri bildiriminize iliştirin.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio geri bildirim seçenekleri](../ide/feedback-options.md)
* [Mac için Visual Studio ile ilgili bir sorun bildirme](/visualstudio/mac/report-a-problem)
* [C++ ile ilgili bir sorunu bildirme](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio Geliştirici Topluluğu](https://developercommunity.visualstudio.com/)
* [Geliştirici Topluluğu veri gizliliği](developer-community-privacy.md)
