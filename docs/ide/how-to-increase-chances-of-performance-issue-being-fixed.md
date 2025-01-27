---
title: Bir performans sorununun düzeltilme olasılığını artırma
description: Visual Studio 'de performans sorunları göndermek için ek bilgiler ve en iyi uygulamalar
ms.custom: SEO-VS-2020
author: madskristensen
ms.author: madsk
manager: jmartens
ms.technology: vs-ide-general
ms.date: 11/19/2019
ms.topic: conceptual
ms.openlocfilehash: c37f98198e999b1ab31bb6e371ca5b8700037736
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635333"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Bir performans sorununun düzeltilme olasılığını artırma

"[sorun bildir](./how-to-report-a-problem-with-visual-studio.md?view=vs-2019&preserve-view=true)" aracı, Visual Studio kullanıcıların bir dizi sorunu bildirmek için yaygın olarak kullanılır. Visual Studio takım, kullanıcı geri bildirimleriyle ilgili kilitlenme ve yavaşlığın eğilimlerini ve çok sayıda kullanıcıyı etkileyen sorunları giderir. Belirli bir geri bildirim bileti daha fazla eyleme çıkılarak, büyük olasılıkla ürün ekibi tarafından hızlı bir şekilde tanılanabilir ve çözümlenir. Bu belge, daha fazla işlem yapılabilir olması için kilitlenme veya yavaşlık sorunları bildirirken en iyi uygulamaları açıklar.

## <a name="general-best-practices"></a>Genel en iyi uygulamalar

Visual Studio, çok sayıda dili, proje türünü, platformu ve daha fazlasını destekleyen büyük ve karmaşık bir platformdur. uygulamasının nasıl gerçekleştirdiği, bir oturumda hangi bileşenlerin yüklü ve etkin olduğu, yüklü uzantıların, Visual Studio ayarlarının, makine yapılandırmasının ve son olarak düzenlenmekte olan kodun şeklinin bulunduğu bir işlevdir. Değişken sayısı verildiğinde, bir kullanıcıdan gelen sorun raporunun, başka bir kullanıcıdan sorun raporu olarak aynı olup olmadığını, görünür belirti aynı olsa bile söylemek zordur. Bu, belirli sorun raporunuzun tanıma olasılığının daha yüksek olduğundan emin olmak için bazı en iyi yöntemler aşağıda verilmiştir.

**Mümkün olduğunca belirli bir başlık sağlayın**

Bildirilmekte olan soruna yönelik ayrı imzalar bulun ve başlıkta mümkün olduğunca fazla sayıda dahil edin. Başlık açıklayıcı ise, ilgisiz sorunları olan (ancak aynı yararlanmayan belirti) kullanıcıların *biletinizi* oylamasını veya yorum yapmasını, böylece sorununuzun tanılamasını zorlaştırır.

**Şüpheli olduğunda, yeni bir sorun raporu Kaydet**

Birçok sorun için herhangi bir farklı imza veya yeniden oluşturma adımı bulunmayabilir. Bu gibi durumlarda, yeni bir rapor, bir veya daha fazla rapor üzerinde, benzer bir dışa dönük *belirti* bildiren bir açıklamadan daha iyidir. Raporun türüne bağlı olarak, bu belgenin ilerleyen kısımlarında açıklandığı gibi Raporunuza ek tanılama dosyaları ekleyin.

**Soruna özgü en iyi yöntemler**

Aşağıda açıklanan sorunlar iyi tanılama dosyaları olmadan tanılanması zor olan sorunlardır. Sorununuzu en iyi açıklayan durumu tanımladıktan sonra, bu servis talebine özgü geri bildirim adımlarını izleyin.

- [Kilitlenmeler:](#crashes) işlem (Visual Studio) beklenmedik bir şekilde sonlandırıldığında kilitlenme oluşur.

- [Yanıt verme süresi:](#unresponsiveness) , Uzun bir süre boyunca yanıt vermemeye başladı.

- [Yavaşlık sorunları:](#slowness-and-high-cpu-issues) VS 'deki belirli bir eylem, istenenden daha yavaş

- [Yüksek CPU:](#slowness-and-high-cpu-issues) Beklenmedik bir şekilde yüksek CPU kullanımı uzatılmış dönemleri

- [Işlem dışı sorunlar:](#out-of-process-issues) Visual Studio uydu sürecinin neden olduğu bir sorun oluştu

## <a name="crashes"></a>Çökme
işlem (Visual Studio) beklenmedik bir şekilde sonlandırıldığında kilitlenme oluşur.

**Doğrudan tekrarlanabilir kilitlenmeler**

Doğrudan tekrarlanabilir kilitlenmeler, aşağıdaki özelliklerin tümüne sahip olan durumlardır:

- Bilinen bir adım kümesini izleyerek gözlemlenebilir

- Birden çok bilgisayarda (varsa) gözlemlenebilir

- Örnek kodda veya geri bildirimin bir parçası olarak bağlanabilen ya da sağlanbağlanabilen bir projede yeniden oluşturulabilir (adımlar bir proje veya belge açmak içeriyorsa)

Bu sorunlar için "[sorunu bildirme](./how-to-report-a-problem-with-visual-studio.md)" bölümündeki adımları izleyin ve şunları eklediğinizden emin olun:

- Sorunu yeniden oluşturma adımları

- Yukarıda açıklanan şekilde tek başına yeniden üretme projesi. Tek başına yeniden oluşturma mümkün değilse lütfen şunları ekleyin:

  - Açık projelerin dili (C \# , C++, vb.)

  - Proje türü (konsol uygulaması, ASP.NET, vb.)

> [!NOTE]
> **En değerli geri bildirim:** Bu durumda, en değerli geri bildirim, sorunu örnek kaynak kodla birlikte yeniden oluşturma adımları kümesidir.

**Bilinmeyen kilitlenmeler**

kilitlenmelere neden olan veya rastgele göründüler konusunda emin değilseniz, her çökme Visual Studio kilitleniyor ve bunları ayrı geri bildirim öğelerine iliştirebilmeniz için dökümleri yerel olarak yakalayabilirsiniz. Visual Studio çöktüğü zaman dökümlerini yerel olarak kaydetmek için yönetici komut penceresinde aşağıdaki komutları çalıştırın:

```
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"
```

Döküm sayısını ve döküm klasörünü uygun şekilde özelleştirin. Bu ayarlarla ilgili daha fazla bilgiyi [burada](/windows/win32/wer/collecting-user-mode-dumps)bulabilirsiniz.

> [!NOTE]
> Görev Yöneticisi kullanılarak yakalanan dökümlerden büyük olasılıkla yanlış bit kullanımı olabilir ve bu da daha az kullanılabilir hale gelir. Yukarıda açıklanan yordam, yığın dökümünü yakalamak için tercih edilen yoldur. Görev Yöneticisi 'ni kullanmak istiyorsanız, çalışmakta olan birini kapatın, 32bit görev yöneticisini (% windir% \\ syswow64 \\taskmgr.exe) başlatın ve buradan bir yığın dökümü toplayın.

> [!NOTE]
> Bu yöntem tarafından üretilen her döküm dosyası boyutu 4 GB 'a kadar olacaktır. DumpFolder 'ı yeterli sürücü alanına sahip bir konuma ayarladığınızdan emin olun veya DumpCount sayısını uygun şekilde ayarlayın.

her Visual Studio kilitlenirse,devenv.exe bir döküm dosyası oluşturacaktır **. [ Number]. dmp** dosyası yapılandırılmış konumda.

sonra, Visual Studio "sorun bildir..." seçeneğini kullanın. Özellik. Uygun dökümü eklemenize olanak sağlayacak.

1. Rapor ettiğiniz kilitlenme için döküm dosyasını bulun (doğru oluşturulma zamanına sahip bir dosya arayın)

2. Mümkünse, \* geri bildirim göndermeden önce boyutunu azaltmak için dosyayı (.zip) ZIP

3. "[Sorunu bildirme](./how-to-report-a-problem-with-visual-studio.md)" bölümündeki adımları izleyin ve yığın dökümünü yeni bir geri bildirim öğesine ekleyin.

> [!NOTE]
> **En değerli geri bildirim:** Bu durumda, en değerli geri bildirim kilitlenme sırasında yakalanan yığın dökümünden oluşur.

## <a name="unresponsiveness"></a>Yanıt verme
, Uzun bir süre boyunca yanıt vermemeye başladı.

**Doğrudan tekrarlanabilir yanıt verme**

Kilitlenmelerde karşılık gelen bölümünde açıklandığı gibi, birden çok makinede görülen ve küçük bir örnekte görünebileceği sorunlar için, en değerli geri bildirim raporları, sorunu yeniden oluşturma adımlarını içeren ve sorunu gösteren örnek kaynak kodu içeren bir sorundur.

**Bilinmeyen yanıt verme süresi**

yanıt veremeyen bir şekilde kendi kendine bildirim, bir sonraki oluşumde Visual Studio yeni bir örneğini başlatın ve bu örnekten bir sorun bildirin.
"kayıt" ekranında yanıt vermeyen Visual Studio oturumu seçtiğinizden emin olun. (Sorunu yeniden oluşturmak için izleyediğimiz eylemleri kaydetme hakkında daha fazla bilgi için bkz. [sorun bildirme](./how-to-report-a-problem-with-visual-studio.md) sayfasında 8. adım.)

yanıt vermeyen Visual Studio örneği yönetici modunda başlatıldıysa ikinci örneğin da yönetici modunda başlatılması gerekir.

>[!NOTE]
> **En değerli geri bildirim:** Bu durumda, en değerli geri bildirim, yanıt verme sırasında yakalanan yığın dökümünlüklarıdır.

## <a name="slowness-and-high-cpu-issues"></a>Yavaşlık ve yüksek CPU sorunları

Yavaşlan veya yüksek CPU kullanımı sorunu, yavaş işlem veya yüksek CPU olayı devam ederken yakalanan bir performans izdir.

>[!NOTE]
> Mümkün olduğunda, her senaryoyu ayrı ve belirli bir geri bildirim raporunda yalıtın.
Örneğin, yazma ve gezinme her ikisi de yavaşsa, sorun başına aşağıdaki adımları izleyin. Bu, ürün takımının belirli sorunların nedenini yalıtmasına yardımcı olur.

Performansı yakalamaya en iyi sonuçları elde etmek için şu adımları izleyin:

1. zaten çalışmıyorsa, sorunu yeniden oluşturabileceğiniz Visual Studio açık bir kopyasına sahiptir

    - Sorunu yeniden oluşturmak için her şeyin ayarlanmış olmasını sağlar. Örneğin, belirli bir dosya açıldığında belirli bir projenin yüklenmesi gerekiyorsa, devam etmeden önce bu adımların her ikisinin de tamamlanmış olduğundan emin olun.

    - Bir çözümü yüklemeye özgü bir sorun *bildirmeyen* performans izlemesini kaydetmeden önce çözümü açtıktan sonra, çözüm boyutuna bağlı olarak 5-10 dakika (veya daha fazla) beklemeyi deneyin. Çözüm yükleme işlemi büyük miktarda veri üretir, bu nedenle birkaç dakika beklemek, raporlamadaki belirli bir sorunu odaklanmamıza yardımcı olur.

2. *hiçbir çözüm açık olmadan* Visual Studio ikinci bir kopyasını başlat

3. Visual Studio yeni kopyasında **sorun bildir** aracını açın

4. "İzleme ve yığın dökümü sağlayın (isteğe bağlı)" adımına ulaşana kadar [sorun bildirme](./how-to-report-a-problem-with-visual-studio.md) bölümündeki adımları izleyin.

5. Visual Studio ilk kopyasını (performans sorunundan bir sorunla karşılaşmadan) kaydetmeyi ve kaydı başlatmayı seçin.

    - Adım Kaydedicisi uygulaması görüntülenir ve kayıt başlatılır.

    - **Kayıt sırasında,** Visual Studio ilk kopyasında sorunlu eylemi gerçekleştirin. Kaydedilen süre içinde görünmedikleri takdirde belirli performans sorunlarını düzeltmemizi zorlaştırıyor.

    - Eylem 30 saniyeden kısaysa ve kolayca tekrarlanabilir, sorunu daha fazla göstermek için eylemi tekrarlayın.

    - Çoğu durumda, özellikle de sorunlu bir işlem 30 saniyeden uzun süre boyunca sorunları göstermek için 60 saniyelik bir izleme yeterlidir. Süre, düzeltilmesi gereken davranışı yakalamak için gerektiği şekilde ayarlanabilir.

6. Raporlamak istediğiniz yavaş işlem veya yüksek CPU olayı tamamlandıktan hemen sonra Adım Kaydedicisi içindeki "Kaydı Durdur" seçeneğine tıklayın. Performans izlemenin işlenmesi birkaç dakika sürebilir.

7. İşlem tamamlandıktan sonra geri bildiriminiz için birkaç ek olacaktır. Sorunu yeniden oluşturmaya yardımcı olabilecek ek dosyalar ekleyin (örnek bir proje, ekran görüntüleri, videolar vb.).

8. Geri bildirimi gönderin.

Bir performans izlemesini kaydederken, raporlama yaptığınız yavaş işlem veya yüksek CPU bir uçtan geliyorsa kaydı hemen durdurun. Çok fazla bilgi toplanırsa, en eski bilgilerin üzerine yazılır. İzleme yakında durdurulmamışsa (birkaç saniye içinde), ilginç bir işlemden sonra, yararlı izleme verilerinin üzerine yazılır.

geliştirici Community web sitesindeki mevcut geri bildirim öğelerine doğrudan performans izlemeleri eklemeyin. ek bilgi isteme/sağlama, Visual Studio yerleşik bir sorun aracında desteklenen bir iş akışıdır. Önceki bir geri bildirim öğesini çözümlemek için bir performans izlemesi gerekliyse, geri bildirim öğesinin durumunu "daha fazla bilgi gerekiyor" olarak ayarlayacağız, bu da yeni bir sorunu raporlama ile aynı şekilde yanıt verebilir. Ayrıntılı yönerge için lütfen Sorun Bildir [aracının belgesinde "Daha](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed) Fazla Bilgi Gerekiyor" bölümüne bakın.

> [!NOTE]
> **En değerli geri bildirim:** Neredeyse tüm yavaşlık/yüksek CPU sorunları için en değerli geri bildirim, o sırada davranışı yakalayan performans izlemesi ( .etl.zip) ile birlikte yapmaya çalıştığınız şeyi üst düzey bir \* açıklamadır.

**Gelişmiş Performans İzlemeleri**

Sorun bildir aracında izleme toplama özellikleri çoğu senaryo için yeterlidir. Ancak izleme koleksiyonu üzerinde daha fazla denetime ihtiyaç duyulan zamanlar (örneğin, daha büyük bir arabellek boyutuna sahip izleme) vardır ve bu durumda PerfView harika bir araçtır. PerfView aracını kullanarak performans izlemelerini el ile kaydetme adımları [PerfView](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Recording-performance-traces-with-PerfView.md) ile performans izlemelerini kaydetme sayfasında bulunabilir.

## <a name="out-of-process-issues"></a>İşlem Dışında Sorunlar

> [!NOTE]
> 2019 Visual Studio 16.3 sürümünden itibaren, işlem yapılmamış günlükler Sorun Bildir aracı kullanılarak gönderilen geri bildirime otomatik olarak eklenir.
Ancak, sorun doğrudan yeniden tekrarlanabilirse, aşağıdaki adımların ardından sorun daha iyi tanılamaya yardımcı olacak ek bilgiler eklemeye yardımcı olabilir.

Bu işlemle paralel olarak çalıştıran ve ana Visual Studio dışından çeşitli özellikler sağlayan bir dizi uydu Visual Studio vardır. Bu uydu işlemlerden biri hata oluşursa genellikle Visual Studio tarafında 'StreamJsonRpc.RemoteInvocationException' veya 'StreamJsonRpc.ConnectionLostException' olarak görülür.

Bu tür sorunları en çok eyleme değiştirilebilir yapan şey, aşağıdaki adımların ardından toplanabilir ek günlükler sağlamaktır:

1. Bu doğrudan yenidenlanabilir bir sorunsa ,başlangıç olarak **%temp%/servicehub/logs klasörünü** silin. Bu sorunu yeniden oluşturamazsanız lütfen bu klasörü olduğu gibi kullanın ve aşağıdaki madde işaretlerine dikkat edin:

    - **ServiceHubTraceLevel genel ortam değişkenlerini All** olarak **ayarlayın**
    - Sorunu yeniden üretin.

2. Günlük Toplama Microsoft Visual Studio .NET Framework'nı buradan [indirin.](https://www.microsoft.com/download/details.aspx?id=12493)
3. Aracı çalıştırın. Bu, **%temp%/vslogs.zip**. Lütfen bu dosyayı geri bildiriminize iliştirin.

## <a name="see-also"></a>Ayrıca bkz.

* [Sorun bildirme Mac için Visual Studio](/visualstudio/mac/report-a-problem)
* [C++ ile ilgili bir sorun bildirme](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio Geliştirici Community](https://developercommunity.visualstudio.com/home)
* [Geliştirici Topluluğu veri gizliliği](developer-community-privacy.md)