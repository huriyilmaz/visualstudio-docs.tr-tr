---
title: Ne kadar kodun test edildiğini öğrenmek için kod kapsamını kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- code coverage
ms.assetid: 800fc739-acd2-4242-84cb-1d83b4d82cf9
caps.latest.revision: 38
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 737311167fc1f444d5c0f8a5d2c27e2fe321da75
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851245"
---
# <a name="using-code-coverage-to-determine-how-much-code-is-being-tested"></a>Ne Kadar Kodun Test Edildiğini Belirlemek için Kod Kapsamını Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proje kodunuzun ne oranda aslında birim testleri gibi kodlanmış testler tarafından test edilen belirlemek için Visual Studio kod kapsamı özelliğini kullanabilirsiniz. Etkin hatalara karşı koruma sağlamak için testleriniz çalışmalı veya kodunuzun büyük bir kısmını 'kapsamalıdır'.

 Kod Kapsamı Çözümleme (CLI) yönetilen ve yönetilmeyen (yerel) kod için uygulanabilir.

 Test yöntemlerini Test Gezgini'ni kullanarak çalıştırdığınızda kod kapsamı bir seçenektir. Sonuçlar tablosu, her derleme sınıfı ve yöntemi içinde çalışan kod yüzdesini gösterir. Ayrıca, kaynak düzenleyici hangi kodun test edildiğini gösterir.

 ![Renklendirme ile kod kapsamı sonuçları](../test/media/codecoverage1.png "CodeCoverage1")

 **Requirements**

- Visual Studio Enterprise

### <a name="to-analyze-code-coverage-on-unit-tests-in-test-explorer"></a>Test Gezgini'ndeki birim testlerinde kod kapsamını analiz etmek için

1. **Test** menüsünde, **kod kapsamını analiz et**' i seçin.

2. Hangi satırların çalıştırıldığını görmek için ![kod kapsamı renklendirmesini göster simgesi](../test/media/codecoverage-showcoloringicon.png "CodeCoverage-Showcoloringıcon")**kod kapsamı renklendirmesini göster**' i seçin.

     Renkleri değiştirmek veya kalın yüz kullanmak için **Araçlar**, **Seçenekler**, **ortam**, **yazı tipleri ve renkler**' i seçin, **ayarları göster: metin düzenleyici**. **Görüntüleme öğeleri**altında, kapsam öğelerini ayarlayın.

3. Sonuçlar düşük kapsamı gösterirse, hangi kod parçalarının uygulanmadığını araştırın ve bunları kapsamak için daha fazla test yazın. Geliştirme ekipleri için tipik olarak yaklaşık %80 kod kapsamı hedeflenir. Bazı durumlarda, düşük kapsam kabul edilebilir. Örneğin, düşük kapsamı bazı kodlar standart şablonundan oluşturulduğu kabul edilebilir.

> [!TIP]
> Doğru sonuçlar elde etmek için:
>
> - Bu derleyici optimizasyonunun kapalı olduğundan emin olun.
>
>   Yönetilmeyen (yerel) kod ile çalışıyorsanız, bir hata ayıklama yapısı kullanın.
>   - Her derleme için .pdb (simge) dosyaları oluşturduğunuzdan emin olun.
>
>   Tahmin ettiğiniz sonuçları alamazsanız bkz. [sorun giderme kodu kapsamı](../test/troubleshooting-code-coverage.md). . Kod kapsamını kod güncelleştirdikten sonra çalıştırmayı unutmayın. Kodunuzu değiştirdikten sonra veya testleri çalıştırdığınızda kapsam sonuçları ve kod renklendirme otomatik olarak güncelleştirilmez.

## <a name="reporting-in-blocks-or-lines"></a>Bloklarda veya satırlarda raporlama
 Kod kapsamı *bloklar*halinde sayılır. Bir blok, tek bir giriş ve çıkış noktası kodu parçasıdır.  Programın denetim akışı bir test çalışması sırasında bir blok geçerse, o blok anlatıldığı gibi sayılır. Blok kullanılma sayısının sonuç üzerinde etkisi yoktur.

 Ayrıca, tablo üst bilgisinde **sütun Ekle/Kaldır** ' a tıklayarak da sonuçları satır bakımından görüntülenmesini sağlayabilirsiniz. Test, kodun herhangi bir satırında tüm kod bloklarına uygulanırsa, tek satır olarak sayılır. Uygulanan ve uygulanmayan bazı kod blokları bir satır içerdiğinde bu kısmi bir satır olarak sayılır.

 Yüzdeler kaynak kodunda gördüğünüz parçaların boyutuyla daha yakından ilişkili olduğundan bazı kullanıcılar satırları saymayı tercih eder. Birçok satır kaplayan olsa bile uzun bir blok hesaplama tek bir blok olarak sayılacaktır.

## <a name="managing-code-coverage-results"></a>Kod kapsama sonuçlarını yönetme
 Kod Kapsama Sonuçları penceresi genellikle en son çalıştırma sonucunu gösterir. Sonuçlar test verilerini değiştirirseniz veya testlerinizin her defasında yalnızca bir kısmını çalıştırırsanız değişir.

 Kod kapsamı penceresini önceki sonuçları veya diğer bilgisayarlarda elde edilen sonuçları görüntülemek için de kullanılabilir.

 Birçok çalıştırmanın sonucunu örneğin farklı test verileri kullanan çalışmalardan birleştirebilirsiniz.

- **Önceki bir sonuç kümesini görüntülemek için**, açılan menüden seçin. Menü, yeni bir çözüm açtığınızda temizlenen geçici bir liste gösterir.

- **Önceki bir oturumdan sonuçları görüntülemek için**, **kod kapsamı sonuçlarını içeri aktar**' ı seçin, çözümünüzde TestResults klasörüne gidin ve bir. Coverage dosyasını içeri aktarın.

     Karşılama renklendirme .coverage dosyası oluşturulurken kaynak kodu değişirse yanlış olabilir.

- **Sonuçları metin olarak okunabilir hale getirmek Için** **kod kapsamı sonuçlarını dışarı aktar**' ı seçin. Bu, diğer araçlarla işlemek veya kolayca posta ile göndermek okunabilir .coveragexml dosyasını oluşturur.

- **Başka birine sonuç göndermek için**bir. Coverage dosyası ya da aktarılmış bir. veXML dosyası gönderin. Sonra dosyayı içe aktarabilirsiniz. Kaynak kodun aynı sürümü varsa, kapsam renklendirmeyi görebilirsiniz.

## <a name="merging-results-from-different-runs"></a>Farklı çalışmalardan sonuçları birleştirme
 Bazı durumlarda, test verilerine bağlı olarak kodunuzda farklı bloklar kullanılacaktır. Bu nedenle, farklı bir test çalışmasının sonuçlarını birleştirmek isteyebilirsiniz.

 Örneğin, giriş "2" ile bir test çalıştırdığınızda, belirli bir işlevin %50'sinin kapsandığını bulun. Giriş "-2" ile ikinci kez test çalıştırdığınızda diğer %50'si işlev kapsamında görünüm renklendirme kapsamına bakın. Şimdi iki test çalışması sonuçlarını birleştirin ve işlevin %100 kapsamında rapor ve görünümü renklendirme kapsamını gösterin.

 ![Kod kapsamı penceresinde birleştirme Için simgeyi kullanın Bu,](../test/media/codecoverage-mergeicon.png "CodeCoverage-Mergeıcon")**kod kapsamı sonuçlarını birleştirerek** bunu yapın. Son çalışmaların veya alınan sonuçların herhangi bir bileşimini seçebilirsiniz. Dışa aktarılan sonuçları birleştirmek istiyorsanız, bunları önce almanız gerekir.

 Birleştirme işleminin sonuçlarını kaydetmek için **kod kapsamı sonuçlarını dışarı aktarma** ' yı kullanın.

### <a name="limitations-in-merging"></a>Birleştirmede sınırlamalar

- Kodun farklı sürümlerinden kapsama verilerini birleştirirseniz, sonuçlar ayrı ayrı gösterilir, ancak birleştirilmez. Tam olarak birleştirilmiş sonuçlar almak için test verilerini değiştirerek kodun aynı yapısını kullanın.

- Dışa ve sonra içe alınmış sonuç dosyasını birleştirirseniz, sonuçları bloklarla değil yalnızca çizgilerle görüntüleyebilirsiniz. Satır verilerini göstermek için **Sütunları Ekle/Kaldır** komutunu kullanın.

- ASP.NET projesinin testlerinden sonuçları birleştirirseniz, birleştirilmiş değil ayrı testlerin sonuçları görüntülenir. Bu yalnızca ASP.NET yapılarına uygulanır: başka bir derleme için sonuçlar birleştirilecektir.

## <a name="excluding-elements-from-the-code-coverage-results"></a>Kod kapsamı sonuçlarından öğeleri hariç tut
 Örneğin kodu bir metin şablonundan oluşturulan tedarik puanlarını kodunuzda belirli öğeler dışında isteyebilirsiniz. Aşağıdaki kod öğelerinden herhangi birine `System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverage` özniteliği ekleyin: sınıf, yapı, yöntem, özellik, özellik ayarlayıcı veya alıcı, olay. Hariç tutulan bir sınıfın türetilmiş sınıfları dışarıda tuttuğunu unutmayın.

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

```cpp#
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

### <a name="excluding-elements-in-native-c-code"></a>Yerel C++ kod öğeleri hariç
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

 `ExcludeFromCodeCoverage(` *Exclusionname* `, L"` *fonksiyonadı* `");`

 `ExcludeSourceFromCodeCoverage(` *Exclusionname* `, L"` *SourceFilePath* `");`

- *Exclusionname* herhangi bir benzersiz addır.

- *Fonksiyonadı* tam olarak nitelenmiş bir işlev adıdır. Joker karakterler içerebilir. Örneğin, bir sınıfın tüm işlevlerini dışlamak için, `MyNamespace::MyClass::*` yazın

- *SourceFilePath* , bir. cpp dosyasının yerel veya UNC yoludur. Joker karakterler içerebilir. Aşağıdaki örnek, belirli bir dizindeki tüm dosyaları dışlar: `\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Herhangi bir ad alanı veya sınıf içindeki değil genel ad alanındaki dışlama makroları için çağrılar yerleşir.

- Dışlamaları birim test kod dosyasına veya uygulama kod dosyasına yerleştirebilirsiniz.

- Dışlamaları, derleyici seçeneği ayarlanarak veya `#pragma managed(off)`kullanılarak yönetilmeyen (yerel) kod olarak derlenmelidir.

> [!NOTE]
> C++/CLI kodundaki işlevleri dışlamak için, `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` özniteliği işleve uygulayın. Bu C# ile aynıdır.

### <a name="including-or-excluding-additional-elements"></a>Dahil veya hariç ek öğeler
 Kod kapsamı çözümlemesi yüklü olan ve bir .pdb dosyası .dll veya .exe dosyası ile aynı dizinde bulunan derlemeler üzerinde yapılır. Bu nedenle bazı durumlarda uygun .pdb dosyalarının kopyalarını alarak eklenen derleme kümesini genişletebilirsiniz.

 .runsettings dosyasını yazarak seçilen kod kapsamı çözümleme derlemeleri ve öğeleri üzerinde daha fazla denetimle alıştırma yapabilirsiniz. Örneğin, kendi sınıfları için öznitelikler eklemek zorunda kalmadan belirli tür derlemeleri hariç tutabilirsiniz. Daha fazla bilgi için bkz. [kod kapsamı analizini özelleştirme](../test/customizing-code-coverage-analysis.md).

## <a name="analyzing-code-coverage-in-the-build-service"></a>Yapı hizmetindeki kod kapsamı çözümleme
 Kodunuzda denetlediğinizde, testiniz diğer ekip üyelerinden gelen diğer tüm testlerle birlikte yapı sunucusunda çalışır. (Bu ayarı zaten ayarlamadıysanız, bkz. [Yapı sürecinizdeki testleri çalıştırma](https://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38).) Derleme hizmetinde kod kapsamını analiz etmek yararlı olur çünkü bu, tüm projede en güncel ve kapsamlı kapsama görünümünü sağlar. Otomatik sistem testleri ve geliştirme makinelerinde genellikle çalıştırmadığınız kodlanmış diğer testleri de içerecektir.

1. Takım Gezgini ' de, **derlemeler**' ı açın ve ardından bir yapı tanımı ekleyin veya düzenleyin.

2. **İşlem** sayfasında **otomatik testler**, **test kaynağı**, **çalıştırma ayarları**' nı genişletin. **Çalışma ayarları dosyasının türünü** **kod kapsamı etkin**olarak ayarlayın.

    Birden fazla Test Kaynağı tanımı varsa, her biri için bu adımı yineleyin.

   - <em>Ancak **tür çalışma ayarları dosyası adında bir</em>alan yok*. *

      **Otomatikleştirilmiş testler**altında, **Test derlemesi** ' ni seçin ve satırın sonundaki üç nokta düğmesini **[...]** seçin. **Test çalıştırması Ekle/Düzenle** iletişim kutusunda, **Test Çalıştırıcısı**' nın altında, **Visual Studio Test Çalıştırıcısı**' nı seçin.

   ![Kod kapsamı için derleme tanımı ayarlanıyor](../test/media/codecoverage-plaincc.png "CodeCoverage-plainCC")

   Yapı çalıştıktan sonra kod kapsamı sonuçları test çalıştırmasına eklenir ve yapı özet olarak görünür.

## <a name="analyzing-code-coverage-in-a-command-line"></a>Komut Satırında Kod Kapsamı Çözümleme
 Komut satırından testleri çalıştırmak için vstest.console.exe kullanın. Kod kapsamı, bu yardımcı programın bir seçeneğidir. Daha fazla bilgi için bkz. [VSTest. Console. exe komut satırı seçenekleri](https://msdn.microsoft.com/library/52e1689d-b1a8-4589-bd98-99a55acd0a11).

1. Visual Studio Geliştirici Komut Satırını başlatın:

     Windows **Başlat** menüsünde, **tüm programlar**, **Microsoft Visual Studio**, **Visual Studio Araçları** **Geliştirici komut istemi**' ı seçin.

2. Çalıştırın:

     `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage`

## <a name="troubleshooting"></a>Sorun giderme
 Kod kapsamı sonuçlarını görmüyorsanız bkz. [sorun giderme kodu kapsamı](../test/troubleshooting-code-coverage.md).

## <a name="external-resources"></a>Dış kaynaklar

### <a name="guidance"></a>Kılavuz
 [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 2: birim testi: Içini test etme](https://msdn.microsoft.com/library/jj159340.aspx)

## <a name="see-also"></a>Ayrıca Bkz.
 [Kod kapsamı Analizi](../test/customizing-code-coverage-analysis.md) [sorunlarını giderme kodu kapsam](../test/troubleshooting-code-coverage.md) [birimi test](../test/unit-test-your-code.md) kodunuzu özelleştirme
