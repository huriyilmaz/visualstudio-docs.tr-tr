---
title: Kod kapsamı analizini özelleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f6337c35-acae-4c5f-b5d9-ac5ff687ef18
caps.latest.revision: 18
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2a78c10b125379d1b4aa284d4b2ff6e999b80f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660593"
---
# <a name="customizing-code-coverage-analysis"></a>Kod Kapsamı Çözümlemeyi Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Code kapsam Aracı, varsayılan olarak birim testleri sırasında yüklenen tüm çözüm derlemelerini (. exe/. dll) analiz eder. Çoğu zaman iyi çalıştığı için bu varsayılanı korumanız önerilir. Daha fazla bilgi için bkz. kod [kapsamını kullanarak ne kadar kodun test edildiğini belirleme](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

 Kod kapsamı davranışını özelleştirmeden önce bazı alternatifleri düşünün:

- *Kod kapsamı sonuçlarından test kodunu dışlamak ve yalnızca uygulama kodunu dahil etmek istiyorum.*

   Öğesini `ExcludeFromCodeCoverage Attribute` Test sınıfınıza ekleyin.

- *Çözümmin parçası olmayan derlemeler eklemek istiyorum.*

   Bu derlemeler için .pdb dosyalarını alın ve bunları derleme .dll dosyaları gibi aynı klasöre kopyalayın.

  Kod kapsamı davranışını özelleştirmek için, [Bu konunun sonundaki örneği](#sample) kopyalayın ve. runsettings dosya uzantısını kullanarak çözümünüze ekleyin. Kendi gereksinimlerinize göre düzenleyin ve ardından **Test** menüsünde test **ayarları**' nı seçin, **Test ayarları** dosyası ' nı seçin. Bu konunun geri kalanını bu yordam daha ayrıntılı biçimde açıklar.

## <a name="the-runsettings-file"></a>.runsettings dosyası
 Gelişmiş kod kapsamı ayarları .runsettings dosyasında belirtilir. Bu, birim test etme araçları tarafından kullanılan yapılandırma dosyasıdır. [Bu konunun sonundaki örneği](#sample) kopyalamanızı ve kendi gereksinimlerinize uyacak şekilde düzenlemenizi öneririz.

- *Visual Studio 2010 ' de kullandığım. testsettings dosyasına ne oldu?*

   Visual Studio 2010'da .testsettings dosyası MSTest çerçevesine dayalı birim testleri için geçerlidir. Visual Studio 2012'de test araçları yalnızca MSTest için değil aynı zamanda NUnit ve xUnit.net gibi diğer çerçeveler için de uygulanır. .testsettings dosyası bu işe yaramaz. .runsettings dosyası, tüm test çerçeveleri ile çalışacak şekilde test araçlarını özelleştirmek için tasarlanmıştır.

  Kod kapsamını özelleştirmek için çözümünüze bir .runsettings dosyası eklemeniz gerekir:

1. Uzantıya sahip bir çözüm öğesi olarak bir. xml dosyası ekleyin `.runsettings` :

    Çözüm Gezgini, çözümünüzün kısayol menüsünde, **Ekle**, **Yeni öğe**' yi seçin ve **XML dosyası**' nı seçin. Dosyayı şu şekilde biten bir adla kaydedin `CodeCoverage.runsettings`

2. Bu konunun sonundaki örnekte verilen içerik ekleyin ve sonra gereksinimleriniz için aşağıdaki bölümlerde açıklandığı şekilde özelleştirin.

3. **Test** menüsünde **Test ayarları**' nı seçin, **Test ayarları dosyası** ' nı seçin ve dosyayı seçin.

4. Şimdi **kod kapsamını çözümle**' yi çalıştırdığınızda bu `.runsettings` Dosya davranışını kontrol eder. Kod kapsamını yeniden çalıştırmanız gerektiğini unutmayın: testleri çalıştırdığınızda veya kodunuzu güncelleştirdiğinizde önceki kapsam sonuçları ve kod renklendirme otomatik olarak gizli değildir.

5. Özel ayarları kapatmak ve açmak için **Test**, **Test ayarları** menüsünde dosya seçimini kaldırın veya seçin.

   ![Özel ayarlar dosyası ile test ayarları menüsü](../test/media/codecoverage-settingsfile.png "CodeCoverage-settingsFile")

   Birim testlerinin diğer yönleri aynı .runsettings dosyasında yapılandırılabilir. Daha fazla bilgi için bkz. [birim testi kodunuz](../test/unit-test-your-code.md).

### <a name="specifying-symbol-search-paths"></a>Simge arama yolu belirtme
 Kod kapsamı bulunan derlemeler için simgeleri (.pdb dosyaları) gerektirir. Çözümünüz tarafından oluşturulmuş derlemeler için, simge dosyaları genellikle ikili dosyalarda bulunur ve kod kapsamı otomatik olarak çalışır. Ancak bazı durumlarda, kod kapsamı çözümlemenizde başvurulmuş derlemeleri eklemek isteyebilirsiniz. Bu gibi durumlarda .pdb dosyaları ikili bitişik olmayabilir, ancak .runsettings dosyasında simge arama yolu belirtebilirsiniz.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>

```

> [!WARNING]
> Sembol çözünürlük özellikle pek çok derlemeyle uzak dosya konumu kullanırken zaman alabilir. Bu nedenle, ikili (.dll ve .exe) dosyaları ile aynı yerel konuma uzak .pdb dosyalarını kopyalamayı düşünün.

### <a name="excluding-and-including"></a>Dahil ve hariç
 Belirtilen derleme kod kapsamını çözümleme dışı bırakabilirsiniz. Örneğin:

```minterastlib
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

 Alternatif olarak, hangi derlemelerin dahil edileceğini belirtebilirsiniz. Bu yaklaşımın daha fazla derlemeleri çözümü eklediğinizde dezavantajı vardır, listeye eklemeyi unutmamalısınız:

```minterastlib
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

 `<Include>`Boşsa, kod kapsamı işleme, yüklenen ve için **. pdb** dosyalarının bulunduğu tüm derlemeleri (. dll ve. exe dosyaları), bir listedeki yan tümcesiyle eşleşen öğeler dışında içerir `<Exclude>` .

 `Include` daha önce işlenir `Exclude` .

### <a name="regular-expressions"></a>Normal ifadeler
 Dahil ve hariç düğümler normal ifadeler kullanır. Daha fazla bilgi için bkz. [Visual Studio 'Da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md). Normal ifadeler joker karakterler ile aynı değildir. Özellikle:

1. **\.\\*** herhangi bir karakter dizesiyle eşleşir

2. **\\.** bir noktayla eşleşir ".")

3. ** \\ ( \\ )** parantezle eşleşir "()"

4. **\\\\** bir dosya yolu sınırlayıcısı ile eşleşir " \\ "

5. **^** dizenin başlangıcını eşleştirir

6. **$** dizenin sonuyla eşleşir

   Tüm eşlemeler büyük/küçük harf duyarsızdır.

   Örneğin:

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>

```

> [!WARNING]
> Atlatılamayan ve eşleşmeyen parantezler gibi normal ifadede bir hata varsa kod kapsamı çözümleme çalışmaz.

### <a name="other-ways-to-include-or-exclude-elements"></a>Öğeleri içerecek veya dışlayacak diğer yollar
 Örnekler için [Bu konunun sonundaki örneğe](#sample) bakın.

- `ModulePath` – Derleme dosyası yolu tarafından belirtilen derlemeler.

- `CompanyName` – derlemeler şirket özniteliğiyle eşleşir.

- `PublicKeyToken` – imzalı derlemeleri ortak anahtar belirteci ile eşleştirir. Örneğin, tüm Visual Studio bileşenlerini ve uzantılarını eşleştirmek için kullanın `<PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>` .

- `Source` – öğelerin tanımlandıkları kaynak dosyanın yol adına göre eşleşir.

- `Attribute` – belirli bir özniteliğin eklendiği öğelerle eşleşir. Adın sonunda "Öznitelik" dahil özniteliğin tam adını belirtin.

- `Function` – tam ad ile yordamları, işlevleri veya yöntemleri eşleştirir.

  **İşlev adıyla eşleşen**

  Normal ifadenizin tam ad alanı, sınıf adı, yöntemin adı ve parametre listesi de dahil olmak üzere, işlev adıyla eşleşmesi gerekir. Örneğin,

- C# veya Visual Basic: `Fabrikam.Math.LocalMath.SquareRoot(double)`

- C++  `Fabrikam::Math::LocalMath::SquareRoot(double)`

```xml
<Functions>
  <Include>
    <!-- Include methods in the Fabrikam namespace: -->
    <Function>^Fabrikam\..*</Function>
    <!-- Include all methods named EqualTo: -->
    <Function>.*\.EqualTo\(.*</Function>
  </Include>
  <Exclude>
    <!-- Exclude methods in a class or namespace named UnitTest: -->
    <Function>.*\.UnitTest\..*</Function>
  </Exclude>
</Functions>

```

## <a name="how-to-specify-runsettings-files-while-running-tests"></a>Testleri çalıştırırken .runsettings dosyaları belirleme

### <a name="to-customize-runsettings-in-visual-studio-tests"></a>Visual Studio testlerinde runsettings özelleştirmek için
 **Test**, **Test ayarları**' nı seçin, **Test ayarları dosyası** ' nı seçin ve. runsettings dosyasını seçin. Dosya, Test Ayarları menüsünde görünür ve seçebilir veya iptal edebilirsiniz. Seçildiğinde,. runsettings dosyanız, **kod kapsamını çözümle**'yı her kullandığınızda geçerlidir.

### <a name="to-customize-run-settings-in-a-command-line-test"></a>Komut satırı testinde ayarları çalıştırmayı özelleştirmek için
 Komut satırından testleri çalıştırmak için vstest.console.exe kullanın. Ayarlar dosyası, bu yardımcı programın bir parametresidir. Daha fazla bilgi için bkz. [komut satırından VSTest. Console kullanma](https://msdn.microsoft.com/library/852812d8-b3bb-407e-bc43-04d511fcb27a).

1. Visual Studio Geliştirici Komut Satırını başlatın:

     Windows **Başlat**' da, **tüm programlar**, **Microsoft Visual Studio**, **Visual Studio Araçları** **Geliştirici komut istemi**' ı seçin.

2. Çalıştır:

     `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings`

### <a name="to-customize-run-settings-in-a-build-definition"></a>Bir yapı tanımında ayarları çalıştırmayı özelleştirmek için
 Bir takım yapısından kod kapsama verisi elde edebilirsiniz.

 ![Yapı tanımında runsettings belirtme](../test/media/codecoverage-buildrunsettings.png "CodeCoverage-buildRunsettings")

1. .runsettings dosyanızın işaretli olduğundan emin olun.

2. Takım Gezgini ' de, **derlemeler**' ı açın ve ardından bir yapı tanımı ekleyin veya düzenleyin.

3. **İşlem** sayfasında **otomatik testler**, **test kaynağı**, **çalıştırma ayarları**' nı genişletin. **. Runsettings** dosyanızı seçin.

   - <em>Ancak test **derlemesi</em>* **test kaynağı**yerine görüntülenir. **Çalışma ayarları** alanını ayarlamaya çalıştığımda yalnızca. testsettings dosyaları seçebilirsiniz.*

      **Otomatikleştirilmiş testler**altında, **Test derlemesi**' ni seçin ve satırın sonundaki **[...]** seçeneğini belirleyin. **Test çalıştırması Ekle/Düzenle** iletişim kutusunda, **Test Çalıştırıcısı** 'Nı **Visual Studio Test Çalıştırıcısı**olarak ayarlayın.

   Sonuçlar yapı raporunun özet bölümünde görünürdür.

## <a name="sample-runsettings-file"></a><a name="sample"></a> Sample. runsettings dosyası
 Bu kodu kopyalayın ve kendi gereksinimlerinize göre düzenleyin. Bu varsayılan .runsettings dosyasıdır.

 (. Runsettings dosyasının diğer kullanımları için bkz [.. runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).)

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See https://msdn.microsoft.com/library/2k3te2cs.aspx.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!—Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.Runtime\.CompilerServices.CompilerGeneratedAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>

```

## <a name="see-also"></a>Ayrıca Bkz.
 Kodun [ne kadar kodun test edildiğini öğrenmek için kod kapsamını kullanma](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) [kodunuzu test](../test/unit-test-your-code.md) etme
