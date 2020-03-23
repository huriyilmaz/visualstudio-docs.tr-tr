---
title: Kod Kapsamı Sorunlarını Giderme
ms.date: 11/04/2016
ms.topic: troubleshooting
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bd70394262a2dd19ebf32f57549b9d2b3e8ee92a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565981"
---
# <a name="troubleshoot-code-coverage"></a>Kod kapsamı sorunlarını giderme

Visual Studio'daki kod kapsamı çözümleme aracı, yerel ve yönetilen derlemeler *(.dll* veya *.exe* dosyaları) için veri toplar. Ancak, bazı durumlarda, **Kod Kapsamı Sonuçları** penceresi "Oluşturulan Boş sonuçlar: ..." benzer bir hata görüntüler. Boş sonuçlar alabildiğinizin çeşitli nedenleri vardır. Bu makale, bu sorunları çözmenize yardımcı olur.

## <a name="what-you-should-see"></a>Görmeniz gereken

**Test** menüsünde bir **Çözüm kodu kapsamı** komutu seçerseniz ve yapı ve testler başarılı bir şekilde çalışırsa, Kod **Kapsamı** penceresinde bir sonuç listesini görmeniz gerekir. Ayrıntıları görmek için öğeleri genişletmeniz gerekebilir.

![Boyama ile kod kapsamı sonuçları](../test/media/codecoverage1.png)

Daha fazla bilgi için [bkz.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Sonuçları ya da eski sonuçları görmek için olası nedenler

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Visual Studio'nun doğru sürümüne sahip misiniz?

Visual Studio Atılgan'a ihtiyacın var.

### <a name="no-tests-were-executed"></a>Hiçbir sınama yürütülemedi

Analiz&mdash;Çıkış pencerenizi kontrol edin. Açılan **listeden Çıktıyı Göster'de** **Testleri**seçin. Herhangi bir uyarı veya hatanın günlüğe kaydedilip kaydedilmediğine bakın.

Açıklama&mdash;Kodu kapsama çözümlemesi testler çalışırken yapılır. Testler çalıştırıldığında sadece belleğe yüklenen derlemeleri içerir. Testlerin hiçbiri yürütülmezse, kod kapsamının rapor ediletilen bir şey yok.

Test&mdash;Gezgini'nde Çözüm, testlerin başarılı bir şekilde çalıştırDığını doğrulamak için **Tümünü Çalıştır'ı** seçin. **Analyze Code Coverage'ı**kullanmadan önce hataları düzeltin.

### <a name="youre-looking-at-a-previous-result"></a>Önceki sonuca bakıyorsunuz

Testlerinizi değiştirip yeniden çalıştırdığınızda, önceki kod kapsamı sonucu, bu eski çalıştırmadaki kod boyama da dahil olmak üzere görünmeye devam edebilir.

1. **Kod Kapsamını Çözümle'yi**Çalıştır.

2. **Kod Kapsamı Sonuçları** penceresinde belirlenen en son sonucu seçtiğinizden emin olun.

### <a name="pdb-symbol-files-are-unavailable"></a>.pdb (simge) dosyaları kullanılamaz

Çözümleme&mdash;Hedef klasörünü derle (genellikle *bin\debug)* açın ve her derleme için *.dll* veya *.exe* dosyasıyla aynı dizinde bir *.pdb* dosyası olduğunu doğrulayın.

Açıklama&mdash;Kod kapsama altyapısı, her derlemenin test çalışması sırasında erişilebilir ilişkili *.pdb* dosyasına sahip olduğunu gerektirir. Belirli bir derleme için *.pdb* dosyası yoksa, derleme çözümlenmez.

*.pdb* dosyası *.dll* veya *.exe* dosyalarıyla aynı yapıdan oluşturulmalıdır.

Çözünürlük&mdash;Yapı ayarlarınızın *.pdb* dosyasını oluşturduğundan emin olun. Proje oluşturulurken *.pdb* dosyaları güncelleştirilmezse, proje özelliklerini açın, **Yapı** sayfasını seçin, **Gelişmiş'i**seçin ve **Hata Ayıklama Bilgilerini**inceleyin.

C++ projeleri için, oluşturulan .pdb dosyalarının tam hata ayıklama bilgilerine sahip olduğundan emin olun. Proje özelliklerini açın ve **Bağlantı** > **Hata Ayıklama**Oluşturma Hata > **Ayıklama Bilgisini** **paylaşma ve yayımlamak için en iyi duruma getirilmiş Hata Ayıklama Bilgileri (/DEBUG:FULL) olarak**ayarladığını doğrulayın.

*.pdb* ve *.dll* veya *.exe* dosyaları farklı yerlerdeyse, *.pdb* dosyasını aynı dizine kopyalayın. Kod kapsama altyapısının başka bir konumda *.pdb* dosyalarını aramak için yapılandırılabilir. Daha fazla bilgi için [kod kapsamı çözümlemesi özelleştir'e](../test/customizing-code-coverage-analysis.md)bakın.

### <a name="use-an-instrumented-or-optimized-binary"></a>Enstrümantmalı veya optimize edilmiş ikili

Analiz&mdash;İkili profil güdümlü optimizasyon gibi gelişmiş optimizasyon herhangi bir biçimde uğramıştır, ya da *vsinstr.exe* veya *vsperfmon.exe*gibi bir profil oluşturma aracı tarafından enstrümante olup olmadığını belirleyin.

Açıklama&mdash;Bir derleme zaten başka bir profil oluşturma aracı tarafından enstrümante veya en iyi duruma getirilmişse, derleme kod kapsamı çözümlemesi atlanır. Bu tür derlemelerde kod kapsamı çözümlemesi yapılamaz.

Çözünürlük&mdash;Optimizasyonu kapatın ve yeni bir yapı kullanın.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kod yönetilen (.NET) veya yerel (C++) kodu değilse

Çözümleme&mdash;Yönetilen veya C++ kodu üzerinde bazı testler çalıştırdığınızı doğrulayın.

Visual&mdash;Studio'da Açıklama Kodu kapsama analizi yalnızca yönetilen ve yerel (C++) kodda kullanılabilir. Üçüncü taraf araçlarıyla çalışıyorsanız, kodun bir kısmı veya tümü farklı bir platformda yürütülebilir.

Çözünürlük&mdash;Yok kullanılabilir.

### <a name="assembly-has-been-installed-by-ngen"></a>NGen tarafından yüklenen derleme

Çözümleme&mdash;Derlemenin yerel görüntü önbelleğinden yüklenmediğini doğrulayın.

Açıklama&mdash;Performans nedenleriyle, yerel görüntü derlemeleri çözümlenmez. Daha fazla bilgi için [Bkz. Ngen.exe (Native Image Generator)](/dotnet/framework/tools/ngen-exe-native-image-generator).

Çözünürlük&mdash;Derlemenin MSIL sürümünü kullanın. NGen'le işlemeyin.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Hatalı sözdizimi ile özelleştirilmiş .runsettings dosyası

Çözümleme&mdash;Özel bir *.runsettings* dosyası kullanıyorsanız, sözdizimi hatası içerebilir. Kod kapsamı çalıştırılmaz ve test çalışmasının sonunda kod kapsamı penceresi açılmaz veya eski sonuçları gösterir.

Açıklama&mdash;Kod kapsama seçeneklerini yapılandırmak için birim testlerinizi özel bir *.runsettings* dosyasıyla çalıştırabilirsiniz. Bu seçenek size dosyaları eklemeyi veya çıkarmayı sağlar. Daha fazla bilgi için [kod kapsamı çözümlemesi özelleştir'e](../test/customizing-code-coverage-analysis.md)bakın.

Çözünürlük&mdash;İki olası hata türü vardır:

- **XML hatası**

     Visual Studio XML düzenleyicisinde *.runsettings* dosyasını açın. Hata göstergelerine bakın.

- **Normal ifade hatası**

  Dosyadaki her dize bir düzenli ifadedir. Hatalar için her birini gözden geçirin ve özellikle şu nabakını yapın:

  - Uyumsuz parantez (...) veya kaçamayan parantezler \\(... \\). Arama dizisinde parantezleri eşleştirmek istiyorsanız, atlatmak gerekir. Örneğin, bir işlev kullanımı maç için:`.*MyFunction\(double\)`

  - İfadenin başına yıldız veya artı koyun. Herhangi bir karakter dizesini eşleştirmek için, bir nokta ve ardından yıldız işareti kullanın:`.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Yanlış istisnalarla özelleştirilmiş .runsettings dosyası

Analiz&mdash;Özel bir *.runsettings* dosyası kullanıyorsanız, derlemenizi içerdiğinden emin olun.

Açıklama&mdash;Kod kapsama seçeneklerini yapılandırmak için birim testlerinizi özel bir *.runsettings* dosyasıyla çalıştırabilirsiniz. Bu seçenek size dosyaları eklemeyi veya çıkarmayı sağlar. Daha fazla bilgi için [kod kapsamı çözümlemesi özelleştir'e](../test/customizing-code-coverage-analysis.md)bakın.

Çözünürlük&mdash; *.runsettings* dosyasındaki tüm `Exclude` `Include` düğümleri kaldırın ve ardından tüm düğümleri kaldırın. Bu problemi çözdüyse, bunları aşamalar halinde yerleştirin.

DataCollectors düğümünün Kod Kapsamını belirttiğinden emin olun. [Kod kapsama çözümlemesi özelleştir'deki](../test/customizing-code-coverage-analysis.md)örnekle karşılaştırın.

## <a name="some-code-is-always-shown-as-not-covered"></a>Bazı kodlar her zaman kapsandığı gibi gösterilmez

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>İzlemeden önce yerel DLL'lerdeki kodun başlatılması

Çözümleme&mdash;Statik olarak bağlı yerel kodda, başlatma işlevi **DllMain'in** bir parçası ve kod yürütülmüş olsa bile bazen kapsam dışında olarak gösterilir.

Açıklama&mdash;Kod kapsamı aracı, uygulama çalışmaya başlamadan hemen önce bir derlemeye enstrümantasyon ekleyerek çalışır. Önceden yüklenen herhangi bir derlemede, **DllMain'deki** başlatma kodu montaj yüklenir yüklenmez ve uygulama çalışmadan önce yürütür. Bu kod genellikle statik olarak yüklenen derlemeler için geçerli olan kapsam kapsamında değil gibi görünüyor.

Çözünürlük&mdash;Yok.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kapsamını kullanarak ne kadar kodun test edildiğini belirleme](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
