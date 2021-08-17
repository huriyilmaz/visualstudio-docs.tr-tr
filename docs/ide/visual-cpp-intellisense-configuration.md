---
title: IntelliSense için bir C++ projesi yapılandırma
description: IntelliSense sorunlarını tanımlamanıza ve düzeltmenize yardımcı olmak için Visual Studio IDE'yi kullanarak IntelliSense'in düzgün bir şekilde çalışması için C++ projenizi el ile yapılandırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/08/2018
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 5de1e8e3faff8370343c5145e0ddbd107f0b3b82f7f2e48b901afa7e2c4377c3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121399664"
---
# <a name="configure-a-c-project-for-intellisense"></a>IntelliSense için bir C++ projesi yapılandırma

Bazı durumlarda, IntelliSense'in düzgün şekilde çalışması için C++ projenizi el ile yapılandırmanız gerekebilir. Proje MSBuild için (.vcxproj dosyalarını temel alarak), proje özelliklerinde ayarları ayarlayabilirsiniz. Diğer MSBuild projelerde, projenin CppProperties.jsdizininde yer alan dosyada ayarları yapın. Bazı durumlarda, IntelliSense'in makro tanımlarını anlaya yardımcı olmak için bir ipucu dosyası oluşturmanız gerekir. IDE Visual Studio IntelliSense sorunlarını tanımlamanıza ve düzeltmeye yardımcı olur.

## <a name="single-file-intellisense"></a>Tek dosyalı IntelliSense

Projeye dahil edilen bir dosyayı açicaginiz zaman, Visual Studio IntelliSense desteği sağlar ancak varsayılan olarak hata ikilemleri gösterilmez. Gezinti **Çubuğunda** *Çeşitli* Dosyalar yazıyorsa, bu büyük olasılıkla yanlış kod altında hata geçişlerini neden görmeyebilirsiniz veya önişlemci makrosu tanımlanmamıştır.

## <a name="check-the-error-list"></a>Hata Listesini Denetleme

Bir dosya tek dosya modunda açık değilse ve IntelliSense düzgün çalışmıyorsa, ilk olarak Hata Listesi penceresi kontrol etmektir. Geçerli kaynak dosyanın tüm IntelliSense hatalarını dahil edilen tüm üst bilgi dosyalarıyla birlikte görmek için açılan listeden Derleme **+ IntelliSense'i** seçin:

![Hata Listesinde VC++ IntelliSense](media/vcpp-intellisense-error-list.png)

IntelliSense en fazla 1000 hata üretir. Bir kaynak dosyanın dahil olduğu üst bilgi dosyalarında 1000'den fazla hata varsa, kaynak dosyanın en başında yalnızca tek bir hata ikilem gösterir.

## <a name="ensure-include-paths-are-correct"></a>Tüm #include doğru olduğundan emin olun

### <a name="msbuild-projects"></a>MSBuild projeleri

Derlemelerinizi Visual Studio IDE dışında çalıştırıyorsanız ve derlemeleriniz başarılı oluyorsa ancak IntelliSense yanlışsa, komut satırınız bir veya daha fazla yapılandırma için proje ayarlarıyla eşitnin dışında olabilir. Çözüm Gezgini proje düğümüne sağ  tıklayın ve geçerli yapılandırma **#include** platform için tüm bağlantı yollarının doğru olduğundan emin olun. Yollar tüm yapılandırmalarda ve platformlarda aynıysa  Tüm yapılandırmalar ve Tüm platformlar'ı seçerek yolların doğru olduğunu doğrulayın. 

![VC++ Dizinleri Dahil Edin](media/vcpp-intellisense-include-paths.png)

VC_IncludePath gibi derleme makroları için geçerli değerleri görmek için **Dizinleri** Dahil VC_IncludePath seçin ve sağdan açılan listeye tıklayın. Ardından **\<Edit>** Makrolar düğmesini **seçin ve tıklayın.**

### <a name="makefile-projects"></a>Derleme görevleri dosyası projeleri

NMake proje şablonunu temel alan Makefile projeleri için sol bölmede **NMake'i** ve **ardından IntelliSense** kategorisinin arama yolunu dahil edin'i seçin: 

![Makefile projesi yolları içerir](media/vcpp-intellisense-makefile-include-paths.png)

### <a name="open-folder-projects"></a>Klasörü Aç projeleri

CMake projeleri için, #include tüm yapılandırmalar için doğru şekilde belirtilen yollara sahip CMakeLists.txt. Diğer proje türleri, dosyada CppProperties.jsgerektirir. Daha fazla bilgi için, [bkz. Configure IntelliSense with CppProperties.json](/cpp/build/open-folder-projects-cpp#configure-code-navigation-with-cpppropertiesjson). Dosyada tanımlanan her yapılandırma için yolların doğru olduğundan emin olun.

Dosyanın söz dizimi hatası CppProperties.js, etkilenen dosyalarda IntelliSense yanlış olur. Visual Studio hata, hatanın Çıkış Penceresi.

## <a name="tag-parser-issues"></a>Etiket ayrıştırıcı sorunları

Etiket ayrıştırıcı, göz atma ve gezinme için kullanılan bir "belirsiz" C++ ayrıştırıcıdır. Çok hızlıdır ancak her kod yapıyı tamamen kavramaya denemez.

Örneğin, ön işlemci makrolarını değerlendirmez ve bu nedenle bunları yoğun olarak kullanan kodu yanlış ayrıştırabilir. Etiket Ayrıştırıcısı, yabancı bir kod yapısıyla karşılaştığında kodun tüm bölgesini atlar.

Bu sorunun bildirimlerini iki yaygın şekilde Visual Studio:

1. Gezinti Çubuğu en içteki makroyu gösteriyorsa geçerli işlev tanımı atlanır:

   ![Etiket ayrıştırıcısı işlev tanımını atlar](media/vcpp-intellisense-tag-parser-macro.png)

1. IDE, önceden tanımlanmış bir işlev için işlev tanımı oluşturmanızı sağlar:

   ![Mevcut işlevi tanımlamak için etiket ayrıştırıcı teklifleri](media/vcpp-intellisense-tag-parser-function.png)

Bu tür sorunları düzeltmek için çözüm dizininizin köküne **cpp.hint** adlı bir dosya ekleyin. Daha fazla bilgi için bkz. [İpucu Dosyaları.](/cpp/build/reference/hint-files)

Etiket ayrıştırıcı hataları Hata Listesi **penceresinde** görüntülenir.

## <a name="validate-project-settings-with-diagnostic-logging"></a>Tanılama günlüğü ile proje ayarlarını doğrulama

IntelliSense derleyicisi, Yolları ve Önişlemci makrolarını dahil olmak üzere doğru derleyici seçeneklerini kullanarak olmadığını kontrol etmek için Araçlar > Seçenekleri > Metin Düzenleyicisi **> C/C++**> Gelişmiş > Tanılama Günlüğü'nde IntelliSense komut satırlarının Tanılama Günlüğünü açın. Günlüğü **Etkinleştir'i** True, **Günlük Düzeyi'yi** 5 (en ayrıntılı) ve **Günlük** Filtresi'yi 8 (IntelliSense günlüğü) olarak ayarlayın.

Komut Çıkış Penceresi intelliSense derleyiciye geçirilen komut satırlarını gösterecektir. Örnek çıktı aşağıdaki gibidir:

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

Bu bilgiler, IntelliSense'in neden yanlış bilgi sağlamayı anlıyoruz yardımcı olabilir. Örneğin, projenizin Include dizini **$(MyVariable)\Include** dizinini içeriyorsa ve tanılama günlüğü bir Dahil etme yolu olarak **/I\Include** gösteriyorsa, **$(MyVariable)** değerlendirilmedi ve son dahil etme yolundan kaldırıldı demektir.

## <a name="about-the-intellisense-build"></a>IntelliSense derlemesi hakkında

Visual Studio, tüm IntelliSense özelliklerini kullanan veritabanını oluşturmak ve korumak için ayrılmış bir C++ derleyicisi kullanır. IntelliSense veritabanını kodla eşit tutmak için Visual Studio, proje ayarlarında veya kaynak dosyalarda yapılan belirli değişikliklere yanıt olarak yalnızca IntelliSense derlemelerini arka plan görevleri olarak otomatik olarak başlatıyor.

Ancak, bazı Visual Studio IntelliSense veritabanını zamanında güncelleştirmeyebilirsiniz. Örneğin, bir git **çekme** veya **git** onay komutu Visual Studio değişiklikleri algılamak bir saate kadar zamanlanabilir. Çözümdeki proje düğümüne sağ tıklar ve Çözümü Yeniden Yalıt'ı seçerek Çözüm Gezgini bir **çözümdeki** tüm dosyaları **yeniden sın zorabilirsiniz.**

## <a name="troubleshooting-intellisense-build-failures"></a>IntelliSense derleme hatalarını giderme

IntelliSense derlemesi ikili dosyalar oluşturmaz, ancak yine de başarısız olabilir. Hatanın olası nedenlerinden biri özel .props veya .targets dosyalarıdır. 2017 Visual Studio 15.6 ve sonraki sürümlerde Yalnızca IntelliSense derleme hataları Çıkış penceresine kaydedilir. Bunları görmek için Çıktıyı **göster'i Çözüm olarak** **ayarlayın:**

![Çözüm hataları için çıkış penceresi](media/vcpp-intellisense-output-window.png)

Hata iletisi tasarım zamanı izlemeyi etkinleştirmeniz için size talimat verir:

```output
error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
configuration 'Debug|x64'. IntelliSense might be unavailable.
Set environment variable TRACEDESIGNTIME=true and restart
Visual Studio to investigate.
```

TRACEDESIGNTIME ortam değişkensini true olarak ayarp Visual Studio yeniden başlattıktan sonra %TEMP% dizininde derleme hatasını tanılamaya yardımcı olacak bir günlük dosyasıyla karşılaşırsınız.

TRACEDESIGNTIME ortam değişkeni hakkında daha fazla bilgi edinmek için bkz. [Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Diagnosing-Project-System-Build-Errors.md) ve [Common Project System](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Bu makalelerde yer alan bilgiler C++ projeleriyle ilgilidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
