---
title: Kod Kapsamı Sorunlarını Giderme
ms.date: 11/04/2016
ms.topic: troubleshooting
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 9a7e90310df3e9e2e73b653fdc651ba266e679ae
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659875"
---
# <a name="troubleshoot-code-coverage"></a>Kod kapsamı sorunlarını giderme

Visual Studio 'daki kod kapsamı çözümleme aracı, yerel ve yönetilen derlemeler ( *. dll* veya *. exe* dosyaları) için veri toplar. Ancak, bazı durumlarda, **kod kapsamı sonuçları** penceresi "boş sonuçlar oluşturuldu:...." şuna benzer bir hata görüntüler. Boş sonuçları elde etmenize neden olan çeşitli nedenler vardır. Bu makale, bu sorunları çözmenize yardımcı olur.

## <a name="what-you-should-see"></a>Görmeniz gereken

**Test** menüsünde **kod kapsamını çözümle** komutunu seçerseniz ve derleme ve testler başarıyla çalışıyorsa, **kod kapsamı** penceresinde sonuçların bir listesini görmeniz gerekir. Ayrıntıları görmek için öğeleri genişletmeniz gerekebilir.

![Renklendirme ile kod kapsamı sonuçları](../test/media/codecoverage1.png)

Daha fazla bilgi için bkz. kod [kapsamını kullanarak ne kadar kodun test edildiğini belirleme](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Sonuçları ya da eski sonuçları görmek için olası nedenler

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Visual Studio'nun doğru sürümüne sahip misiniz?

Visual Studio Enterprise gerekiyor.

### <a name="no-tests-were-executed"></a>Hiçbir sınama yürütülemedi

Çıkış pencerenizin Analizi &mdash;Check. **Çıktıyı göster** açılan listesinden **testler**' i seçin. Herhangi bir uyarı veya hatanın günlüğe kaydedilip kaydedilmediğine bakın.

Açıklama &mdash;Code testler çalışırken kapsam analizi yapılır. Testler çalıştırıldığında sadece belleğe yüklenen derlemeleri içerir. Testlerin hiçbiri yürütülürse, kod kapsamı raporlamak için bir şey yoktur.

Çözüm &mdash;In test Gezgini, testlerin başarıyla çalıştığını doğrulamak için **Tümünü Çalıştır** ' ı seçin. **Kod kapsamını çözümle**özelliğini kullanmadan önce tüm hataları düzeltin.

### <a name="youre-looking-at-a-previous-result"></a>Önceki sonuca bakıyorsunuz

Testlerinizi değiştirirken ve yeniden çalıştırdığınızda, bu eski çalıştırmasının kod renklendirme da dahil olmak üzere önceki bir kod kapsamı sonucu hala görünür olabilir.

1. **Kod kapsamını analiz et**' i çalıştırın.

2. **Kod kapsamı sonuçları** penceresinde en son sonuç kümesini seçtiğinizden emin olun.

### <a name="pdb-symbol-files-are-unavailable"></a>.pdb (simge) dosyaları kullanılamaz

Analiz &mdash;Open hedef klasörü (genellikle *bin\Debug*) ve her derleme için, *. dll* veya *. exe* dosyası ile aynı dizinde bir *. pdb* dosyası olduğunu doğrulayın.

Açıklama &mdash;The kod kapsamı altyapısı, test çalıştırması sırasında her derlemenin ilişkili *. pdb* dosyasını erişilebilir olmasını gerektirir. Belirli bir derleme için *. pdb* dosyası yoksa, derleme çözümlenmez.

*. Pdb* dosyası *. dll* veya *. exe* dosyalarıyla aynı derlemeden oluşturulmalıdır.

Çözüm, derleme ayarlarınızın *. pdb* dosyasını üretdiğinizden emin &mdash;Make. Proje oluşturulduğunda *. pdb* dosyaları güncellenmemişse, proje özelliklerini açın, **derleme** sayfasını seçin, **Gelişmiş**' i seçin ve **hata ayıklama bilgilerini**inceleyin.

Projeler C++ için, oluşturulan. pdb dosyalarının tam hata ayıklama bilgilerine sahip olduğundan emin olun. Proje özelliklerini açın ve hata**ayıklama  >  hata ayıklama** **bilgisi oluştur** ** > ,** **Paylaşım ve yayımlama için iyileştirilmiş hata ayıklama bilgileri oluşturmak üzere ayarlandığını doğrulayın (/Debug: Full)** .

*. Pdb* ve *. dll* veya *. exe* dosyaları farklı yerlerde ise, *. pdb* dosyasını aynı dizine kopyalayın. Ayrıca, başka bir konumdaki *. pdb* dosyalarını aramak için kod kapsamı altyapısını yapılandırmak mümkündür. Daha fazla bilgi için bkz. [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

### <a name="use-an-instrumented-or-optimized-binary"></a>Belgelenmiş veya iyileştirilmiş bir ikili kullanın

Analiz &mdash;Determine, ikili dosyanın profil temelli Iyileştirme veya *vsinstr. exe* ya da *VSPerfMon. exe*gibi bir profil oluşturma aracı tarafından işaretlenmiş herhangi bir biçimde gelişmiş iyileştirmesi varsa analiz.

Açıklama &mdash;If bir derleme zaten başka bir profil oluşturma aracı tarafından işaretlenmiş veya iyileştirildi, derleme kod kapsamı analizinden çıkarılır. Bu tür derlemelerde kod kapsamı Analizi gerçekleştirilemez.

Çözüm &mdash;Switch en iyi duruma getirme ve yeni bir derleme kullanma.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kod yönetilen (.NET) veya yerel (C++) kodu değilse

Analiz, yönetilen veya C++ kod üzerinde bazı testler çalıştırdığınızı &mdash;Verify.

Açıklama &mdash;Code Visual Studio 'da kapsam Analizi yalnızca yönetilen ve yerel (C++) kodda kullanılabilir. Üçüncü taraf araçlarla çalışıyorsanız, kodun bir kısmı veya tümü farklı bir platformda yürütülemeyebilir.

Çözüm &mdash;None kullanılabilir.

### <a name="assembly-has-been-installed-by-ngen"></a>NGen tarafından yüklenen derleme

Analiz, derlemenin yerel görüntü önbelleğinden yüklenmediğini &mdash;Verify.

Açıklama &mdash;For performans nedenleri, yerel görüntü derlemeleri çözümlenmez. Daha fazla bilgi için bkz. [Ngen. exe (yerel görüntü Oluşturucu)](/dotnet/framework/tools/ngen-exe-native-image-generator).

Çözümleme, derlemenin MSIL sürümünü &mdash;Use. NGen ile işleme yapmayın.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Hatalı sözdizimi ile özelleştirilmiş .runsettings dosyası

Analysis &mdash;If özel bir *. runsettings* dosyası kullanıyorsunuz, bu bir sözdizimi hatası içeriyor olabilir. Kod kapsamı çalıştırılmaz ve kod kapsamı penceresi Test çalıştırmasının sonunda açılmaz ya da eski sonuçları gösterir.

Açıklama &mdash;You, kod kapsamı seçeneklerini yapılandırmak için birim testlerinizi özel bir *. runsettings* dosyası ile çalıştırabilir. Bu seçenek size dosyaları eklemeyi veya çıkarmayı sağlar. Daha fazla bilgi için bkz. [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

Çözüm &mdash;There iki olası hata türüdür:

- **XML hatası**

     Visual Studio XML düzenleyicisinde *. runsettings* dosyasını açın. Hata göstergelerine bakın.

- **Normal ifade hatası**

  Dosyadaki her dize bir düzenli ifadedir. Her birini hatalar için gözden geçirin ve belirli bir görünüm:

  - Eşleşmeyen parantezler (...) veya kaçışsız parantezler \\ (... \\). Arama dizisinde parantezleri eşleştirmek istiyorsanız, atlatmak gerekir. Örneğin, bir işlev kullanımıyla eşleştirmek için: `.*MyFunction\(double\)`

  - İfadenin başına yıldız veya artı koyun. Herhangi bir karakter dizesini eşleştirmek için, bir nokta ve bir yıldız işareti kullanın: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Yanlış istisnalarla özelleştirilmiş .runsettings dosyası

Analiz &mdash;If özel bir *. runsettings* dosyası kullandığınız için derlemenizi içerdiğinden emin olun.

Açıklama &mdash;You, kod kapsamı seçeneklerini yapılandırmak için birim testlerinizi özel bir *. runsettings* dosyası ile çalıştırabilir. Bu seçenek size dosyaları eklemeyi veya çıkarmayı sağlar. Daha fazla bilgi için bkz. [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

Çözüm, *. runsettings* dosyasındaki tüm `Include` düğümlerini &mdash;Remove ve ardından tüm `Exclude` düğümlerini kaldırır. Bu problemi çözdüyse, bunları aşamalar halinde yerleştirin.

DataCollectors düğümünün Kod Kapsamını belirttiğinden emin olun. [Kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md)içindeki örnekle karşılaştırın.

## <a name="some-code-is-always-shown-as-not-covered"></a>Bazı kodlar her zaman kapsandığı gibi gösterilmez

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>İzlemeden önce yerel DLL'lerdeki kodun başlatılması

Analiz &mdash;In statik olarak bağlı yerel kod, **DllMain** başlatma işlevinin bir parçası ve çağrı yaptığı kod, bazen kod yürütülene rağmen kapsanmayan olarak gösterilmemiştir.

Açıklama &mdash;The kod kapsamı Aracı, uygulamanın çalışmaya başlamasından hemen önce bir derlemeye izleme ekleyerek çalışır. Önceden yüklenen herhangi bir derlemede, **DllMain** 'deki başlatma kodu, derleme yüklenir almaz ve uygulama çalışmadan önce yürütülür. Bu kod, genellikle statik olarak yüklenen derlemeler için geçerli olan kapsanmayan şekilde görünür.

Çözüm &mdash;None.

## <a name="see-also"></a>Ayrıca bkz.

- [Ne kadar kodun test edildiğini öğrenmek için kod kapsamını kullanın](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
