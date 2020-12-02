---
title: IntelliSense için bir C++ projesi yapılandırma
description: IntelliSense sorunlarını belirlemenize ve düzeltmenize yardımcı olması için Visual Studio IDE 'yi kullanarak IntelliSense 'in düzgün şekilde çalışmasını sağlamak üzere C++ projenizi el ile yapılandırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/08/2018
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 34be73203f5c1d01e4674e7892e0f89d4aae4816
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478802"
---
# <a name="configure-a-c-project-for-intellisense"></a>IntelliSense için bir C++ projesi yapılandırma

Bazı durumlarda, IntelliSense 'in düzgün şekilde çalışmasını sağlamak için C++ projenizi el ile yapılandırmanız gerekebilir. MSBuild projeleri için (. vcxproj dosyalarını temel alan), proje özelliklerindeki ayarları ayarlayabilirsiniz. MSBuild olmayan projeler için, projenin kök dizinindeki CppProperties.jsdosyadaki ayarları ayarlayabilirsiniz. Bazı durumlarda, IntelliSense 'in Makro tanımlarını anlamalarına yardımcı olmak için bir ipucu dosyası oluşturmanız gerekebilir. Visual Studio IDE, IntelliSense sorunlarını belirlemenize ve düzeltmenize yardımcı olur.

## <a name="single-file-intellisense"></a>Tek dosya IntelliSense

Bir projeye dahil olmayan bir dosyayı açtığınızda, Visual Studio bazı IntelliSense desteği sağlar ancak varsayılan olarak hiçbir hata dalgalı çizgiler gösterilmez. **Gezinti çubuğu** *çeşitli dosyalar* yazmazsa, büyük olasılıkla hatalı kod altında hata dalgalı çizgiler görmediğiniz veya bir Önişlemci makrosunun neden tanımlanmadığı açıklanmaktadır.

## <a name="check-the-error-list"></a>Hata Listesi denetleyin

Bir dosya tek dosya modunda açılmadığından ve IntelliSense düzgün çalışmıyorsa, denetlenecek ilk yer Hata Listesi penceresidir. Geçerli kaynak dosyanın tüm IntelliSense hatalarını tüm dahil edilen üstbilgi dosyalarıyla birlikte görmek için açılan listede **Oluştur + IntelliSense** ' i seçin:

![Hata Listesi 'de VC + + IntelliSense](media/vcpp-intellisense-error-list.png)

IntelliSense en fazla 1000 hata üretir. Kaynak dosyanın içerdiği üst bilgi dosyalarında 1000 üzerinde hata varsa, kaynak dosya kaynak dosyanın en başında yalnızca tek bir hata dalgalı çizgi gösterir.

## <a name="ensure-include-paths-are-correct"></a>#İnclude yollarının doğru olduğundan emin olun

### <a name="msbuild-projects"></a>MSBuild projeleri

Yapılarınızı Visual Studio IDE dışında çalıştırırsanız, yapılarınız başarılı oluyor ancak IntelliSense yanlış ise, komut satırlarınızın bir veya daha fazla yapılandırmanın proje ayarlarıyla eşitlenmesi mümkündür. **Çözüm Gezgini** ' de proje düğümüne sağ tıklayın ve tüm **#include** yollarının geçerli yapılandırma ve platform için doğru olduğundan emin olun. Yollar tüm yapılandırmalarda ve platformlarda aynıysa, **tüm yapılandırma** ve **tüm platformlar** ' ı seçip yolların doğru olduğunu doğrulayabilirsiniz.

![VC + + Içerme dizinleri](media/vcpp-intellisense-include-paths.png)

**VC_IncludePath** gibi derleme makrolarının geçerli değerlerini görmek Için Dizin Ekle satırını seçin ve sağdaki aşağı açılan listeye tıklayın. Sonra **\<Edit>** **makrolar** düğmesini seçin ve tıklayın.

### <a name="makefile-projects"></a>Derleme görevleri dosyası projeleri

NMake proje şablonunu temel alan derleme görevleri dosyası projeleri için sol bölmeden **NMAKE** ' i seçin ve ardından **IntelliSense** kategorisi altında **arama yolunu dahil et** ' i seçin:

![Makefile projesi içerme yolları](media/vcpp-intellisense-makefile-include-paths.png)

### <a name="open-folder-projects"></a>Klasörü Aç projeleri

CMake projeleri için, CMakeLists.txt tüm yapılandırmalarda #include yollarının doğru belirtildiğinden emin olun. Diğer proje türleri dosyasında bir CppProperties.jsgerektirebilir. Daha fazla bilgi için bkz. [IntelliSense 'i CppProperties.jsIle yapılandırma](/cpp/build/open-folder-projects-cpp#configure-code-navigation-with-cpppropertiesjson). Yolun, dosyada tanımlanan her yapılandırma için doğru olduğundan emin olun.

Dosyadaki CppProperties.jsbir sözdizimi hatası varsa, etkilenen dosyalardaki IntelliSense yanlış olur. Visual Studio Çıkış Penceresi hatayı görüntüler.

## <a name="tag-parser-issues"></a>Ayrıştırıcı sorunlarını etiketleme

Etiket ayrıştırıcısı, göz atmak ve gezinmek için kullanılan "benzer" bir C++ ayrıştırıcısıdır. Bu çok hızlıdır, ancak her kod yapısını tamamen anlarsınız.

Örneğin, Önişlemci makrolarını değerlendirmez ve bu nedenle, büyük bir kullanım kullanan kodu yanlış bir şekilde ayrıştırılabilir. Etiket ayrıştırıcısı tanıdık bir kod yapısı ile karşılaştığında, bu kod bölgesinin tamamını atlayabilir.

Bu sorunun Visual Studio 'da bildirimlerinin iki genel yolu vardır:

1. Gezinti çubuğu bir en içteki makroyu gösteriyorsa, geçerli işlev tanımı atlandı:

   ![Etiket ayrıştırıcısı işlev tanımını atlıyor](media/vcpp-intellisense-tag-parser-macro.png)

1. IDE, zaten tanımlanmış olan bir işlev için bir işlev tanımı oluşturmayı önerir:

   ![Bir ayrıştırıcının varolan işlevi tanımlamasını sağlayan etiketi](media/vcpp-intellisense-tag-parser-function.png)

Bu tür sorunları onarmak için, çözüm dizininizin köküne **cpp. İpucu** adlı bir dosya ekleyin. Daha fazla bilgi için bkz. [Ipucu dosyaları](/cpp/build/reference/hint-files).

Etiket Ayrıştırıcı hataları **hata listesi** penceresinde görüntülenir.

## <a name="validate-project-settings-with-diagnostic-logging"></a>Tanılama günlüğü ile proje ayarlarını doğrulama

IntelliSense derleyicisinin Içerme ve Önişlemci makroları dahil doğru derleyici seçeneklerini kullanıp kullanmadığını denetlemek için **araçlar > seçenekler > metin düzenleyicisi > C/C++ > gelişmiş > tanılama günlüğü**' nde IntelliSense komut satırlarının tanılama günlüğünü açın. Günlüğe **kaydetmeyi doğru** , **günlük düzeyini** 5 ' e (en ayrıntılı) ve **günlük filtresini** 8 ' e (IntelliSense günlüğü) ayarlayın.

Çıkış Penceresi artık IntelliSense derleyicisine geçirilen komut satırlarını gösterir. Örnek çıktı aşağıdaki gibidir:

```output
[IntelliSense] Configuration Name: Debug|Win32
[IntelliSense] Toolset IntelliSense Identifier:
[IntelliSense] command line options:
/c
/I.
/IC:\Repo\Includes
/DWIN32
/DDEBUG
/D_DEBUG
/Zc:wchar_t-
/Zc:forScope
/Yustdafx.h
```

Bu bilgiler, IntelliSense 'in neden yanlış bilgi sağladığını anlamanıza yardımcı olabilir. Örneğin, projenizin Içerme dizini **$ (MyVariable) \ Include** değerini içeriyorsa ve tanılama günlüğünde **/I\ınclude** öğesini içerme yolu olarak gösteriyorsa, **$ (MyVariable)** öğesinin değerlendirilmediği ve son içerme yolundan kaldırıldığı anlamına gelir.

## <a name="about-the-intellisense-build"></a>IntelliSense derlemesi hakkında

Visual Studio, tüm IntelliSense özelliklerini destekleyen veritabanını oluşturmak ve sürdürmek için adanmış bir C++ derleyicisi kullanır. IntelliSense veritabanını kodla eşitlenmiş halde tutmak için, Visual Studio yalnızca IntelliSense tarafından otomatik olarak başlatılır; proje ayarlarında veya kaynak dosyalarında yapılan belirli değişikliklere yanıt olarak yalnızca IntelliSense için arka plan görevleri olarak oluşturulur.

Ancak, bazı durumlarda Visual Studio IntelliSense veritabanını zamanında güncelleştirmeyebilir. Örneğin, **git pull** veya **Git Checkout** komutunu çalıştırdığınızda, dosyalardaki değişikliklerin algılanması için Visual Studio bir saate kadar zaman alabilir. **Çözüm Gezgini** ' de proje düğümüne sağ tıklayıp **çözümü yeniden Tara**' yı seçerek, bir Çözümdeki tüm dosyaları yeniden taramaya zorlayabilirsiniz.

## <a name="troubleshooting-intellisense-build-failures"></a>IntelliSense derleme hatalarıyla ilgili sorunları giderme

Bir IntelliSense derlemesi ikili dosyaları oluşturmaz, ancak yine de başarısız olabilir. Hatanın olası nedenlerinden biri Custom. props veya. targets dosyalarıdır. Visual Studio 2017 sürüm 15,6 ve sonrasında, yalnızca IntelliSense derleme hataları çıkış penceresine kaydedilir. Bunları görmek için, **çıktıyı ' den** **çözüme** göster ' i ayarlayın:

![Çözüm hataları için çıkış penceresi](media/vcpp-intellisense-output-window.png)

Hata iletisi, tasarım zamanı izlemeyi etkinleştirmenizi isteyebilir:

```output
error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
configuration 'Debug|x64'. IntelliSense might be unavailable.
Set environment variable TRACEDESIGNTIME=true and restart
Visual Studio to investigate.
```

TRACEDESIGNTIME ortam değişkenini true olarak ayarlarsanız ve Visual Studio 'Yu yeniden başlatırsanız,% TEMP% dizininde, derleme hatasının tanılanmasına yardımcı olabilecek bir günlük dosyası görürsünüz.

TRACEDESIGNTIME ortam değişkeni hakkında daha fazla bilgi edinmek için bkz. [Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Diagnosing-Project-System-Build-Errors.md) ve [ortak proje sistemi](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Bu makalelerdeki bilgiler, C++ projeleri için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
