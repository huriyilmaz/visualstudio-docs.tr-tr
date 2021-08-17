---
title: Kod Kapsamı Çözümlemeyi Özelleştirme
description: Test kodunu kapsam sonuçlarından dışlamak için ExcludeFromCodeCoverageAttribute özniteliğini kullanmayı öğrenin. Derlemeleri çözümünüz dışında dahil edersiniz.
ms.custom: SEO-VS-2020
ms.date: 08/21/2019
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c380f65f9bde1e6980d6989aecaaa93d5e60a548d8805416532215a2bcf64034
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425028"
---
# <a name="customize-code-coverage-analysis"></a>Kod kapsamı analizini özelleştirme

Varsayılan olarak, kod kapsamı birim testleri sırasında yüklenen tüm çözüm derlemelerini analiz eder. Çoğu zaman iyi şekilde çalıştığını için bu varsayılan davranışı kullanmanız önerilir. Daha fazla bilgi için [bkz. Ne kadar kodun test olduğunu belirlemek için kod kapsamı kullanma.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

Test kodunu kod kapsamı sonuçlarından dışlamak ve yalnızca uygulama kodunu eklemek için <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> özniteliğini test sınıfınıza ekleyin.

Çözüme dahil olmayan derlemeleri dahil etmek için, bu derlemeler için *.pdb* dosyalarını alın ve bunları derleme dosyalarıyla aynı *klasöre.dll* kopyalayın.

## <a name="run-settings-file"></a>Ayarlar dosyasını çalıştırma

Çalıştırma [ayarları dosyası,](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) birim testi araçları tarafından kullanılan yapılandırma dosyasıdır. Gelişmiş kod kapsamı ayarları bir *.runsettings dosyasında* belirtilir.

Kod kapsamı özelleştirmek için şu adımları izleyin:

1. Çözümünüze bir çalıştırma ayarları dosyası ekleyin. Bu **Çözüm Gezgini,** çözüm çözümlü kısayol menüsünde Yeni Öğe  >  **Ekle'yi ve** **ARDıNDAN XML Dosyası'yı seçin.** Dosyayı *CodeCoverage.runsettings gibi bir adla kaydedin.*

2. Bu makalenin sonundaki örnek dosyadan içeriği ekleyin ve ardından aşağıdaki bölümlerde açıklandığı gibi ihtiyaçlarınıza göre özelleştirin.

::: moniker range="vs-2017"

3. Çalıştırma ayarları dosyasını seçmek için Test menüsünde Test ve **Test** Ayarlar  >  **Dosya'Ayarlar seçin.** Komut satırına test çalıştırmaya bir çalıştırma ayarları dosyası belirtmek için [bkz. Birim testlerini yapılandırma.](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file-from-the-command-line)

::: moniker-end

::: moniker range=">=vs-2019"

3. Çalıştırma ayarları dosyasını seçmek için Test **menüsünde** Dosya olarak Seç'Ayarlar **seçin.** Komut satırına test çalıştırmaya bir çalıştırma ayarları dosyası belirtmek için [bkz. Birim testlerini yapılandırma.](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file-from-the-command-line)

::: moniker-end

   Kod Kapsamı **Çözümle'yi** seçerek yapılandırma bilgileri çalıştırma ayarları dosyasından okunur.

   > [!TIP]
   > Testleri çalıştırarak veya kodunuzu güncelleştirerek önceki kod kapsamı sonuçları ve kod renklendirmeleri otomatik olarak gizlenir.

::: moniker range="vs-2017"

Özel ayarları kapatmak ve açmak için Test Testi Uygulama menüsünde **dosyanın** > **seçimini Ayarlar** seçin.

![Visual Studio 2017'de özel ayarlar dosyasıyla test ayarları menüsü](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Özel ayarları kapatmak ve açmak için Test menüsünde dosyanın seçimini kaldırın **veya** dosyayı seçin.

::: moniker-end

## <a name="symbol-search-paths"></a>Sembol arama yolları

Kod kapsamı, derlemeler için sembol dosyaları (*.pdb* dosyaları) gerektirir. Çözümünüz tarafından derlemeler için sembol dosyaları genellikle ikili dosyaların yanı sıra mevcuttur ve kod kapsamı otomatik olarak çalışır. Bazı durumlarda, kod kapsamı analizinize başvurulan derlemeleri dahil etmek istiyor olabilir. Böyle *durumlarda, .pdb* dosyaları ikili dosyalar ile bitişik değildir, ancak *.runsettings* dosyasında sembol arama yolunu belirtebilirsiniz.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> Sembol çözümlemesi, özellikle de çok sayıda derleme ile uzak dosya konumu kullanırken zaman alır. Bu nedenle, *.pdb dosyalarını* ikili (.dllve *.exe* ) *dosyalarıyla aynı yerel konuma* kopyalamayı göz önünde bulundurabilirsiniz.

## <a name="include-or-exclude-assemblies-and-members"></a>Derlemeleri ve üyeleri dahil etmek veya hariç tutmak

Derlemeleri veya belirli türleri ve üyeleri kod kapsamı analizine dahil veya hariç tutabilirsiniz. Dahil **Edin bölümü** boşsa veya atlanırsa, yüklenen ve ilişkili PDB dosyalarına sahip tüm derlemeler dahil edilir. Bir derleme veya üye Exclude bölümündeki  bir yan tümceyle eş olursa, kod kapsamından hariç tutulabilir. Dışla bölümü, Dahil Edilenler bölümünden **önceliklidir:** bir  derleme hem Dahil Edin hem de Dışla'da listelenmişse, kod kapsamına dahil olmaz. 

Örneğin, aşağıdaki XML, adını belirterek tek bir derlemeyi dışlar:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>.*Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

Aşağıdaki örnek, kod kapsamına yalnızca tek bir derlemenin dahil olması gerektiğini belirtir:

```xml
<ModulePaths>
  <Include>
   <ModulePath>.*Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

Aşağıdaki tabloda, derlemelerin ve üyelerin kod kapsamına dahil edilmesi veya kod kapsamından dışlanması için çeşitli yollar gösterir.

| XML öğesi | Neleri eşler? |
| - | - |
| ModulePath | Derleme adı veya dosya yolu tarafından belirtilen derlemeleri eşler. |
| CompanyName | Şirket özniteliğine göre **derlemeleri eşler.** |
| Publickeytoken | Ortak anahtar belirteci tarafından imzalanmış derlemeleri eşler. |
| Kaynak | Öğeleri tanımlandığı kaynak dosyanın yol adına göre eşler. |
| Öznitelik | Belirtilen özniteliğine sahip öğelerle eşler. Özniteliğin tam adını belirtin, örneğin `<Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>` .<br/><br/>özniteliğini dışlarsanız, , , ve otomatik uygulanan özellikler gibi dil özelliklerini kullanan <xref:System.Runtime.CompilerServices.CompilerGeneratedAttribute> `async` `await` `yield return` kod, kod kapsamı analizinin dışındadır. Gerçek anlamda oluşturulan kodu hariç tutmak için yalnızca özniteliğini hariç <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> tutabilirsiniz. |
| İşlev | Yordamları, işlevleri veya yöntemleri parametre listesi de dahil olmak üzere tam adla eşler. Normal bir ifade kullanarak adın bir bölümünü de [eşlersiniz.](#regular-expressions)<br/><br/>Örnekler:<br/><br/>`Fabrikam.Math.LocalMath.SquareRoot(double);` (C#)<br/><br/>`Fabrikam::Math::LocalMath::SquareRoot(double)` (C++) |

### <a name="regular-expressions"></a>Normal ifadeler

Dahil etme ve dışlama düğümleri, joker karakterlerle aynı olmayan normal ifadeleri kullanır. Tüm eşlemeler büyük/küçük harf duyarsızdır. Bazı örnekler şunlardır:

- **.\*** herhangi bir karakterden bir dizeyle eşler

- **\\.** bir nokta "." ile eşler.

- **\\ ( \\ )** parantezleri "( )" ile eşler

- **\\\\** bir dosya yolu sınırlayıcı " " ile \\ eşler

- **^** dizenin başlangıcıyla eşler

- **$** dizenin sonuyla eşler

Aşağıdaki XML, normal ifadeler kullanarak belirli derlemelerin nasıl dahil edilecek ve hariç tutulacaklarını gösterir:

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

Aşağıdaki XML, normal ifadeler kullanarak belirli işlevlerin nasıl dahil ve hariç tutulacaklarını gösterir:

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
> Normal ifadede bir hata varsa (örneğin, kaçışsız veya eşleşmeyen parantezler) kod kapsamı analizi çalışmaz.

Normal ifadeler hakkında daha fazla bilgi için [bkz. Normal ifadeleri Visual Studio.](../ide/using-regular-expressions-in-visual-studio.md)

## <a name="sample-runsettings-file"></a>Örnek .runsettings dosyası

Bu kodu kopyalayın ve ihtiyaçlarınıza uyacak şekilde düzenleyin.

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

- [Çalıştırma ayarları dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Ne kadar kodun test edildiklerini belirlemek için kod kapsamı kullanma](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Kodunuzu birim testi](../test/unit-test-your-code.md)
