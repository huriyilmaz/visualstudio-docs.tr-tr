---
title: Kod Kapsamı Çözümlemeyi Özelleştirme
ms.date: 08/21/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ce63e6ff368b090f096642c7f664c1adf45a0857
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880318"
---
# <a name="customize-code-coverage-analysis"></a>Kod kapsamı analizini özelleştirme

Varsayılan olarak, kod kapsamı birim testleri sırasında yüklenen tüm çözüm derlemelerini analiz eder. Çoğu zaman iyi çalıştığından, bu varsayılan davranışı kullanmanızı öneririz. Daha fazla bilgi için [bkz.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

Test kodunu kod kapsamı sonuçlarından dışlamak ve yalnızca <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> uygulama kodunu eklemek için, özniteliği test sınıfınıza ekleyin.

Çözümünüzün bir parçası olmayan derlemeleri eklemek için, bu derlemeler için *.pdb* dosyalarını edinin ve derleme *.dll* dosyalarıyla aynı klasöre kopyalayın.

## <a name="run-settings-file"></a>Ayarlar dosyalarını çalıştır

[Çalıştırma ayarları dosyası,](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) birim test araçları tarafından kullanılan yapılandırma dosyasıdır. Gelişmiş kod kapsamı ayarları bir *.runsettings* dosyasında belirtilir.

Kod kapsamını özelleştirmek için aşağıdaki adımları izleyin:

1. Çözümünüze bir çalışma ayarları dosyası ekleyin. **Çözüm Gezgini'nde,** çözümünüzün kısayol menüsünde**Yeni Öğe** **Ekle'yi** > seçin ve **XML Dosyası'nı**seçin. *Dosyayı CodeCoverage.runsettings*gibi bir adla kaydedin.

2. Bu makalenin sonundaki örnek dosyadaki içeriği ekleyin ve ardından izleyen bölümlerde açıklandığı şekilde gereksinimlerinize göre özelleştirin.

::: moniker range="vs-2017"

3. Çalışma ayarları dosyasını seçmek **için, Test** menüsünde **Test Ayarlarını** > **Seçin Test Ayarları Dosyasını**seçin. Komut satırından testleri çalıştırmak için bir çalışma ayarları dosyası belirtmek için [bkz.](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#command-line)

::: moniker-end

::: moniker range=">=vs-2019"

3. Çalışma ayarları dosyasını seçmek **için, Test** menüsünde **Ayarlar Dosyasını Seç'i**seçin. Komut satırından testleri çalıştırmak için bir çalışma ayarları dosyası belirtmek için [bkz.](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#command-line)

::: moniker-end

   **Kod Kapsamını Çözümle'yi**seçtiğinizde, yapılandırma bilgileri çalıştırma ayarları dosyasından okunur.

   > [!TIP]
   > Testleri çalıştırdığınızda veya kodunuzu güncellediğinizde önceki kod kapsamı sonuçları ve kod boyama otomatik olarak gizlenir.

::: moniker range="vs-2017"

Özel ayarları kapatıp açmak için **Test** > **Ayarları** menüsündeki dosyayı seçin veya seçin.

![Visual Studio 2017'de özel ayarlar dosyası ile test ayarları menüsü](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Özel ayarları kapatıp açmak için **Test** menüsündeki dosyayı seçin veya seçin.

::: moniker-end

## <a name="symbol-search-paths"></a>Sembol arama yolları

Kod kapsamı derlemeler için sembol dosyaları *(.pdb* dosyaları) gerektirir. Çözümünüz tarafından oluşturulan derlemeler için, sembol dosyaları genellikle ikili dosyaların yanında bulunur ve kod kapsamı otomatik olarak çalışır. Bazı durumlarda, kod kapsamı çözümlemesi nizde başvurulan derlemeleri eklemek isteyebilirsiniz. Bu gibi durumlarda, *.pdb* dosyaları ikilidosyalara bitişik olmayabilir, ancak *.runsettings* dosyasında simge arama yolunu belirtebilirsiniz.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> Sembol çözünürlüğü, özellikle birçok derlemeiçeren uzak bir dosya konumu kullanırken zaman alabilir. Bu nedenle, *.pdb* dosyalarını ikili *(.dll* ve *.exe*) dosyalarıyla aynı yerel konuma kopyalamayı düşünün.

## <a name="include-or-exclude-assemblies-and-members"></a>Derlemeleri ve üyeleri dahil et veya hariç tut

Derlemeleri veya belirli türleri ve üyeleri kod kapsamı çözümlemesi dahil edebilir veya hariç tutabilirsiniz. **Ekle** bölümü boşsa veya atlanırsa, yüklenen ve ilişkili PDB dosyaları olan tüm derlemeler dahil edilir. Bir derleme veya üye **Dışla** bölümündeki bir yan tümceyle eşleşirse, kod kapsamı nın dışında tutulur. **Dışla** bölümü **Ekle** bölümünden öncegelir: bir derleme hem **Ekle** hem de **Dışla'** da listelenirse, kod kapsamına dahil edilmez.

Örneğin, aşağıdaki XML adını belirterek tek bir derlemeyi dışlar:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>.*Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

Aşağıdaki örnekte, kod kapsamına yalnızca tek bir derlemenin eklenmesi gerektiği belirtilmiştir:

```xml
<ModulePaths>
  <Include>
   <ModulePath>.*Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

Aşağıdaki tablo, derlemelerin ve üyelerin kod kapsamına eklenmesi veya dışlanması için eşleştirilebilen çeşitli yolları gösterir.

| XML elemanı | Ne eşleşir |
| - | - |
| Modül Yolu | Derleme adı veya dosya yolu tarafından belirtilen derlemeleri eşleşir. |
| CompanyName | **Şirket** özniteliğine göre derlemelerle eşleşir. |
| Publickeytoken | Ortak anahtar belirteci tarafından imzalanmış maçlar. |
| Kaynak | Öğeleri, tanımlandıkları kaynak dosyanın yol adına göre eşleşir. |
| Öznitelik | Belirtilen özniteliğe sahip öğelerle eşleşir. Özniteliğin tam adını belirtin, `<Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>`örneğin.<br/><br/><xref:System.Runtime.CompilerServices.CompilerGeneratedAttribute> Özniteliği dışlarsanız, , , , `await` `yield return` `async`, ve otomatik olarak uygulanan özellikler gibi dil özelliklerini kullanan kod kod kapsamı çözümlemesi dışında tutulur. Gerçekten oluşturulan kodu hariç tutmak <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> için yalnızca özniteliği hariç tasla. |
| İşlev | Parametre listesi de dahil olmak üzere tam nitelikli ada göre yordamları, işlevleri veya yöntemleri eşleşir. Ayrıca normal bir [ifade](#regular-expressions)kullanarak adın bir kısmını eşleyebilirsiniz.<br/><br/>Örnekler:<br/><br/>`Fabrikam.Math.LocalMath.SquareRoot(double);`(C#)<br/><br/>`Fabrikam::Math::LocalMath::SquareRoot(double)`(C++) |

### <a name="regular-expressions"></a>Normal ifadeler

Jokerlerle aynı olmayan normal ifadeler kullanarak düğümleri ekleyin ve hariç tutar. Tüm eşlemeler büyük/küçük harf duyarsızdır. Bazı örnekler şunlardır:

- **. \* ** herhangi bir karakter dizeeş

- **\\.** bir nokta "" eşleşir.

- ( ) parantezeş "( )" ** \\ \\**

- **\\\\**bir dosya yolu delimiter " "\\eşleşir

- **^** dize başlangıcıyla eşleşir

- **$** dize sonu eşleşir

Aşağıdaki XML, normal ifadeler kullanarak belirli derlemeleri nasıl ekleyip dışlayanınacağıgöster:

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

Aşağıdaki XML, normal ifadeler kullanarak belirli işlevlerinasıl ekleyip dışlayanınacağıgöster:

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
> Düzenli bir ifadede, kaçılmamış veya eşleşmeyen bir parantez gibi bir hata varsa, kod kapsamı çözümlemesi çalışmaz.

Normal ifadeler hakkında daha fazla bilgi için [bkz.](../ide/using-regular-expressions-in-visual-studio.md)

## <a name="sample-runsettings-file"></a>Örnek .runsettings dosyası

Bu kodu kopyalayın ve ihtiyaçlarınıza göre edin.

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
Each element in the list is a regular expression (ECMAScript syntax). See /visualstudio/ide/using-regular-expressions-in-visual-studio.
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

- [Çalışma ayarları dosyalarını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Ne kadar kodun sınandığını belirlemek için kod kapsamını kullanma](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Birim kodunuzu test edin](../test/unit-test-your-code.md)
