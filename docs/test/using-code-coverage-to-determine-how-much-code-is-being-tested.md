---
title: Kod kapsamı testi
description: Visual Studio 'nun kod kapsamı özelliğini kullanarak, kodlanmış testler tarafından proje kodunuzun ne oranlarından hangilerinin test edildiğini öğrenin.
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
manager: jillfra
ms.openlocfilehash: c2c7bcb270184bcc140dbadef63af1315df765dc
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330062"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Kod kapsamını kullanarak ne kadar kodun test edildiğini belirleme

Proje kodunuzun ne oranda aslında birim testleri gibi kodlanmış testler tarafından test edilen belirlemek için Visual Studio kod kapsamı özelliğini kullanabilirsiniz. Etkin hatalara karşı koruma sağlamak için testleriniz çalışmalı veya kodunuzun büyük bir kısmını 'kapsamalıdır'.

Kod Kapsamı Çözümleme (CLI) yönetilen ve yönetilmeyen (yerel) kod için uygulanabilir.

Test yöntemlerini Test Gezgini'ni kullanarak çalıştırdığınızda kod kapsamı bir seçenektir. Sonuçlar tablosu, her derleme sınıfı ve yöntemi içinde çalışan kod yüzdesini gösterir. Ayrıca, kaynak düzenleyici hangi kodun test edildiğini gösterir.

::: moniker range="vs-2017"

![Renklendirme ile kod kapsamı sonuçları](../test/media/codecoverage1.png)

::: moniker-end

## <a name="requirements"></a>Gereksinimler

Kod kapsamı özelliği yalnızca Visual Studio Enterprise sürümünde kullanılabilir.

## <a name="analyze-code-coverage"></a>Kod kapsamını analiz et

::: moniker range="vs-2017"

1. **Test** menüsünde, **kod kapsamını analiz et**' i seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. **Test** menüsünde, **Tüm testler Için kod kapsamını çözümle**' yi seçin.

   ![VS 2019 ' de kod kapsamı menüsünü çözümle](../test/media/vs-2019/analyze-code-coverage.png)

   Kod kapsamını test Gezgini araç penceresinden de çalıştırabilirsiniz.

::: moniker-end

2. Testler çalıştırıldıktan sonra, hangi satırların çalıştırıldığını görmek için ![ kod kapsamı renklendirmesi simgesini göster ' i seçin ](../test/media/codecoverage-showcoloringicon.png) . kod **kapsamı sonuçları** penceresinde kod **kapsamı renklendirmesini göster** ' i seçin. Varsayılan olarak, testlerin kapsadığı kod açık mavi renkle vurgulanır.

   > [!TIP]
   > Renkleri değiştirmek veya kalın yüzü kullanmak için **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **yazı tipleri ve renkler**  >  **ayarları göster: metin düzenleyici**. **Görüntüleme öğeleri** altında, "kapsam" öğeleri için ayarları ayarlayın, örneğin, **kapsam dokunulmayan alanı**.
   >
   > ![Kod kapsamı yazı tipleri ve renkler](media/vs-2019/coverage-fonts-and-colors.png)

3. Sonuçlar düşük kapsamı gösterirse, hangi kod parçalarının uygulanmadığını araştırın ve bunları kapsamak için daha fazla test yazın. Geliştirme ekipleri için tipik olarak yaklaşık %80 kod kapsamı hedeflenir. Bazı durumlarda, düşük kapsam kabul edilebilir. Örneğin, düşük kapsamı bazı kodlar standart şablonundan oluşturulduğu kabul edilebilir.

> [!TIP]
> - Derleyici iyileştirmesini kapat
> - Yönetilmeyen (yerel) kodla çalışıyorsanız bir hata ayıklama derlemesi kullanın
> - Her derleme için. pdb (sembol) dosyaları oluştur

Tahmin ettiğiniz sonuçları alamazsanız bkz. [kod kapsamı sorunlarını giderme](../test/troubleshooting-code-coverage.md).

Kodunuzu güncelleştirdikten sonra kod kapsamını çalıştırmayı unutmayın. Kodunuzu değiştirdikten sonra veya testleri çalıştırdığınızda kapsam sonuçları ve kod renklendirme otomatik olarak güncelleştirilmez.

## <a name="report-in-blocks-or-lines"></a>Bloklar veya satırlarda raporla

Kod kapsamı *bloklar* halinde sayılır. Bir blok, tek bir giriş ve çıkış noktası kodu parçasıdır.  Programın denetim akışı test çalışması sırasında bir bloktan geçerse, bu blok kapsanmış olarak sayılır. Blok kullanılma sayısının sonuç üzerinde etkisi yoktur.

Ayrıca, tablo üst bilgisinde **sütun Ekle/Kaldır** ' a tıklayarak da sonuçları satır bakımından görüntülenmesini sağlayabilirsiniz. Yüzdeler kaynak kodunda gördüğünüz parçaların boyutuyla daha yakından ilişkili olduğundan bazı kullanıcılar satırları saymayı tercih eder. Birçok satır kaplayan olsa bile uzun bir blok hesaplama tek bir blok olarak sayılacaktır.

> [!TIP]
> Kod satırı, birden fazla kod bloğu içerebilir. Böyle bir durum söz konusu ise ve test çalıştırması satırdaki tüm kod bloklarını alıştırmalarda, tek bir satır olarak sayılır. Satırdaki tüm kod blokları yoksa, kısmi satır olarak sayılır.

## <a name="manage-code-coverage-results"></a>Kod kapsamı sonuçlarını yönetme

**Kod kapsamı sonuçları** penceresi genellikle en son çalıştırmanın sonucunu gösterir. Sonuçlar test verilerini değiştirirseniz veya testlerinizin her defasında yalnızca bir kısmını çalıştırırsanız değişir.

Kod kapsamı penceresini önceki sonuçları veya diğer bilgisayarlarda elde edilen sonuçları görüntülemek için de kullanılabilir.

Birçok çalıştırmanın sonucunu örneğin farklı test verileri kullanan çalışmalardan birleştirebilirsiniz.

- **Önceki bir sonuç kümesini görüntülemek için**, açılan menüden seçin. Menü, yeni bir çözüm açtığınızda temizlenen geçici bir liste gösterir.

- **Önceki bir oturumdan sonuçları görüntülemek için**, **kod kapsamı sonuçlarını içeri aktar**' ı seçin, çözümünüzde **TestResults** klasörüne gidin ve bir *. Coverage* dosyasını içeri aktarın.

   Kaynak kodu *. kapsam* dosyası oluşturulduktan sonra değiştiyse, kapsam renklendirme yanlış olabilir.

- **Sonuçları metin olarak okunabilir hale getirmek Için** **kod kapsamı sonuçlarını dışarı aktar**' ı seçin. Bu, diğer araçlarla işlem yapmak veya e-posta ile kolayca göndermek için okunabilir bir *. katarexml* dosyası oluşturur.

- **Başka birine sonuç göndermek için** bir *. Coverage* dosyası ya da aktarılmış bir *. veXML* dosyası gönderin. Sonra dosyayı içe aktarabilirsiniz. Kaynak kodun aynı sürümü varsa, kapsam renklendirmeyi görebilirsiniz.

## <a name="merge-results-from-different-runs"></a>Farklı çalıştırmaların sonuçlarını birleştirme

Bazı durumlarda, test verilerine bağlı olarak kodunuzda farklı bloklar kullanılacaktır. Bu nedenle, farklı bir test çalışmasının sonuçlarını birleştirmek isteyebilirsiniz.

Örneğin, giriş "2" ile bir test çalıştırdığınızda, belirli bir işlevin %50'sinin kapsandığını bulun. "-2" girişiyle ikinci kez testi çalıştırdığınızda, işlevin diğer %50 ' inin ele alınmasının kapsam renklendirme görünümünde görürsünüz. Şimdi iki test çalışması sonuçlarını birleştirin ve işlevin %100 kapsamında rapor ve görünümü renklendirme kapsamını gösterin.

![Kod kapsamı penceresinde birleştirme için simgeyi kullanın Bu, ](../test/media/codecoverage-mergeicon.png) **kod kapsamı sonuçlarını birleştirerek** bunu yapın. Son çalışmaların veya alınan sonuçların herhangi bir bileşimini seçebilirsiniz. Dışa aktarılan sonuçları birleştirmek istiyorsanız, bunları önce almanız gerekir.

Birleştirme işleminin sonuçlarını kaydetmek için **kod kapsamı sonuçlarını dışarı aktarma** ' yı kullanın.

### <a name="limitations-in-merging"></a>Birleştirmede sınırlamalar

- Kodun farklı sürümlerinden kapsama verilerini birleştirirseniz, sonuçlar ayrı ayrı gösterilir, ancak birleştirilmez. Tam olarak birleştirilmiş sonuçlar almak için test verilerini değiştirerek kodun aynı yapısını kullanın.

- Dışa ve sonra içe alınmış sonuç dosyasını birleştirirseniz, sonuçları bloklarla değil yalnızca çizgilerle görüntüleyebilirsiniz. Satır verilerini göstermek için **Sütunları Ekle/Kaldır** komutunu kullanın.

- ASP.NET projesinin testlerinden sonuçları birleştirirseniz, birleştirilmiş değil ayrı testlerin sonuçları görüntülenir. Bu yalnızca ASP.NET yapılarına uygulanır: başka bir derleme için sonuçlar birleştirilecektir.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Kod kapsamı sonuçlarından öğeleri hariç tut

Örneğin kodu bir metin şablonundan oluşturulan tedarik puanlarını kodunuzda belirli öğeler dışında isteyebilirsiniz. <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName>Aşağıdaki kod öğelerinden herhangi birine özniteliği ekleyin: Class, struct, Method, Property, Property Setter veya getter, Event.

> [!TIP]
> Bir sınıfın dışlanması türetilmiş sınıfları dışlamaz.

Örneğin:

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

### <a name="exclude-elements-in-native-c-code"></a>Yerel C++ kodundaki öğeleri hariç tut

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

`ExcludeFromCodeCoverage(`*Exclusionname* `, L"` *Fonksiyonadı*`");`

`ExcludeSourceFromCodeCoverage(`*Exclusionname* `, L"` *SourceFilePath*`");`

- *Exclusionname* herhangi bir benzersiz addır.

- *Fonksiyonadı* tam olarak nitelenmiş bir işlev adıdır. Joker karakterler içerebilir. Örneğin, bir sınıfın tüm işlevlerini dışlamak için şunu yazın `MyNamespace::MyClass::*`

- *SourceFilePath* , bir. cpp dosyasının yerel veya UNC yoludur. Joker karakterler içerebilir. Aşağıdaki örnek, belirli bir dizindeki tüm dosyaları dışlar: `\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Herhangi bir ad alanı veya sınıf içindeki değil genel ad alanındaki dışlama makroları için çağrılar yerleşir.

- Dışlamaları birim test kod dosyasına veya uygulama kod dosyasına yerleştirebilirsiniz.

- Dışlamaları, derleyici seçeneği ayarlanarak veya kullanılarak yönetilmeyen (yerel) kod olarak derlenmelidir `#pragma managed(off)` .

> [!NOTE]
> C++/CLı kodundaki işlevleri dışlamak için, işlevine özniteliğini uygulayın `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` . Bu C# ile aynıdır.

### <a name="include-or-exclude-additional-elements"></a>Ek öğeleri dahil etme veya dışlama

Kod kapsamı Analizi yalnızca yüklenmiş ve. *pdb* dosyası *. dll* veya *. exe* dosyası ile aynı dizinde kullanılabilen derlemelerde gerçekleştirilir. Bu nedenle, bazı durumlarda, uygun *. pdb* dosyalarının kopyalarını alarak dahil edilen derleme kümesini genişletebilirsiniz.

Bir *. runsettings* dosyası yazarak kod kapsamı analizi için hangi derlemelerin ve öğelerin seçildiği hakkında daha fazla denetim gerçekleştirebilirsiniz. Örneğin, kendi sınıfları için öznitelikler eklemek zorunda kalmadan belirli tür derlemeleri hariç tutabilirsiniz. Daha fazla bilgi için bkz. [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Azure Pipelines kod kapsamını analiz etme

Kodunuzu iade ettiğinizde, testleriniz yapı sunucusunda diğer takım üyelerinden gelen testlerle birlikte çalışır. Tüm projede en güncel ve kapsamlı kapsama görünümünü almak için Azure Pipelines kod kapsamını çözümlemek yararlı olur. Ayrıca, genellikle geliştirme makinelerinde çalıştırılmamaları için otomatikleştirilmiş Sistem testlerini ve diğer kodlanmış testleri de içerir. Daha fazla bilgi için bkz. [Derlemelerinizle birim testlerini çalıştırma](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true).

## <a name="analyze-code-coverage-from-the-command-line"></a>Komut satırından kod kapsamını analiz etme

Komut satırından testleri çalıştırmak için *vstest.console.exe* kullanın. Kod kapsamı *vstest.console.exe* yardımcı programının bir seçeneğidir.

1. Visual Studio için Geliştirici Komut İstemi başlatın:

   ::: moniker range="vs-2017"

   Windows **Başlat** menüsünde, vs 2017 için **Visual Studio 2017** > **Geliştirici komut istemi** seçin.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   Windows **Başlat** menüsünde, vs 2019 için **Visual Studio 2019** > **Geliştirici komut istemi** seçin.

   ::: moniker-end

2. Komut isteminde aşağıdaki komutu çalıştırın:

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

Daha fazla bilgi için bkz. [VSTest.Console.exe komut satırı seçenekleri](vstest-console-options.md).

## <a name="troubleshoot"></a>Sorun giderme

Kod kapsamı sonuçlarını görmüyorsanız, [kod kapsamı sorunlarını giderme](../test/troubleshooting-code-coverage.md) makalesinde size yardımcı olabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md)
- [Kod kapsamı sorunlarını giderme](../test/troubleshooting-code-coverage.md)
- [Kodunuzun birim testi](../test/unit-test-your-code.md)
