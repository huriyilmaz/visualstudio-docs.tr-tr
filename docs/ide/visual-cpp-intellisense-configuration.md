---
title: IntelliSense için bir C++ projesi yapılandırma
ms.date: 10/08/2018
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 8c43c48a797619f86f81e219e31ccf2afab5ba87
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279319"
---
# <a name="configure-a-c-project-for-intellisense"></a>IntelliSense için bir C++ projesi yapılandırma

Bazı durumlarda, IntelliSense'in düzgün çalışması için C++ projenizi el ile yapılandırmanız gerekebilir. MSBuild projeleri için (.vcxproj dosyalarına dayalı), proje özelliklerindeki ayarları ayarlayabilirsiniz. MSBuild olmayan projeler için, projenin kök dizinindeki CppProperties.json dosyasındaki ayarları ayarlarsınız. Bazı durumlarda, IntelliSense'in makro tanımlarını anlamasına yardımcı olmak için bir ipucu dosyası oluşturmanız gerekebilir. Visual Studio IDE, IntelliSense sorunlarını belirlemenize ve düzeltmenize yardımcı olur.

## <a name="single-file-intellisense"></a>Tek dosyalı IntelliSense

Bir projeye dahil olmayan bir dosyayı açtığınızda, Visual Studio bazı IntelliSense desteği sağlar, ancak varsayılan olarak hiçbir hata squiggles gösterilir. Gezinti **Çubuğu** Çeşitli Dosyalar diyorsa, bu büyük olasılıkla neden yanlış kod altında hata squiggles görmüyorsanız açıklar, ya da neden bir önişlemci makro tanımlı değil. *Miscellaneous Files*

## <a name="check-the-error-list"></a>Hata Listesini Kontrol Et

Bir dosya tek dosya modunda açık değilse ve IntelliSense doğru çalışmıyorsa, ilk kontrol edilen yer Hata Listesi penceresidir. Geçerli kaynak dosyadaki tüm IntelliSense hatalarını, dahil edilen tüm üstbilgi dosyalarıyla birlikte görmek için açılır kapıda **Build + IntelliSense'i** seçin:

![VC++ Hata Listesinde IntelliSense](media/vcpp-intellisense-error-list.png)

IntelliSense en fazla 1000 hata üretir. Kaynak dosya tarafından eklenen üstbilgi dosyalarında 1000'den fazla hata varsa, kaynak dosya kaynak dosyanın en başında yalnızca tek bir hata hatası gösterir.

## <a name="ensure-include-paths-are-correct"></a>#include yollarının doğru olduğundan emin olun

### <a name="msbuild-projects"></a>MSBuild projeleri

Yapılarınızı Visual Studio IDE'nin dışında çalıştırıyorsanız ve yapılarınızın başarılı olması ancak IntelliSense yanlışsa, komut satırınızın bir veya daha fazla yapılandırma için proje ayarlarıyla eşitlenmemiş olması mümkündür. **Solution Explorer'daki** proje düğümüne sağ tıklayın ve tüm **#include** yollarının geçerli yapılandırma ve platform için doğru olduğundan emin olun. Yollar tüm yapılandırmalarda ve platformlarda aynıysa, **Tüm yapılandırmaları** ve tüm **platformları** seçebilir ve yolların doğru olduğunu doğrulayabilirsiniz.

![VC++ Dizinleri Dahil Et](media/vcpp-intellisense-include-paths.png)

**VC_IncludePath**gibi yapı makroları için geçerli değerleri görmek için Dizinleri Ekle satırını seçin ve sağdaki açılır dosyayı tıklatın. Ardından ** \<>'yı edit'i** seçin ve **Makrolar** düğmesine tıklayın.

### <a name="makefile-projects"></a>Derleme görevleri dosyası projeleri

NMake proje şablonunu temel alan Makefile projeleri için sol bölmede **NMake'i** seçin ve ardından **IntelliSense** kategorisi altında **arama yolunu ekle'yi** seçin:

![Makefile projesi yolları içerir](media/vcpp-intellisense-makefile-include-paths.png)

### <a name="open-folder-projects"></a>Klasörü Aç projeleri

CMake projeleri için, CMakeLists.txt'deki tüm yapılandırmalar için #include yollarının doğru şekilde belirtildiğinden emin olun. Diğer proje türleri cppProperties.json dosyası gerektirebilir. Daha fazla bilgi için [CppProperties.json ile IntelliSense'i Yapılandırın.](/cpp/build/open-folder-projects-cpp#configure-code-navigation-with-cpppropertiesjson) Dosyada tanımlanan her yapılandırma için yolların doğru olduğundan emin olun.

CppProperties.json dosyasında sözdizimi hatası varsa, etkilenen dosyalardaki IntelliSense yanlış olacaktır. Visual Studio hatayı Çıkış Penceresinde görüntüler.

## <a name="tag-parser-issues"></a>Etiket parser sorunları

Etiket parser tarama ve gezinme için kullanılan bir "bulanık" C ++ parser olduğunu. Çok hızlıdır ancak her kod yapısını tamamen kavramaya çalışmaz.

Örneğin, önişlemci makrolarını değerlendirmez ve bu nedenle bunları yoğun olarak kullanan kodu yanlış ayrışdırabilir. Tag Parser yabancı bir kod yapısıyla karşılaştığında, tüm kod bölgesini atlayabilir.

Bu sorunun Visual Studio'da ortaya çıkmasının iki yaygın yolu vardır:

1. Gezinti Çubuğu en içteki makroyu gösteriyorsa, geçerli işlev tanımı atlandı:

   ![Etiket parser fonksiyon tanımı atlar](media/vcpp-intellisense-tag-parser-macro.png)

1. IDE, zaten tanımlanmış bir işlev için işlev tanımı oluşturmayı teklif eder:

   ![Etiket parser varolan işlevi tanımlamak için sunuyor](media/vcpp-intellisense-tag-parser-function.png)

Bu tür sorunları gidermek için, çözüm dizininizin köküne **cpp.ipucu** adlı bir dosya ekleyin. Daha fazla bilgi için [İpucu Dosyaları'na](/cpp/build/reference/hint-files)bakın.

Etiket parser hataları **Hata Listesi** penceresinde görünür.

## <a name="validate-project-settings-with-diagnostic-logging"></a>Tanılama günlüğe kaydetme ile proje ayarlarını doğrulama

IntelliSense derleyicisinin Yolları Ve Önİşleme İşlemci makroları dahil olmak üzere doğru derleyici seçeneklerini kullanıp kullanmadığını kontrol etmek için, **Araçlar > Seçenekleri > Metin Düzenleyicisi > C/C++ > Advanced > Diagnostic Logging'de**IntelliSense komut satırlarının Tanısal Günlüğe Kaydetme'yi açın. **Günlük Günlemesini** Doğru'ya, Günlük **Düzeyini** 5'e (en ayrıntılı) ve **Günlük Filtresini** 8'e (IntelliSense günlüğe kaydetme) ayarla.

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

Bu bilgiler, IntelliSense'in neden yanlış bilgi sağladığını anlamanıza yardımcı olabilir. Örneğin, projenizin Ekle dizini **$(MyVariable)\Include**ve tanılama günlüğü gösterir **/I\Include** yolu olarak içeriyorsa, bu **$(MyVariable)** değerlendirilmediği ve son dahil yolundan kaldırıldığı anlamına gelir.

## <a name="about-the-intellisense-build"></a>IntelliSense yapısı hakkında

Visual Studio, tüm IntelliSense özelliklerine güç veren veritabanını oluşturmak ve korumak için özel bir C++ derleyicisi kullanır. IntelliSense veritabanını kodla senkronize tutmak için Visual Studio, proje ayarlarında veya kaynak dosyalarında yapılan bazı değişikliklere yanıt olarak yalnızca Arka plan görevleri olarak intelliSense oluşturmayı otomatik olarak başlatır.

Ancak, bazı durumlarda Visual Studio, IntelliSense veritabanını zamanında güncelleştiremeyebilir. Örneğin, **git çekme** veya **git ödeme** komutunu çalıştırdığınızda, Visual Studio'nun dosyalardaki değişiklikleri algılaması bir saat kadar sürebilir. **Solution Explorer'daki** proje düğümüne sağ tıklayarak ve **Rescan Solution'ı**seçerek çözümdeki tüm dosyaların rescan'ını zorlayabilirsiniz.

## <a name="troubleshooting-intellisense-build-failures"></a>Sorun Giderme IntelliSense yapı hataları

Bir IntelliSense yapı ikili üretmek değil, ama yine de başarısız olabilir. Hatanın olası nedenlerinden biri özel .props veya .targets dosyalarıdır. Visual Studio 2017 sürüm 15.6 ve sonraki sürümlerinde, IntelliSense'in yalnızca yapı hataları Çıktı penceresine kaydedilir. Bunları görmek için, **Çözüm'den** **Çözüme**çıkış göster'i ayarlayın:

![Çözüm hataları için çıkış penceresi](media/vcpp-intellisense-output-window.png)

Hata iletisi, tasarım zamanı izlemeetkinleştirmenizi sağlayabilir:

```output
error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
configuration 'Debug|x64'. IntelliSense might be unavailable.
Set environment variable TRACEDESIGNTIME=true and restart
Visual Studio to investigate.
```

Çevre değişkeni TRACEDESIGNTIME'ı doğru olarak ayarlar ve Visual Studio'yu yeniden başlatırsanız, %TEMP% dizininde yapı hatasını tanılamaya yardımcı olabilecek bir günlük dosyası görürsünüz.

TRACEDESIGNTIME ortamı değişkeni hakkında daha fazla bilgi edinmek için [Roslyn](https://github.com/dotnet/roslyn/wiki/Diagnosing-Project-System-Build-Errors) ve [Ortak Proje Sistemi'ne](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md)bakın. Bu makalelerdeki bilgiler C++ projeleri için önemlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
