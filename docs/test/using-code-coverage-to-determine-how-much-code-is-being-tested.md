---
title: Kod kapsamı testi
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
manager: jillfra
ms.openlocfilehash: 6dd6dde83720c6e6f37bd6827bb5d97526202aa7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585606"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Kod kapsamını kullanarak ne kadar kodun test edildiğini belirleme

Proje kodunuzun ne oranda aslında birim testleri gibi kodlanmış testler tarafından test edilen belirlemek için Visual Studio kod kapsamı özelliğini kullanabilirsiniz. Etkin hatalara karşı koruma sağlamak için testleriniz çalışmalı veya kodunuzun büyük bir kısmını 'kapsamalıdır'.

Kod Kapsamı Çözümleme (CLI) yönetilen ve yönetilmeyen (yerel) kod için uygulanabilir.

Test yöntemlerini Test Gezgini'ni kullanarak çalıştırdığınızda kod kapsamı bir seçenektir. Sonuçlar tablosu, her derleme sınıfı ve yöntemi içinde çalışan kod yüzdesini gösterir. Ayrıca, kaynak düzenleyici hangi kodun test edildiğini gösterir.

::: moniker range="vs-2017"

![Boyama ile kod kapsamı sonuçları](../test/media/codecoverage1.png)

::: moniker-end

## <a name="requirements"></a>Gereksinimler

Kod kapsamı özelliği yalnızca Visual Studio Enterprise sürümünde kullanılabilir.

## <a name="analyze-code-coverage"></a>Kod kapsamını analiz edin

::: moniker range="vs-2017"

1. **Test** menüsünde **Kod Kapsamını Analiz**et'i seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. **Test** menüsünde, **Tüm Testler için Kod Kapsamını Analiz et'i**seçin.

   ![VS 2019'da kod kapsama menüsünü analiz edin](../test/media/vs-2019/analyze-code-coverage.png)

   Test Gezgini araç penceresinden kod kapsamı da çalıştırabilirsiniz.

::: moniker-end

2. Testler çalıştırıldıktan sonra, hangi satırların çalıştırıldığını görmek için ![](../test/media/codecoverage-showcoloringicon.png) Kod Kapsamı Boyama simgesini Kod Kapsamı **Sonuçları** penceresinde Göster Kod Kapsamı **Boyama'yı** seçin. Varsayılan olarak, testler tarafından kapsanan kod açık mavi ile vurgulanır.

   > [!TIP]
   > Renkleri değiştirmek veya kalın yüz kullanmak **için, Araçlar** > **Seçenekleri** > **Ortamı** > **Yazı Tipleri ve Renkler** > **Için Ayarları Göster'i seçin: Metin Düzenleyicisi.** **Görüntü öğelerinin**altında, "Kapsam" öğelerinin ayarlarını ayarlayın, örneğin, **Kapsama Alanı Dokunulmaz.**
   >
   > ![Kod kapsamı yazı tipleri ve renkleri](media/vs-2019/coverage-fonts-and-colors.png)

3. Sonuçlar düşük kapsamı gösterirse, hangi kod parçalarının uygulanmadığını araştırın ve bunları kapsamak için daha fazla test yazın. Geliştirme ekipleri için tipik olarak yaklaşık %80 kod kapsamı hedeflenir. Bazı durumlarda, düşük kapsam kabul edilebilir. Örneğin, düşük kapsamı bazı kodlar standart şablonundan oluşturulduğu kabul edilebilir.

> [!TIP]
> - Derleyici optimizasyonu kapatma
> - Yönetilmeyen (yerel) kodla çalışıyorsanız, hata ayıklama oluşturma
> - Her derleme için .pdb (sembol) dosyaları oluşturma

Beklediğiniz sonuçları alamazsanız, [Sorun Giderme kodu kapsamına](../test/troubleshooting-code-coverage.md)bakın.

Kodunuzu güncelledikten sonra kod kapsamını yeniden çalıştırmayı unutmayın. Kodunuzu değiştirdikten sonra veya testleri çalıştırdığınızda kapsam sonuçları ve kod renklendirme otomatik olarak güncelleştirilmez.

## <a name="report-in-blocks-or-lines"></a>Blok veya satır içinde rapor

Kod kapsamı *bloklar*halinde sayılır. Bir blok, tek bir giriş ve çıkış noktası kodu parçasıdır.  Programın denetim akışı bir test çalışması sırasında bir blok geçerse, bu blok kapalı olarak sayılır. Blok kullanılma sayısının sonuç üzerinde etkisi yoktur.

Ayrıca, tablo başlığında **Sütun Ekle/Kaldır'ı** seçerek sonuçların satır açısından görüntülenmesini de sağlayabilirsiniz. Yüzdeler kaynak kodunda gördüğünüz parçaların boyutuyla daha yakından ilişkili olduğundan bazı kullanıcılar satırları saymayı tercih eder. Birçok satır kaplayan olsa bile uzun bir blok hesaplama tek bir blok olarak sayılacaktır.

> [!TIP]
> Kod satırı birden fazla kod bloğu içerebilir. Bu durumda ve test çalışması satırdaki tüm kod blokları egzersizleri, bir satır olarak sayılır. Satırdaki bazı ancak tüm kod blokları çalıştırılırsa, kısmi satır olarak sayılır.

## <a name="manage-code-coverage-results"></a>Kod kapsamı sonuçlarını yönetme

**Kod Kapsamı Sonuçları** penceresi genellikle en son çalıştırmanın sonucunu gösterir. Sonuçlar test verilerini değiştirirseniz veya testlerinizin her defasında yalnızca bir kısmını çalıştırırsanız değişir.

Kod kapsamı penceresini önceki sonuçları veya diğer bilgisayarlarda elde edilen sonuçları görüntülemek için de kullanılabilir.

Birçok çalıştırmanın sonucunu örneğin farklı test verileri kullanan çalışmalardan birleştirebilirsiniz.

- **Önceki sonuç kümesini görüntülemek için**açılan menüden seçin. Menü, yeni bir çözüm açtığınızda temizlenen geçici bir liste gösterir.

- **Önceki bir oturumun sonuçlarını görüntülemek için,** **İçe Aktar Kod Kapsamı Sonuçlarını**seçin, çözümünüzdeki Test **Sonuçları** klasörüne gidin ve bir .coverage dosyası içe *aktarın.*

   *.coverage* dosyası oluşturulduğundan beri kaynak kodu değişmişse, kapsam boyama yanlış olabilir.

- **Sonuçları metin olarak okunabilir hale getirmek için,** **Dışa Aktarma Kodu Kapsamı Sonuçlarını**seçin. Bu, diğer araçlarla işleyebilir veya postayla kolayca gönderilebilen okunabilir bir *.coveragexml* dosyası oluşturur.

- **Sonuçları başka birine göndermek için** *,kapsama* dosyası veya dışa aktarılan *.coveragexml* dosyasını gönderin. Sonra dosyayı içe aktarabilirsiniz. Kaynak kodun aynı sürümü varsa, kapsam renklendirmeyi görebilirsiniz.

## <a name="merge-results-from-different-runs"></a>Farklı çalıştırmaların sonuçlarını birleştirme

Bazı durumlarda, test verilerine bağlı olarak kodunuzda farklı bloklar kullanılacaktır. Bu nedenle, farklı bir test çalışmasının sonuçlarını birleştirmek isteyebilirsiniz.

Örneğin, giriş "2" ile bir test çalıştırdığınızda, belirli bir işlevin %50'sinin kapsandığını bulun. Testi "-2" girişiyle ikinci kez çalıştırdığınızda, kapsama renklendirme görünümünde işlevin diğer %50'sinin kapsandığını görürsünüz. Şimdi iki test çalışması sonuçlarını birleştirin ve işlevin %100 kapsamında rapor ve görünümü renklendirme kapsamını gösterin.

Bunu ![yapmak için Kod Kapsamı](../test/media/codecoverage-mergeicon.png) penceresinde Birleştirme düğmesi için Simge'yi kullanın **Kod Birleştirme** Sonuçları.'nda. Son çalışmaların veya alınan sonuçların herhangi bir bileşimini seçebilirsiniz. Dışa aktarılan sonuçları birleştirmek istiyorsanız, bunları önce almanız gerekir.

Birleştirme işleminin sonuçlarını kaydetmek için **Dışa Aktarma Kodu Kapsamı Sonuçlarını** kullanın.

### <a name="limitations-in-merging"></a>Birleştirmede sınırlamalar

- Kodun farklı sürümlerinden kapsama verilerini birleştirirseniz, sonuçlar ayrı ayrı gösterilir, ancak birleştirilmez. Tam olarak birleştirilmiş sonuçlar almak için test verilerini değiştirerek kodun aynı yapısını kullanın.

- Dışa ve sonra içe alınmış sonuç dosyasını birleştirirseniz, sonuçları bloklarla değil yalnızca çizgilerle görüntüleyebilirsiniz. Satır verilerini göstermek için **Sütun ları Ekle/Kaldır** komutunu kullanın.

- ASP.NET projesinin testlerinden sonuçları birleştirirseniz, birleştirilmiş değil ayrı testlerin sonuçları görüntülenir. Bu yalnızca ASP.NET yapılarına uygulanır: başka bir derleme için sonuçlar birleştirilecektir.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Öğeleri kod kapsamı sonuçlarından hariç tutma

Örneğin kodu bir metin şablonundan oluşturulan tedarik puanlarını kodunuzda belirli öğeler dışında isteyebilirsiniz. <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> Aşağıdaki kod öğelerinden herhangi biri için öznitelik ekleyin: sınıf, yapı, yöntem, özellik, özellik ayarlayıcı veya getter, olay.

> [!TIP]
> Bir sınıfı hariç tutmak, türetilen sınıfları dışlamaz.

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

### <a name="exclude-elements-in-native-c-code"></a>Yerel C++ kodundaki öğeleri hariç tutma

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

`ExcludeFromCodeCoverage(`*DışlamaAdı* `, L"` *İşadı*`");`

`ExcludeSourceFromCodeCoverage(`*DışlamaName* `, L"` *SourceFilePath*`");`

- *ExclusionName* herhangi bir benzersiz addır.

- *FunctionName* tam nitelikli bir işlev adıdır. Joker karakterler içerebilir. Örneğin, bir sınıfın tüm işlevlerini hariç tutmak için,`MyNamespace::MyClass::*`

- *SourceFilePath,* bir .cpp dosyasının yerel veya UNC yoludur. Joker karakterler içerebilir. Aşağıdaki örnek, belirli bir dizindeki tüm dosyaları hariç tutar:`\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Herhangi bir ad alanı veya sınıf içindeki değil genel ad alanındaki dışlama makroları için çağrılar yerleşir.

- Dışlamaları birim test kod dosyasına veya uygulama kod dosyasına yerleştirebilirsiniz.

- Dışlamalar, derleyici seçeneğini ayarlayarak veya `#pragma managed(off)`kullanılarak yönetilmeyen (yerel) kod olarak derlenmelidir.

> [!NOTE]
> C++/CLI kodundaki işlevleri dışlamak için, işleve özniteliği `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` uygulayın. Bu C# ile aynıdır.

### <a name="include-or-exclude-additional-elements"></a>Ek öğeler ekleme veya hariç tutma

Kod kapsamı çözümlemesi yalnızca yüklenen ve *.pdb* dosyasının *.dll* veya *.exe* dosyasıyla aynı dizinde kullanılabildiği derlemelerde gerçekleştirilir. Bu nedenle, bazı durumlarda, uygun *.pdb* dosyalarının kopyalarını alarak dahil edilen derlemeler kümesini genişletebilirsiniz.

*.runsettings* dosyası yazarak kod kapsamı çözümlemesi için hangi derlemelerin ve öğelerin seçili olduğu üzerinde daha fazla denetim yapabilirsiniz. Örneğin, kendi sınıfları için öznitelikler eklemek zorunda kalmadan belirli tür derlemeleri hariç tutabilirsiniz. Daha fazla bilgi için [kod kapsamı çözümlemesi özelleştir'e](../test/customizing-code-coverage-analysis.md)bakın.

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Azure Ardışık Hatlar'da kod kapsamını analiz edin

Kodunuzu iade ettiğinizde, testleriniz yapı sunucusunda diğer ekip üyelerinin testleriyle birlikte çalışır. Tüm projedeki kapsama alanının en güncel ve kapsamlı resmini elde etmek için Azure Ardışık Hatları'ndaki kod kapsamını çözümlemek yararlıdır. Ayrıca, genellikle geliştirme makinelerinde çalıştırmadığınız otomatik sistem testleri ve diğer kodlanmış testleri de içerir. Daha fazla bilgi için [yapılarınızın birim testlerini çalıştır'a](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)bakın.

## <a name="analyze-code-coverage-from-the-command-line"></a>Komut satırından kod kapsamını analiz edin

Komut satırından testleri çalıştırmak için *vstest.console.exe'yi*kullanın. Kod kapsamı *vstest.console.exe* yardımcı programının bir seçeneğidir.

1. Visual Studio için Geliştirici Komut Komut Ustem başlatın:

   ::: moniker range="vs-2017"

   Windows **Başlat** menüsünde, VS **2017 için Visual Studio 2017** > **Geliştirici Komut Komut Komut Ustem'ini**seçin.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   Windows **Başlat** menüsünde, VS **2019 için Visual Studio 2019** > **Geliştirici Komut Komut Komut Ustem'i**seçin.

   ::: moniker-end

2. Komut isteminde aşağıdaki komutu çalıştırın:

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

Daha fazla bilgi için [VSTest.Console.exe komut satırı seçeneklerine](vstest-console-options.md)bakın.

## <a name="troubleshoot"></a>Sorun giderme

Kod kapsamı sonuçlarını görmüyorsanız, [Sorun Giderme Kodu kapsamı](../test/troubleshooting-code-coverage.md) makalesi size yardımcı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md)
- [Kod kapsamı sorunlarını giderme](../test/troubleshooting-code-coverage.md)
- [Birim kodunuzu test edin](../test/unit-test-your-code.md)
