---
title: Kod Kapsamı Çözümlemeyi Özelleştirme
ms.date: 08/21/2019
ms.topic: conceptual
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 7392397748d26224a0fba0d5510fccb6655d7642
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665070"
---
# <a name="customize-code-coverage-analysis"></a>Kod kapsamı analizini özelleştirme

Varsayılan olarak, kod kapsamı birim testleri sırasında yüklenen tüm çözüm derlemelerini analiz eder. Çoğu zaman en iyi şekilde çalıştığından, bu varsayılan davranışı kullanmanızı öneririz. Daha fazla bilgi için bkz. kod [kapsamını kullanarak ne kadar kodun test edildiğini belirleme](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Kod kapsamı sonuçlarından test kodunu dışlamak ve yalnızca uygulama kodunu dahil etmek için, <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> özniteliğini test sınıfınıza ekleyin.

Çözümünüzün bir parçası olmayan derlemeleri dahil etmek için, bu derlemeler için *. pdb* dosyalarını edinin ve bunları Assembly *. dll* dosyaları ile aynı klasöre kopyalayın.

## <a name="run-settings-file"></a>Çalışma ayarları dosyası

[Çalışma ayarları dosyası](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) birim testi araçları tarafından kullanılan yapılandırma dosyasıdır. Gelişmiş kod kapsamı ayarları bir *. runsettings* dosyasında belirtilir.

Kod kapsamını özelleştirmek için şu adımları izleyin:

1. Çözümünüze bir çalışma ayarları dosyası ekleyin. **Çözüm Gezgini**, çözümünüzün kısayol menüsünde,  > **Yeni öğe** **Ekle** ' yi seçin ve **XML dosyası**' nı seçin. Dosyayı *CodeCoverage. runsettings*gibi bir adla kaydedin.

2. Bu makalenin sonundaki örnek dosyadan içerik ekleyin ve ardından aşağıdaki bölümlerde açıklandığı gibi gereksinimlerinize göre özelleştirin.

::: moniker range="vs-2017"

3. Çalışma ayarları dosyasını seçmek için, **Test** menüsünde test **ayarları** ' nı seçin  > **Test ayarları dosyası**' nı seçin. Komut satırından testleri çalıştırmak için bir çalıştırma ayarları dosyası belirtmek için bkz. [birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#command-line).

::: moniker-end

::: moniker range=">=vs-2019"

3. Çalışma ayarları dosyasını seçmek için, **Test** menüsünde, **ayarlar dosyası seç**' i seçin. Komut satırından testleri çalıştırmak için bir çalıştırma ayarları dosyası belirtmek için bkz. [birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#command-line).

::: moniker-end

   **Kod kapsamını çözümle**' yi seçtiğinizde, yapılandırma bilgileri çalışma ayarları dosyasından okunmalıdır.

   > [!TIP]
   > Testleri çalıştırdığınızda veya kodunuzu güncelleştirdiğinizde önceki kod kapsamı sonuçları ve kod renklendirme otomatik olarak gizlenmez.

::: moniker range="vs-2017"

Özel ayarları kapatmak ve açmak için **test** > **Test ayarları** menüsünde dosyayı seçimden kaldırın veya seçin.

![Visual Studio 2017 'de özel ayarlar dosyası ile test ayarları menüsü](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Özel ayarları kapatmak ve açmak için, **Test** menüsündeki dosyanın seçimini kaldırın veya seçin.

::: moniker-end

## <a name="symbol-search-paths"></a>Sembol arama yolları

Kod kapsamı derlemeler için sembol dosyaları ( *. pdb* dosyaları) gerektirir. Çözümünüz tarafından oluşturulan derlemeler için, sembol dosyaları genellikle ikili dosyalarla birlikte bulunur ve kod kapsamı otomatik olarak işe yarar. Bazı durumlarda, kod kapsamı analizinizdeki başvurulan derlemeleri dahil etmek isteyebilirsiniz. Bu gibi durumlarda, *. pdb* dosyaları ikililerin bitişik olmayabilir, ancak *. runsettings* dosyasında sembol arama yolunu belirtebilirsiniz.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> Özellikle çok sayıda derlemeye sahip bir uzak dosya konumu kullanılırken, sembol çözünürlüğü zaman alabilir. Bu nedenle, *. pdb* dosyalarını ikili ( *. dll* ve *. exe*) dosyalarıyla aynı yerel konuma kopyalamayı göz önünde bulundurun.

## <a name="include-or-exclude-assemblies-and-members"></a>Derlemeleri ve üyeleri dahil etme veya dışlama

Kod kapsamı analizinden derlemeleri veya belirli türleri ve üyeleri dahil edebilir veya dışlayabilirsiniz. **Dahil etme** bölümü boşsa veya atlanırsa, yüklenen ve ilişkili pdb dosyalarına sahip olan tüm derlemeler dahil edilir. Bir derleme veya üye **dışlama** bölümündeki bir yan tümcesiyle eşleşiyorsa, kod kapsamından çıkarılır. **Dışlama** bölümü **dahil etme** bölümüne göre önceliklidir: bir derleme hem **dahil** hem de **hariç**olarak listeleniyorsa, kod kapsamına dahil edilmez.

Örneğin, aşağıdaki XML, adını belirterek tek bir derlemeyi dışlar:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

Aşağıdaki örnek, kod kapsamına yalnızca tek bir derlemenin dahil edileceğini belirtir:

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

Aşağıdaki tabloda, derlemelerin ve üyelerin kod kapsamından içerme veya dışlama için eşleştiribileceği çeşitli yollar gösterilmektedir.

| XML öğesi | Eşleşme |
| - | - |
| ModulePath | Bütünleştirilmiş kod adı veya dosya yolu tarafından belirtilen derlemeleri eşleştirir. |
| CompanyName | Derlemeleri **Şirket** özniteliğiyle eşleştirir. |
| PublicKeyToken | İmzalı derlemeleri ortak anahtar belirteci ile eşleştirir. |
| Kaynak | Öğelerin tanımlandıkları kaynak dosyanın yol adına göre eşleşir. |
| Öznitelik | Belirtilen özniteliğine sahip öğeleri eşleştirir. Özniteliğin tam adını belirtin, örneğin `<Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>`.<br/><br/>@No__t_0 özniteliğini hariç tutdıysanız, `async`, `await`, `yield return` ve otomatik uygulanan özellikler gibi dil özelliklerini kullanan kod, kod kapsamı analizinden çıkarılır. Gerçekten üretilen kodu hariç tutmak için yalnızca <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> özniteliğini hariç tutun. |
| İşlev | Parametre listesi de dahil olmak üzere tam olarak nitelenmiş ad ile yordamları, işlevleri veya yöntemleri eşleştirir. Ayrıca, bir [normal ifade](#regular-expressions)kullanarak adın bir bölümünü de eşleştirebilirsiniz.<br/><br/>Örnekler:<br/><br/>`Fabrikam.Math.LocalMath.SquareRoot(double);` (C#)<br/><br/>`Fabrikam::Math::LocalMath::SquareRoot(double)` (C++) |

### <a name="regular-expressions"></a>Normal ifadeler

Dahil etme ve hariç tutma düğümleri, joker karakterlerle aynı olmayan normal ifadeler kullanır. Tüm eşlemeler büyük/küçük harf duyarsızdır. Bazı örnekler şunlardır:

- **. \*** herhangi bir karakter dizesiyle eşleşir

- **\\.** bir noktayla eşleşir "."

- **\\ (\\)** parantezlerle eşleşir "()"

- **\\ \\** , "\\" dosya yolu sınırlayıcısıyla eşleşiyor

- **^** dizenin başlangıcını eşleştirir

- **$** dizenin sonuyla eşleşiyor

Aşağıdaki XML, belirli derlemelerin normal ifadeler kullanılarak nasıl ekleneceğini ve dışlanacağını göstermektedir:

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

Aşağıdaki XML, belirli işlevlerin normal ifadeler kullanılarak nasıl ekleneceğini ve dışlanacağını göstermektedir:

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

> [!WARNING]
> Kaçışsız veya eşleşmeyen parantez gibi normal ifadede bir hata varsa, kod kapsamı Analizi çalışmaz.

Normal ifadeler hakkında daha fazla bilgi için bkz. [Visual Studio 'da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="sample-runsettings-file"></a>Örnek .runsettings dosyası

Bu kodu kopyalayın ve gereksinimlerinize uyacak şekilde düzenleyin.

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
Each element in the list is a regular expression (ECMAScript syntax). See https://docs.microsoft.com/visualstudio/ide/using-regular-expressions-in-visual-studio.
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
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler\.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis\.ExcludeFromCodeCoverageAttribute$</Attribute>
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

            <!-- Set this to True to collect coverage information for functions marked with the "SecuritySafeCritical" attribute. Instead of writing directly into a memory location from such functions, code coverage inserts a probe that redirects to another function, which in turns writes into memory. -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <!-- When set to True, collects coverage information from child processes that are launched with low-level ACLs, for example, UWP apps. -->
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <!-- When set to True, collects coverage information from child processes that are launched by test or production code. -->
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <!-- When set to True, restarts the IIS process and collects coverage information from it. -->
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma ayarları dosyası kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Ne kadar kodun test edildiğini öğrenmek için kod kapsamını kullanın](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Kodunuzun birim testi](../test/unit-test-your-code.md)
