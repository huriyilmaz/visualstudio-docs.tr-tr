---
title: Kod kapsamı testi
description: Kodlu testlerde proje kodunuzun hangi Visual Studio test olduğunu belirlemek için Visual Studio kodunun kod kapsamı özelliğini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 07/23/2019
ms.topic: conceptual
helpviewer_keywords:
- code coverage
dev_langs:
- CSharp
- VB
- CPP
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 365cc9428160c5673e3b9750cf12f7f30b812473af68e42798b452a0ad969abe
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395128"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Kod kapsamını kullanarak ne kadar kodun test edildiğini belirleme

Proje kodunuzun ne oranda aslında birim testleri gibi kodlanmış testler tarafından test edilen belirlemek için Visual Studio kod kapsamı özelliğini kullanabilirsiniz. Etkin hatalara karşı koruma sağlamak için testleriniz çalışmalı veya kodunuzun büyük bir kısmını 'kapsamalıdır'.

Kod Kapsamı Çözümleme (CLI) yönetilen ve yönetilmeyen (yerel) kod için uygulanabilir.

Test yöntemlerini Test Gezgini'ni kullanarak çalıştırdığınızda kod kapsamı bir seçenektir. Sonuçlar tablosu, her derleme sınıfı ve yöntemi içinde çalışan kod yüzdesini gösterir. Ayrıca, kaynak düzenleyici hangi kodun test edildiğini gösterir.

::: moniker range="vs-2017"

![Renklendirme ile kod kapsamı sonuçları](../test/media/codecoverage1.png)

::: moniker-end

## <a name="requirements"></a>Gereksinimler

Kod kapsamı özelliği yalnızca Visual Studio Enterprise kullanılabilir.

## <a name="analyze-code-coverage"></a>Kod kapsamayı analiz etme

::: moniker range="vs-2017"

1. Test menüsünde **Kod** Kapsamı Analiz'i **seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Test menüsünde **Tüm Testler** için Kod **Kapsamı Analizi'ne tıklayın.**

   ![VS 2019'da kod kapsamı analizi menüsü](../test/media/vs-2019/analyze-code-coverage.png)

   Kod kapsamı'nı Test Gezgini araç penceresinden de çalıştırabilirsiniz.

::: moniker-end

2. Testler çalıştır girdikten sonra, hangi satırların çalıştır olduğunu görmek için Kod Kapsamı Sonuçları penceresinde Kod Kapsamı Renklendirmeyi Göster simgesi Kod Kapsamı ![ ](../test/media/codecoverage-showcoloringicon.png)  **Renklendirmeyi Göster'i** seçin. Varsayılan olarak, testler kapsamındaki kod açık mavi renkle vurgulanır.

   > [!TIP]
   > Renkleri değiştirmek veya kalın yüz kullanmak için Araçlar Seçenekler Ortam Yazı Tipleri ve Renkler Göster ayarlarını  >    >    >    >  **seçin: Metin Düzenleyici.** Öğeleri **görüntüle altında,**"Kapsam" öğelerinin ayarlarını ayarlayın; örneğin, **Kapsam Dokunulmadı Alanı.**
   >
   > ![Kod kapsamı yazı tipleri ve renkleri](media/vs-2019/coverage-fonts-and-colors.png)

3. Sonuçlar düşük kapsamı gösterirse, hangi kod parçalarının uygulanmadığını araştırın ve bunları kapsamak için daha fazla test yazın. Geliştirme ekipleri için tipik olarak yaklaşık %80 kod kapsamı hedeflenir. Bazı durumlarda, düşük kapsam kabul edilebilir. Örneğin, düşük kapsamı bazı kodlar standart şablonundan oluşturulduğu kabul edilebilir.

> [!TIP]
> - Derleyici iyileştirmeyi kapatma
> - Unmanaged (native) koduyla çalışıyorsanız hata ayıklama derlemesi kullanın
> - Her derleme için .pdb (sembol) dosyaları oluşturma

Beklediğiniz sonuçları alasanız bkz. Kod kapsamı [sorunlarını giderme.](../test/troubleshooting-code-coverage.md)

Kodunuzu güncelleştirdikten sonra kod kapsamı çalıştırmayı unutmayın. Kodunuzu değiştirdikten sonra veya testleri çalıştırdığınızda kapsam sonuçları ve kod renklendirme otomatik olarak güncelleştirilmez.

## <a name="report-in-blocks-or-lines"></a>Bloklar veya satırlar içinde rapor

Kod kapsamı blokları olarak *sayılır.* Bir blok, tek bir giriş ve çıkış noktası kodu parçasıdır.  Programın denetim akışı bir test çalıştırması sırasında bir blok üzerinden geçerse, bu blok kapsamış olarak sayılır. Blok kullanılma sayısının sonuç üzerinde etkisi yoktur.

Tablo üst bilgisinde Sütun Ekle/Kaldır'ı seçerek **sonuçların satırlar açısından** görüntülenebilir. Yüzdeler kaynak kodunda gördüğünüz parçaların boyutuyla daha yakından ilişkili olduğundan bazı kullanıcılar satırları saymayı tercih eder. Birçok satır kaplayan olsa bile uzun bir blok hesaplama tek bir blok olarak sayılacaktır.

> [!TIP]
> Bir kod satırı birden fazla kod bloğu içerebilir. Böyle bir durum varsa ve test çalıştırması satırda tüm kod bloklarını çalıştırıyorsa, tek satır olarak sayılır. Satırda kod bloklarının bazıları ancak bazıları değil de tüm kod bloklarının alıştırması varsa, kısmi satır olarak sayılır.

## <a name="manage-code-coverage-results"></a>Kod kapsamı sonuçlarını yönetme

Kod **Kapsamı Sonuçları** penceresi genellikle en son çalıştırmanın sonuçlarını gösterir. Sonuçlar test verilerini değiştirirseniz veya testlerinizin her defasında yalnızca bir kısmını çalıştırırsanız değişir.

Kod kapsamı penceresini önceki sonuçları veya diğer bilgisayarlarda elde edilen sonuçları görüntülemek için de kullanılabilir.

Birçok çalıştırmanın sonucunu örneğin farklı test verileri kullanan çalışmalardan birleştirebilirsiniz.

- **Önceki sonuç kümelerini görüntülemek için,** açılan menüden bunu seçin. Menü, yeni bir çözüm açtığınızda temizlenen geçici bir liste gösterir.

- **Önceki oturumdan gelen sonuçları görüntülemek için** Kod Kapsamı Sonuçlarını İçeri Aktar'ı seçin, çözümünüzdeki **TestResults** klasörüne gidin ve *bir .coverage dosyasını içeri aktarın.* 

   .coverage dosyası oluşturulurken kaynak kodun değişmesi, kapsam *renklendirmesi* yanlış olabilir.

- **Sonuçları metin olarak okunabilir yapmak için Kod** Kapsamı Sonuçlarını Dışarı **Aktar'ı seçin.** Bu, diğer araçlarla işlenebilir veya posta ile kolayca gönderebilirsiniz okunabilir bir *.coveragexml* dosyası üretir.

- **Sonuçları başka birine göndermek için** bir *.coverage* dosyası veya dışarı aktarıldı *.coveragexml dosyası* gönderin. Sonra dosyayı içe aktarabilirsiniz. Kaynak kodun aynı sürümü varsa, kapsam renklendirmeyi görebilirsiniz.

## <a name="merge-results-from-different-runs"></a>Farklı çalıştırmalardan gelen sonuçları birleştirme

Bazı durumlarda, test verilerine bağlı olarak kodunuzda farklı bloklar kullanılacaktır. Bu nedenle, farklı bir test çalışmasının sonuçlarını birleştirmek isteyebilirsiniz.

Örneğin, giriş "2" ile bir test çalıştırdığınızda, belirli bir işlevin %50'sinin kapsandığını bulun. Testi "-2" girişiyle ikinci kez çalıştırarak kapsamın renklendirme görünümünde işlevin diğer %50'sini kapsadı olarak görüyorsunuz. Şimdi iki test çalışması sonuçlarını birleştirin ve işlevin %100 kapsamında rapor ve görünümü renklendirme kapsamını gösterin.

Bunu ![ yapmak için Kod Kapsamı penceresindeKimlik Kapsamı Sonuçlarını Birleştir düğmesi ](../test/media/codecoverage-mergeicon.png) **için** Simge'ye tıklayın. Son çalışmaların veya alınan sonuçların herhangi bir bileşimini seçebilirsiniz. Dışa aktarılan sonuçları birleştirmek istiyorsanız, bunları önce almanız gerekir.

Birleştirme **işlemi sonuçlarını kaydetmek için** Kod Kapsamı Sonuçlarını Dışarı Aktar'ı kullanın.

### <a name="limitations-in-merging"></a>Birleştirmede sınırlamalar

- Kodun farklı sürümlerinden kapsama verilerini birleştirirseniz, sonuçlar ayrı ayrı gösterilir, ancak birleştirilmez. Tam olarak birleştirilmiş sonuçlar almak için test verilerini değiştirerek kodun aynı yapısını kullanın.

- Dışa ve sonra içe alınmış sonuç dosyasını birleştirirseniz, sonuçları bloklarla değil yalnızca çizgilerle görüntüleyebilirsiniz. Satır **verilerini göstermek için Sütun Ekle/Kaldır** komutunu kullanın.

- ASP.NET projesinin testlerinden sonuçları birleştirirseniz, birleştirilmiş değil ayrı testlerin sonuçları görüntülenir. Bu yalnızca ASP.NET yapılarına uygulanır: başka bir derleme için sonuçlar birleştirilecektir.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Öğeleri kod kapsamı sonuçlarından dışlama

Örneğin kodu bir metin şablonundan oluşturulan tedarik puanlarını kodunuzda belirli öğeler dışında isteyebilirsiniz. özniteliğini <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> şu kod öğelerine ekleyin: class, struct, method, property, property setter veya getter, event.

> [!TIP]
> Bir sınıfı dışlamak, türetilmiş sınıflarını dışlamaz.

Örnek:

```csharp
using System.Diagnostics.CodeAnalysis;
...
public class ExampleClass1
{
    [ExcludeFromCodeCoverage]
    void ExampleMethod() {...}

    [ExcludeFromCodeCoverage] // exclude property
    int ExampleProperty1
    { get {...} set{...}}

    int ExampleProperty2
    {
        get
        {
            ...
        }
        [ExcludeFromCodeCoverage] // exclude setter
        set
        {
            ...
        }
    }

}
[ExcludeFromCodeCoverage]
class ExampleClass2 { ... }
```

```vb
Imports System.Diagnostics.CodeAnalysis

Class ExampleClass1
    <ExcludeFromCodeCoverage()>
    Public Sub ExampleSub1()
        ...
    End Sub

    ' Exclude property
    < ExcludeFromCodeCoverage()>
    Property ExampleProperty1 As Integer
        ...
    End Property

    ' Exclude setter
    Property ExampleProperty2 As Integer
        Get
            ...
        End Get
        <ExcludeFromCodeCoverage()>
        Set(ByVal value As Integer)
            ...
        End Set
    End Property
End Class

<ExcludeFromCodeCoverage()>
Class ExampleClass2
...
End Class
```

```cpp
// A .cpp file compiled as managed (CLI) code.
using namespace System::Diagnostics::CodeAnalysis;
...
public ref class ExampleClass1
{
  public:
    [ExcludeFromCodeCoverage]
    void ExampleFunction1() { ... }

    [ExcludeFromCodeCoverage]
    property int ExampleProperty2 {...}

    property int ExampleProperty2 {
      int get() { ... }
     [ExcludeFromCodeCoverage]
      void set(int value) { ...  }
   }
}

[ExcludeFromCodeCoverage]
public ref class ExampleClass2
{ ... }
```

### <a name="exclude-elements-in-native-c-code"></a>Yerel C++ kodundaki öğeleri dışlama

C++ koddaki yönetilmeyen (yerel) öğeleri dışlamak için:

```cpp
#include <CodeCoverage\CodeCoverage.h>
...

// Exclusions must be compiled as unmanaged (native):
#pragma managed(push, off)

// Exclude a particular function:
ExcludeFromCodeCoverage(Exclusion1, L"MyNamespace::MyClass::MyFunction");

// Exclude all the functions in a particular class:
ExcludeFromCodeCoverage(Exclusion2, L"MyNamespace::MyClass2::*");

// Exclude all the functions generated from a particular template:
ExcludeFromCodeCoverage(Exclusion3, L"*::MyFunction<*>");

// Exclude all the code from a particular .cpp file:
ExcludeSourceFromCodeCoverage(Exclusion4, L"*\\unittest1.cpp");

// After setting exclusions, restore the previous managed/unmanaged state:
#pragma managed(pop)
```

Aşağıdaki makroları kullanın:

`ExcludeFromCodeCoverage(`*ExclusionName* `, L"` *FunctionName*`");`

`ExcludeSourceFromCodeCoverage(`*ExclusionName* `, L"` *SourceFilePath*`");`

- *ExclusionName* herhangi bir benzersiz addır.

- *FunctionName,* tam işlev adıdır. Joker karakterler içerebilir. Örneğin, bir sınıfın tüm işlevlerini dışlamak için yazın `MyNamespace::MyClass::*`

- *SourceFilePath,* bir .cpp dosyasının yerel veya UNC yoludur. Joker karakterler içerebilir. Aşağıdaki örnek, belirli bir dizinde yer alan tüm dosyaları dışlar: `\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Herhangi bir ad alanı veya sınıf içindeki değil genel ad alanındaki dışlama makroları için çağrılar yerleşir.

- Dışlamaları birim test kod dosyasına veya uygulama kod dosyasına yerleştirebilirsiniz.

- Dışlamaların, derleyici seçeneği ayarlanmadan veya kullanılarak, unmanaged (yerel) kod olarak derlenmiş olması `#pragma managed(off)` gerekir.

> [!NOTE]
> C++/CLI kodundaki işlevleri dışlamak için `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` özniteliğini işleve uygulama. Bu C# ile aynıdır.

### <a name="include-or-exclude-additional-elements"></a>Ek öğeleri dahil etmek veya hariç tutmak

Kod kapsamı analizi yalnızca yüklenen ve *.pdb* dosyasının dosya veya dosya ile aynı dizinde kullanılabilir olduğu *derlemelerde.dll* *.exe* gerçekleştirilir. Bu nedenle bazı durumlarda, uygun *.pdb* dosyalarının kopyalarını alarak dahil edilen derlemeler kümesi genişletebilirsiniz.

Bir *.runsettings* dosyası yazarak kod kapsamı analizi için hangi derlemelerin ve öğelerin seçilecekleri üzerinde daha fazla denetim kullanabilirsiniz. Örneğin, kendi sınıfları için öznitelikler eklemek zorunda kalmadan belirli tür derlemeleri hariç tutabilirsiniz. Daha fazla bilgi için [bkz. Kod kapsamı analizini özelleştirme.](../test/customizing-code-coverage-analysis.md)

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Azure Pipelines'da kod Azure Pipelines

Kodunuzu iade edinca, testlerinizi derleme sunucusunda ve diğer ekip üyelerinin testleriyle birlikte çalıştırın. Projenin tamamında en güncel ve kapsamlı kapsam Azure Pipelines için kod kapsamı çözümlemek yararlı olur. Ayrıca otomatik sistem testlerini ve genellikle geliştirme makinelerinde çalıştırmayıp diğer kodlu testleri de içerir. Daha fazla bilgi için [bkz. Derlemeleriniz ile birim testleri çalıştırma.](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)

## <a name="analyze-code-coverage-from-the-command-line"></a>Komut satırdan kod kapsamayı analiz etme

Testleri komut satırdan çalıştırmak için komutunu *vstest.console.exe.* Kod kapsamı,vstest.console.exe *seçeneğidir.*

1. Geliştirici Komut İstemi için Visual Studio:

   ::: moniker range="vs-2017"

   Windows **menüsünde** VS **2017 için Visual Studio 2017** Geliştirici Komut İstemi seçeneğini > **belirleyin.**

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   Windows **menüsünde** VS **2019 için Visual Studio 2019** > **Geliştirici Komut İstemi'ı seçin.**

   ::: moniker-end

2. Komut isteminde aşağıdaki komutu çalıştırın:

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

Daha fazla bilgi için [bkz.VSTest.Console.exe komut satırı seçenekleri.](vstest-console-options.md)

## <a name="troubleshoot"></a>Sorun giderme

Kod kapsamı sonuçlarını görmüyorsanız Kod kapsamı [sorunlarını giderme makalesi](../test/troubleshooting-code-coverage.md) size yardımcı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md)
- [Kod kapsamı sorunlarını giderme](../test/troubleshooting-code-coverage.md)
- [Kodunuzu birim testi](../test/unit-test-your-code.md)
