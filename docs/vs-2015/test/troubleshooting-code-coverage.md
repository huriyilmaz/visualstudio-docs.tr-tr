---
title: Kod kapsamı sorunlarını giderme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 26de91b8-45e3-4976-a20e-a3bd1942ddcb
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bf21286143b2b9543c834f00ed31ddaa4cef63
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660374"
---
# <a name="troubleshooting-code-coverage"></a>Kod Kapsamı Sorunlarını Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'daki kod kapsamı analiz aracı yerel ve yönetilen (.ddl veya .exe dosyaları) derlemeler için verileri toplar. Ancak, bazı durumlarda, kod kapsamı sonuçları penceresi "boş sonuçlar oluşturuldu:...." şuna benzer bir hata görüntüler. Bunun birkaç olası nedeni olabilir. Bu konu bu sorunların giderilmesine yardımcı olmak amacıyla hazırlanmıştır.

## <a name="what-you-should-see"></a>Görmeniz gereken
 Test menüsünde **kod kapsamını çözümle** komutunu seçerseniz ve derleme ve testler başarıyla çalışıyorsa, kod kapsamı penceresinde sonuçların bir listesini görmeniz gerekir. Ayrıntıları görmek için öğeleri genişletmeniz gerekebilir.

 ![Renklendirme ile kod kapsamı sonuçları](../test/media/codecoverage1.png "CodeCoverage1")

 Daha fazla bilgi için bkz. kod [kapsamını kullanarak ne kadar kodun test edildiğini belirleme](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Sonuçları ya da eski sonuçları görmek için olası nedenler

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Visual Studio'nun doğru sürümüne sahip misiniz?
 Visual Studio Enterprise gerekiyor.

### <a name="no-tests-were-executed"></a>Hiçbir sınama yürütülemedi
 Analiz, çıktı pencerenizi kontrol edin. **Çıktıyı göster** açılan listesinden **testler**' i seçin. Herhangi bir uyarı veya hatanın günlüğe kaydedilip kaydedilmediğine bakın.

 Açıklama kod kapsamı analizi, testler çalışırken yapılır. Testler çalıştırıldığında sadece belleğe yüklenen derlemeleri içerir. Testlerin hiçbiri çalıştırılmazsa kod kapsamı raporunda hiçbir şey olmaz.

 Test Gezgini 'Nde çözüm, testlerin başarıyla çalıştığını doğrulamak için **Tümünü Çalıştır** ' ı seçin. **Kod kapsamını çözümle**özelliğini kullanmadan önce tüm hataları düzeltin.

### <a name="youre-looking-at-a-previous-result"></a>Bir önceki sonucu arıyorsunuz
 Testleri değiştirdiğinizde ve yeniden çalıştırdığınızda bir önceki kod kapsamı sonucu eski çalıştırmadan kod renklendirme dahil görünebilir.

1. Kod Kapsamı Çözümlemeyi Çalıştırın.

2. En son sonuç kümesini Kod Kapsamı sonuçları penceresinde seçtiğinizden emin olun.

### <a name="pdb-symbol-files-are-unavailable"></a>.pdb (simge) dosyaları kullanılamaz
 Analiz derleme hedefi klasörünü açın (genellikle bin\Debug) ve her derleme için. dll veya. exe dosyası ile aynı dizinde bir. pdb dosyası olduğunu doğrulayın.

 Açıklama kod kapsamı altyapısı, test çalıştırması sırasında her derlemenin ilişkili. pdb dosyasını erişilebilir olmasını gerektirir. Belirli bir derleme için .pdb dosyası yoksa, o dosya analiz edilmez.

 .pdb dosyası .dll veya .exe dosyasıyla birlikte aynı derleme sırasında oluşturulmalıdır.

 Çözüm, derleme ayarlarınızın. pdb dosyasını oluşturmasını sağlayın. Proje oluşturulduğunda. pdb dosyaları güncellenmemişse, proje özelliklerini açın, **derleme** sayfasını seçin, **Gelişmiş** ' i seçin ve **hata ayıklama bilgilerini**inceleyin.

 .pdb ve .dll veya .exe dosyaları farklı yerlerdeyse, .pdb dosyasını aynı dizine kopyalayın. Kod kapsamı motorunu .pdb dosyalarını başka bir konumda aramak için yapılandırmak mümkündür. Daha fazla bilgi için bkz. [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

### <a name="using-an-instrumented-or-optimized-binary"></a>Araçlı ya da optimize edilmiş ikili kullanma
 Analiz, ikili dosyanın profil temelli Iyileştirme veya vsinstr.exe ya da vsperfmon.exe gibi bir profil oluşturma aracı tarafından işaretlenmiş gelişmiş iyileştirmede herhangi bir biçime sahip olup olmadığını belirleme.

 Açıklama bir derleme başka bir profil oluşturma aracı tarafından zaten belgelenmiş veya iyileştirilmişse, derleme kod kapsamı analizinden çıkarılır.

 Kod kapsamı analizi bu tür derlemelerde gerçekleştirilmez.

 Çözüm geçiş iyileştirmesi ve yeni bir yapı kullanın.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kod yönetilen (.NET) veya yerel (C++) kodu değilse
 Analiz, yönetilen veya C++ kodu üzerinde bazı testler çalıştırdığınızı doğrulayın.

 Açıklama Visual Studio 'da kod kapsamı Analizi yalnızca yönetilen ve yerel (C++) kodda kullanılabilir. Üçüncü parti araçlar kullanıyorsanız, kodunuzun bazı veya tamamı farklı bir platformda çalışabilir.

 Geçici çözüm yok.

### <a name="assembly-has-been-installed-by-ngen"></a>NGen tarafından yüklenen derleme
 Analiz, derlemenin yerel görüntü önbelleğinden yüklenmediğini doğrulayın.

 Performans nedenleriyle Ilgili açıklama, yerel görüntü derlemeleri çözümlenmez. Daha fazla bilgi için bkz. [Ngen.exe (yerel görüntü Oluşturucu)](https://msdn.microsoft.com/library/44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66).

 Çözüm derlemenin MSIL sürümünü kullanır. NGen ile işlemeyin.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Hatalı sözdizimi ile özelleştirilmiş .runsettings dosyası
 Analiz özel bir. runsettings dosyası kullanıyorsanız, sözdizimi hatası içerebilir.

 Kod kapsamı içindeki sonuçlardır. Kod kapsamı penceresi test sonunda açılmaz ya da eski sonuçları gösterir.

 Açıklama kod kapsamı seçeneklerini yapılandırmak için birim testlerinizi özel bir. runsettings dosyası ile çalıştırabilirsiniz. Bu seçenek size dosyaları eklemeyi veya çıkarmayı sağlar. Daha fazla bilgi için bkz. [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

 Çözüm iki olası hata türü vardır:

- **XML hatası**

     .runsettings dosyasını Visual Studio XML düzenleyicisinde açın. Hata göstergelerine bakın.

- **Normal ifade hatası**

  Dosyadaki her dize bir düzenli ifadedir. Her birini hatalar için gözden geçirin ve bu belirtilen için bakın:

  - Eşleşmeyen parantezler (...) veya kaçışsız parantezler \\ (... \\ ). Arama dizisinde parantezleri eşleştirmek istiyorsanız, atlatmak gerekir. Örneğin, bir işlev kullanımıyla eşleştirmek için: `.*MyFunction\(double\)`

  - İfadenin başına yıldız veya artı koyun. Herhangi bir karakter dizesini eşleştirmek için bir nokta ve ardından bir yıldız işareti kullanın: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Yanlış istisnalarla özelleştirilmiş .runsettings dosyası
 Analiz özel bir. runsettings dosyası kullanıyorsanız, derlemenizi içerdiğinden emin olun.

 Açıklama kod kapsamı seçeneklerini yapılandırmak için birim testlerinizi özel bir. runsettings dosyası ile çalıştırabilirsiniz. Bu seçenek size dosyaları eklemeyi veya çıkarmayı sağlar. Daha fazla bilgi için bkz. [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

 Çözüm `Include` . runsettings dosyasındaki tüm düğümleri kaldırın ve tüm `Exclude` düğümleri kaldırın. Bu problemi çözdüyse, bunları aşamalar halinde yerleştirin.

 DataCollectors düğümünün Kod Kapsamını belirttiğinden emin olun. [Kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md)içindeki örnekle karşılaştırın.

## <a name="some-code-is-always-shown-as-not-covered"></a>Bazı kodlar her zaman kapsandığı gibi gösterilmez

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>İzlemeden önce yerel DLL'lerdeki kodun başlatılması
 Statik olarak bağlı yerel kodda analiz, **DllMain** başlatma işlevinin bir parçası ve çağrı yaptığı kod, bazen kod yürütülene rağmen kapsanmayan olarak gösterilmemiştir.

 Açıklama kod kapsamı Aracı, uygulamanın çalışmaya başlamasından hemen önce bir derlemeye izleme ekleyerek çalışır. Bu andan önce yüklenen herhangi bir derlemede, **DllMain** 'deki başlatma kodu, derleme yüklenir almaz ve uygulama çalışmadan önce yürütülür. Kod kapsanmayacak gibi görünür.

 Genellikle, bu statik olarak yüklenen derlemeler için geçerlidir.

 Çözüm yok.

## <a name="see-also"></a>Ayrıca Bkz.
 [Ne Kadar Kodun Test Edildiğini Belirlemek için Kod Kapsamını Kullanma](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
