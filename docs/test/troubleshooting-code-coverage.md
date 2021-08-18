---
title: Kod Kapsamı Sorunlarını Giderme
description: Yerel ve yönetilen derlemeler için veri toplamayı beklediğinizde Visual Studio boş sonuç iletilerini nasıl çözümleyebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: troubleshooting
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ea2976e01f8f02b0d6ea858afceb43ecad7ef1c7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054125"
---
# <a name="troubleshoot-code-coverage"></a>Kod kapsamı sorunlarını giderme

Visual Studio'daki kod kapsamı analiz aracı, yerel ve yönetilen derlemeler *(.dll* *veya*.exetoplar). Ancak bazı durumlarda Kod Kapsamı **Sonuçları penceresinde** "Boş sonuçlar oluştu: ...." gibi bir hata görüntülenir. Boş sonuçlar alamanın birkaç nedeni vardır. Bu makale bu sorunları çözmenize yardımcı olur.

## <a name="what-you-should-see"></a>Görmeniz gereken

**Test** menüsünde Bir **Kod Kapsamı** Çözümle komutunu seçerseniz ve derleme ve testler başarıyla çalıştırıldısa, Kod Kapsamı penceresinde sonuçların **listesini görüyorsanız.** Ayrıntıları görmek için öğeleri genişletmeniz gerekebilir.

::: moniker range=">=vs-2019"
![Renklendirme ile kod kapsamı sonuçları](../test/media/vs-2019/codecoverage1.png)
::: moniker-end
::: moniker range="vs-2017"
![Renklendirme ile kod kapsamı sonuçları](../test/media/codecoverage1.png)
::: moniker-end

Daha fazla bilgi için [bkz. Test edilen koda ne kadar kod olduğunu belirlemek için kod kapsamı kullanma.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Sonuçları ya da eski sonuçları görmek için olası nedenler

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Visual Studio'nun doğru sürümüne sahip misiniz?

Bir Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Hiçbir sınama yürütülemedi

Analiz &mdash; Çıkış pencerenizi kontrol edin. Açılan **listeden Çıkışı Göster** listesinde Testler'i **seçin.** Herhangi bir uyarı veya hatanın günlüğe kaydedilip kaydedilmediğine bakın.

Açıklama &mdash; Kod kapsamı analizi testler çalışırken yapılır. Testler çalıştırıldığında sadece belleğe yüklenen derlemeleri içerir. Testlerden hiçbiri yürütülmezse, kod kapsamı bildirecek bir şey yoktur.

Çözüm &mdash; Test Gezgini'nde, **testlerin başarıyla çalıştığını** doğrulamak için Hepsini Çalıştır'ı seçin. Kod Kapsamı Analizi'ne başlamadan önce **tüm hataları düzeltin.**

### <a name="youre-looking-at-a-previous-result"></a>Önceki bir sonucu arıyor

Testlerinizi değiştirerek yeniden çalıştırarak eski çalıştırmanın kod renklendirmesi dahil olmak üzere önceki bir kod kapsamı sonucu görünür durumda olabilir.

1. Kod **Kapsamı Analiz Etme'i çalıştırın.**

2. Kod Kapsamı Sonuçları penceresinde en son sonuç kümesi'nin **seçildiğinden emin** olun.

### <a name="pdb-symbol-files-are-unavailable"></a>.pdb (simge) dosyaları kullanılamaz

Analiz &mdash; Derleme hedef klasörünü açın (genellikle *bin\debug*) ve her derleme için,.dllveya.exe dosyasıyla aynı dizinde bir *.pdb* *dosyası olduğunu* doğrulayın.

Açıklama Kod kapsamı altyapısı, her derlemenin test çalıştırması sırasında erişilebilen ilişkili &mdash; *.pdb* dosyasına sahip olmasını gerektirir. Belirli bir derleme için *.pdb* dosyası yoksa, derleme çözümlanmaz.

*.pdb* dosyası, dosya dosyalarıyla aynı derlemeden.dll *.exe* gerekir.

Çözüm &mdash; Derleme ayarlarınızın *.pdb dosyasını oluşturması gerekir.* Proje *güncelleştirilirken .pdb* dosyaları güncelleştirilmezse, proje özelliklerini açın,  Derleme sayfasını seçin, **Gelişmiş'i** seçin ve Hata Ayıklama **Bilgileri'ne bakın.**

C++ projeleri için, oluşturulan .pdb dosyalarının tam hata ayıklama bilgilerine sahip olduğundan emin olur. Proje özelliklerini açın ve BağlantıLayıcı **Hata** Ayıklama Oluşturma Hata Ayıklama Bilgisi Oluştur'un paylaşım ve yayımlama için en iyi duruma getirilmiş Hata Ayıklama Bilgileri Oluştur  >    >   **(/DEBUG:FULL)** olarak ayar olduğunu doğrulayın.

*.pdb ve* *.dll* *veya.exe* farklı yerlerde yer varsa, *.pdb* dosyasını aynı dizine kopyalayın. Başka bir konumda *.pdb* dosyalarını aramak için kod kapsamı altyapısını yapılandırmak da mümkündür. Daha fazla bilgi için [bkz. Kod kapsamı analizini özelleştirme.](../test/customizing-code-coverage-analysis.md)

### <a name="use-an-instrumented-or-optimized-binary"></a>Araçlı veya iyileştirilmiş ikili dosya kullanma

Analiz İkili dosyanın Profil Destekli İyileştirme gibi herhangi bir gelişmiş iyileştirmeden olup olmadığını veya dosya veya profil oluşturma gibi bir profil oluşturma aracı tarafından &mdash; *vsinstr.exevsperfmon.exe.* **

Açıklama Bir derleme başka bir profil oluşturma aracı tarafından zaten araçsa veya iyileştirilmişse, derleme &mdash; kod kapsamı analizinden atlanır. Kod kapsamı analizi bu tür derlemelerde gerçekleştirilene bir işlemdir.

Çözüm &mdash; İyileştirmeyi kapatın ve yeni bir derleme kullanın.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kod yönetilen (.NET) veya yerel (C++) kodu değilse

Analiz &mdash; Bazı testleri yönetilen veya C++ kodu üzerinde çalıştırarak doğrulayın.

Açıklama &mdash; Kod kapsamı analizi Visual Studio yönetilen ve yerel (C++) kodda kullanılabilir. Üçüncü taraf araçlarla çalışıyorsanız, kodun bir veya hepsi farklı bir platformda yürütülür.

Çözüm &mdash; Yok.

### <a name="assembly-has-been-installed-by-ngen"></a>NGen tarafından yüklenen derleme

Analiz &mdash; Derlemenin yerel görüntü önbelleğinden yüklenmemiş olduğunu doğrulayın.

Açıklama &mdash; Performans nedenleriyle yerel görüntü derlemeleri çözümlanmaz. Daha fazla bilgi için [ bkz.Ngen.exe (Yerel Görüntü Oluşturucu)](/dotnet/framework/tools/ngen-exe-native-image-generator).

Çözüm &mdash; Derlemenin bir MSIL sürümünü kullanın. NGen ile işlemeyin.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Hatalı sözdizimi ile özelleştirilmiş .runsettings dosyası

Analiz &mdash; Özel bir *.runsettings* dosyası kullanıyorsanız söz dizimi hatası içeriyor olabilir. Kod kapsamı çalıştırlanmaz ve test çalıştırması sonunda kod kapsamı penceresi açılmaz veya eski sonuçlar gösterilir.

Açıklama &mdash; Kod kapsamı seçeneklerini yapılandırmak için birim testlerinizi özel bir *.runsettings* dosyasıyla çalıştırabilirsiniz. Bu seçenek size dosyaları eklemeyi veya çıkarmayı sağlar. Daha fazla bilgi için [bkz. Kod kapsamı analizini özelleştirme.](../test/customizing-code-coverage-analysis.md)

Çözüm &mdash; Olası iki hata türü vardır:

- **XML hatası**

     *.runsettings dosyasını* Visual Studio XML düzenleyicisinde açın. Hata göstergelerine bakın.

- **Normal ifade hatası**

  Dosyadaki her dize bir düzenli ifadedir. Hataların her birini gözden geçirme ve özellikle şunları gözden geçirme:

  - Eşleşmeyen parantezler (...) veya kaçışsız parantezler \\ (... \\ ). Arama dizisinde parantezleri eşleştirmek istiyorsanız, atlatmak gerekir. Örneğin, bir işlevle eşleşmek için şunları kullanın: `.*MyFunction\(double\)`

  - İfadenin başına yıldız veya artı koyun. Herhangi bir karakter dizesiyle eşleşmek için nokta ve ardından yıldız işareti kullanın: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Yanlış istisnalarla özelleştirilmiş .runsettings dosyası

Analiz &mdash; Özel bir *.runsettings dosyası kullanıyorsanız,* bunun derlemenizi de içerir.

Açıklama &mdash; Kod kapsamı seçeneklerini yapılandırmak için birim testlerinizi özel bir *.runsettings* dosyasıyla çalıştırabilirsiniz. Bu seçenek size dosyaları eklemeyi veya çıkarmayı sağlar. Daha fazla bilgi için [bkz. Kod kapsamı analizini özelleştirme.](../test/customizing-code-coverage-analysis.md)

Çözüm &mdash; `Include` *.runsettings* dosyasındaki tüm düğümleri kaldırın ve ardından tüm `Exclude` düğümleri kaldırın. Bu problemi çözdüyse, bunları aşamalar halinde yerleştirin.

DataCollectors düğümünün Kod Kapsamını belirttiğinden emin olun. Bunu Kod kapsamı analizini [özelleştirme'de yer alan örnekle karşılaştırın.](../test/customizing-code-coverage-analysis.md)

## <a name="some-code-is-always-shown-as-not-covered"></a>Bazı kodlar her zaman kapsandığı gibi gösterilmez

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>İzlemeden önce yerel DLL'lerdeki kodun başlatılması

Analiz Statik olarak bağlı yerel kodda, başlatma işlevinin dllMain ve çağıran kodun bir kısmı bazen kod yürütülse bile &mdash; kapslanmaz olarak gösterilir. 

Açıklama &mdash; Kod kapsamı aracı, uygulama çalışmaya başlamadan hemen önce bir derlemeye ölçüm eklemeyle çalışır. Önceden yüklenen derlemelerde, **DllMain'de** başlatma kodu derleme yüklenir yüklenmez ve uygulama çalıştırılamadan önce yürütülür. Bu kod, genellikle statik olarak yüklenen derlemeler için geçerli olan kapsamın içinde değildir.

Çözüm &mdash; Yok.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kapsamını kullanarak ne kadar kodun test edildiğini belirleme](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
