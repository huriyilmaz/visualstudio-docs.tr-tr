---
title: Kod Kapsamı Sorunlarını Giderme
ms.date: 03/31/2020
ms.topic: troubleshooting
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 39d5d54021e7b8286bd653941d233a73bcf8cfb4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80528005"
---
# <a name="troubleshoot-code-coverage"></a>Kod kapsamı sorunlarını giderme

Visual Studio 'daki kod kapsamı çözümleme aracı, yerel ve yönetilen derlemeler (*. dll* veya *. exe* dosyaları) için veri toplar. Ancak, bazı durumlarda, **kod kapsamı sonuçları** penceresi "boş sonuçlar oluşturuldu:...." şuna benzer bir hata görüntüler. Boş sonuçları elde etmenize neden olan çeşitli nedenler vardır. Bu makale, bu sorunları çözmenize yardımcı olur.

## <a name="what-you-should-see"></a>Görmeniz gereken

**Test** menüsünde **kod kapsamını çözümle** komutunu seçerseniz ve derleme ve testler başarıyla çalışıyorsa, **kod kapsamı** penceresinde sonuçların bir listesini görmeniz gerekir. Ayrıntıları görmek için öğeleri genişletmeniz gerekebilir.

::: moniker range=">=vs-2019"
![Renklendirme ile kod kapsamı sonuçları](../test/media/vs-2019/codecoverage1.png)
::: moniker-end
::: moniker range="vs-2017"
![Renklendirme ile kod kapsamı sonuçları](../test/media/codecoverage1.png)
::: moniker-end

Daha fazla bilgi için bkz. kod [kapsamını kullanarak ne kadar kodun test edildiğini belirleme](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Sonuçları ya da eski sonuçları görmek için olası nedenler

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Visual Studio'nun doğru sürümüne sahip misiniz?

Visual Studio Enterprise gerekiyor.

### <a name="no-tests-were-executed"></a>Hiçbir sınama yürütülemedi

Analiz, &mdash; çıktı pencerenizi kontrol edin. **Çıktıyı göster** açılan listesinden **testler**' i seçin. Herhangi bir uyarı veya hatanın günlüğe kaydedilip kaydedilmediğine bakın.

Açıklama &mdash; kod kapsamı analizi, testler çalışırken yapılır. Testler çalıştırıldığında sadece belleğe yüklenen derlemeleri içerir. Testlerin hiçbiri yürütülürse, kod kapsamı raporlamak için bir şey yoktur.

&mdash;Test Gezgini 'nde çözüm, testlerin başarıyla çalıştığını doğrulamak Için **Tümünü Çalıştır** ' ı seçin. **Kod kapsamını çözümle**özelliğini kullanmadan önce tüm hataları düzeltin.

### <a name="youre-looking-at-a-previous-result"></a>Önceki sonuca bakıyorsunuz

Testlerinizi değiştirirken ve yeniden çalıştırdığınızda, bu eski çalıştırmasının kod renklendirme da dahil olmak üzere önceki bir kod kapsamı sonucu hala görünür olabilir.

1. **Kod kapsamını analiz et**' i çalıştırın.

2. **Kod kapsamı sonuçları** penceresinde en son sonuç kümesini seçtiğinizden emin olun.

### <a name="pdb-symbol-files-are-unavailable"></a>.pdb (simge) dosyaları kullanılamaz

Analiz &mdash; derleme hedefi klasörünü açın (genellikle *bin\Debug*) ve her derleme için, *. dll* veya *. exe* dosyası ile aynı dizinde bir *. pdb* dosyası olduğunu doğrulayın.

Açıklama &mdash; kod kapsamı altyapısı, test çalıştırması sırasında her derlemenin ilişkili *. pdb* dosyasını erişilebilir olmasını gerektirir. Belirli bir derleme için *. pdb* dosyası yoksa, derleme çözümlenmez.

*. Pdb* dosyası *. dll* veya *. exe* dosyalarıyla aynı derlemeden oluşturulmalıdır.

Çözüm &mdash; , derleme ayarlarınızın *. pdb* dosyasını oluşturmasını sağlayın. Proje oluşturulduğunda *. pdb* dosyaları güncellenmemişse, proje özelliklerini açın, **derleme** sayfasını seçin, **Gelişmiş**' i seçin ve **hata ayıklama bilgilerini**inceleyin.

C++ projeleri için, oluşturulan. pdb dosyalarının tam hata ayıklama bilgilerine sahip olduğundan emin olun. Proje özelliklerini açın ve **bağlayıcı**hata  >  **ayıklama**  >  **hata ayıklama bilgileri oluştur** ' un, **Paylaşım ve yayımlama için iyileştirilmiş hata ayıklama bilgileri oluşturmak üzere ayarlandığını doğrulayın (/Debug: Full)**.

*. Pdb* ve *. dll* veya *. exe* dosyaları farklı yerlerde ise, *. pdb* dosyasını aynı dizine kopyalayın. Ayrıca, başka bir konumdaki *. pdb* dosyalarını aramak için kod kapsamı altyapısını yapılandırmak mümkündür. Daha fazla bilgi için bkz. [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

### <a name="use-an-instrumented-or-optimized-binary"></a>Belgelenmiş veya iyileştirilmiş bir ikili kullanın

Analiz &mdash; , ikili dosyanın profil temelli iyileştirme veya *vsinstr.exe* ya da *vsperfmon.exe*gibi bir profil oluşturma aracı tarafından işaretlenmiş gelişmiş iyileştirmede herhangi bir biçime sahip olup olmadığını belirleme.

Açıklama bir &mdash; derleme başka bir profil oluşturma aracı tarafından zaten belgelenmiş veya iyileştirilmişse, derleme kod kapsamı analizinden çıkarılır. Bu tür derlemelerde kod kapsamı Analizi gerçekleştirilemez.

Çözüm &mdash; geçiş iyileştirmesi ve yeni bir yapı kullanın.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kod yönetilen (.NET) veya yerel (C++) kodu değilse

Analiz &mdash; , yönetilen veya C++ kodu üzerinde bazı testler çalıştırdığınızı doğrulayın.

Açıklama &mdash; Visual Studio 'da kod kapsamı Analizi yalnızca yönetilen ve yerel (C++) kodda kullanılabilir. Üçüncü taraf araçlarla çalışıyorsanız, kodun bir kısmı veya tümü farklı bir platformda yürütülemeyebilir.

Geçici çözüm &mdash; yok.

### <a name="assembly-has-been-installed-by-ngen"></a>NGen tarafından yüklenen derleme

Analiz &mdash; , derlemenin yerel görüntü önbelleğinden yüklenmediğini doğrulayın.

&mdash;Performans nedenleriyle ilgili açıklama, yerel görüntü derlemeleri çözümlenmez. Daha fazla bilgi için bkz. [Ngen.exe (yerel görüntü Oluşturucu)](/dotnet/framework/tools/ngen-exe-native-image-generator).

Çözüm &mdash; DERLEMENIN MSIL sürümünü kullanır. NGen ile işleme yapmayın.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Hatalı sözdizimi ile özelleştirilmiş .runsettings dosyası

Analiz &mdash; özel bir *. runsettings* dosyası kullanıyorsanız, sözdizimi hatası içerebilir. Kod kapsamı çalıştırılmaz ve kod kapsamı penceresi Test çalıştırmasının sonunda açılmaz ya da eski sonuçları gösterir.

Açıklama &mdash; kod kapsamı seçeneklerini yapılandırmak için birim testlerinizi özel bir *. runsettings* dosyası ile çalıştırabilirsiniz. Bu seçenek size dosyaları eklemeyi veya çıkarmayı sağlar. Daha fazla bilgi için bkz. [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

Çözüm &mdash; iki olası hata türü vardır:

- **XML hatası**

     Visual Studio XML düzenleyicisinde *. runsettings* dosyasını açın. Hata göstergelerine bakın.

- **Normal ifade hatası**

  Dosyadaki her dize bir düzenli ifadedir. Her birini hatalar için gözden geçirin ve belirli bir görünüm:

  - Eşleşmeyen parantezler (...) veya kaçışsız parantezler \\ (... \\ ). Arama dizisinde parantezleri eşleştirmek istiyorsanız, atlatmak gerekir. Örneğin, bir işlev kullanımıyla eşleştirmek için: `.*MyFunction\(double\)`

  - İfadenin başına yıldız veya artı koyun. Herhangi bir karakter dizesini eşleştirmek için bir nokta ve ardından bir yıldız işareti kullanın: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Yanlış istisnalarla özelleştirilmiş .runsettings dosyası

Analiz &mdash; özel bir *. runsettings* dosyası kullanıyorsanız, derlemenizi içerdiğinden emin olun.

Açıklama &mdash; kod kapsamı seçeneklerini yapılandırmak için birim testlerinizi özel bir *. runsettings* dosyası ile çalıştırabilirsiniz. Bu seçenek size dosyaları eklemeyi veya çıkarmayı sağlar. Daha fazla bilgi için bkz. [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

Çözüm &mdash; `Include` *. runsettings* dosyasındaki tüm düğümleri kaldırın ve tüm `Exclude` düğümleri kaldırın. Bu problemi çözdüyse, bunları aşamalar halinde yerleştirin.

DataCollectors düğümünün Kod Kapsamını belirttiğinden emin olun. [Kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md)içindeki örnekle karşılaştırın.

## <a name="some-code-is-always-shown-as-not-covered"></a>Bazı kodlar her zaman kapsandığı gibi gösterilmez

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>İzlemeden önce yerel DLL'lerdeki kodun başlatılması

&mdash;Statik olarak bağlı yerel kodda analiz, **DllMain** başlatma işlevinin bir parçası ve çağrı yaptığı kod, bazen kod yürütülene rağmen kapsanmayan olarak gösterilmemiştir.

Açıklama &mdash; kod kapsamı Aracı, uygulamanın çalışmaya başlamasından hemen önce bir derlemeye izleme ekleyerek çalışır. Önceden yüklenen herhangi bir derlemede, **DllMain** 'deki başlatma kodu, derleme yüklenir almaz ve uygulama çalışmadan önce yürütülür. Bu kod, genellikle statik olarak yüklenen derlemeler için geçerli olan kapsanmayan şekilde görünür.

Çözüm &mdash; yok.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kapsamını kullanarak ne kadar kodun test edildiğini belirleme](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
