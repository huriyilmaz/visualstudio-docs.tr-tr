---
title: Live Unit Testing SSS
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: gewarren
ms.author: gewarren
ms.workload:
- dotnet
ms.openlocfilehash: 545c8974e3d0dea196a6168db03586a37d15ed72
ms.sourcegitcommit: 1a3c2ca995fd44fc72741b3a100c6e57f4f8702c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72262297"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing sık sorulan sorular

## <a name="supported-frameworks"></a>Desteklenen çerçeveler

**Hangi test çerçeveleri Live Unit Testing destekler ve desteklenen en düşük sürüm nedir?**

Live Unit Testing, aşağıdaki tabloda listelenen üç popüler birim testi çerçevesi ile birlikte kullanılabilir. Desteklenen en düşük sürüm bağdaştırıcılarının ve çerçeveleri de tabloda listelenir. Birim testi çerçevelerini NuGet.org adresinden tüm kullanılabilir.

|Test çerçevesi  |Visual Studio bağdaştırıcısı en düşük sürüm  |Framework en düşük sürüm  |
|---------|---------|---------|
|xUnit.net |xunit.Runner.VisualStudio sürüm 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter sürümü 3.7.0 |NUnit 3.5.0 sürümü |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

@No__t-0 ' a başvuruda bulunan daha önceden MSTest tabanlı test projelerine sahipseniz ve daha yeni MSTest NuGet paketlerine geçmek istemiyorsanız, Visual Studio 2019 veya Visual Studio 2017 sürümüne yükseltin.

Bazı durumlarda, açıkça için Live Unit Testing çalışmaya sırayla çözümde proje tarafından başvurulan NuGet paketlerini geri yüklemek gerekebilir. Çözümün açık bir derlemesini gerçekleştirerek veya çözüm üzerinde sağ tıklayıp **NuGet paketlerini geri yükle** ' yi seçerek paketleri geri yükleyebilirsiniz. (bkz.  > **çözümü** **Derle** , oturma birimi testini etkinleştirmeden önce.

## <a name="net-core-support"></a>.NET Core desteği

**Live Unit Testing .NET Core ile çalışıyor mu?**

Evet. Live Unit Testing .NET Core ve .NET Framework ile birlikte kullanılabilir.

## <a name="configuration"></a>Yapılandırma

**Bu öğeyi kapatdığımda neden Live Unit Testing çalışmıyor?**

Çıkış penceresi (Live Unit Testing açılan pencere seçildiğinde) Live Unit Testing neden çalışmadığını anlamalıdır. Aşağıdaki nedenlerden biri için Live Unit Testing çalışmayabilir:

- Çözümdeki projeler tarafından başvurulan NuGet paketleri geri yüklenemediğinde Live Unit Testing çalışmaz. Çözümün açık bir derlemesini yapmak veya Live Unit Testing açılmadan önce çözümde NuGet paketlerini geri yüklemek, bu sorunu çözmelidir.

- Projelerinizde MSTest tabanlı testler kullanıyorsanız, `Microsoft.VisualStudio.QualityTools.UnitTestFramework` ' a yönelik başvuruyu kaldırdığınızdan ve en son MSTest NuGet paketlerine başvurular eklediğinizden emin olun, `MSTest.TestAdapter` (minimum 1.1.11 sürümü gereklidir) ve `MSTest.TestFramework` (en düşük sürümü 1.1.11 gereklidir) . Daha fazla bilgi için, [Visual Studio 'da Live Unit Testing kullanma](live-unit-testing.md#supported-test-frameworks) makalesindeki "desteklenen test çerçeveleri" bölümüne bakın.

- Çözümünüzde en az bir projede bir NuGet başvurusu veya xUnit, NUnit veya MSTest test çerçevesine doğrudan başvuru olmalıdır. Bu proje Ayrıca karşılık gelen bir Visual Studio test bağdaştırıcıları NuGet paketine başvurmalıdır. Visual Studio test bağdaştırıcısına bir *. runsettings* dosyası aracılığıyla da başvurulabilir. *. Runsettings* dosyası aşağıdaki örnekteki gibi bir girdiye sahip olmalıdır:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Yükseltmeden sonra yanlış kapsam

**Visual Studio projelerinizde başvurulan test bağdaştırıcısını desteklenen sürüme yükselttikten sonra neden Live Unit Testing yanlış kapsamı gösteriyor?**

- Çözümdeki birden çok proje NuGet test bağdaştırıcısı paketine başvuruda bulunursa, her birinin desteklenen sürüme yükseltilmesi gerekir.

- Test bağdaştırıcısı paketinden içeri aktarılan MSBuild *. props* dosyasının da doğru şekilde güncelleştirildiğinden emin olun. Genellikle proje dosyasının en üstünde bulunan, aşağıdaki gibi, bir içeri aktarmanın NuGet paketi sürümünü/yolunu denetleyin:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Derlemeleri Özelleştir

**Live Unit Testing Derlemelerimi özelleştirebilir miyim?**

Çözümünüz, "normal" işaretlenmiş olmayan derleme için gerekli olmayan izleme (Live Unit Testing) için derleme için özel adımlar gerektiriyorsa, projenize veya *. targets* dosyalarına `BuildingForLiveUnitTesting` özelliğini denetleyen bir kod ekleyebilirsiniz ve özel ön/sonrası oluşturma adımları gerçekleştirir. Ayrıca, belirli derleme adımlarını (paket yayımlama veya oluşturma gibi) ya da bu proje özelliğine dayalı Live Unit Testing bir yapıya derleme adımları (örneğin, önkoşulları kopyalama) eklemeyi seçebilirsiniz. Bu özelliğe göre yapınızı özelleştirmek, normal derlemenizi herhangi bir şekilde değiştirmez ve yalnızca Live Unit Testing yapıları etkiler.

Örneğin, normal bir derleme sırasında NuGet paketleri üreten bir hedef olabilir. Yaptığınız her Düzenlemeden sonra NuGet paketlerinin oluşturulmasını istemezsiniz. Bu nedenle, aşağıdaki gibi bir şey yaparak Live Unit Testing derlemesinde bu hedefi devre dışı bırakabilirsiniz:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-or-outdir"></a>@No__t-0OutputPath > veya \<OutDir > ile hata iletileri

@no__t-Live Unit Testing çözümümüzü derlemeyi denediğinde şu hatayı alıyorum: "... `<OutputPath>` veya `<OutDir>` koşullu olarak ayarlanamaz. Live Unit Testing, çıkış derlemesinden testleri yürütmez "? **

Çözümünüz için derleme işlemi `<OutputPath>` veya `<OutDir>` ' i `<BaseOutputPath>` ' nin alt dizini olmaması adına koşulsuz olarak geçersiz kılıyorsa bu hatayı alabilirsiniz. Bu gibi durumlarda Live Unit Testing, derleme yapıtlarının `<BaseOutputPath>` altındaki bir klasöre bırakıldığından emin olmak için de bu değerleri geçersiz kıldığından çalışmayacaktır. Yapı yapıtlarınızın düzenli bir yapıda kesilmesini istediğiniz konumu geçersiz kılmanız gerekirse, `<BaseOutputPath>` ' e göre koşullu @no__t geçersiz kılın.

Örneğin, derlemeniz aşağıda gösterildiği gibi `<OutputPath>` ' yı geçersiz kılıyorsa:

```xml 
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

ardından, aşağıdaki XML ile değiştirebilirsiniz:

```xml 
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Bu, `<OutputPath>` ' ın `<BaseOutputPath>` klasörü içinde olmasını sağlar.

Doğrudan derleme sürecinizdeki `<OutDir>` ' i geçersiz kılmayın; derleme yapıtlarını belirli bir konuma bırakmak yerine, `<OutputPath>` ' i geçersiz kılın.

## <a name="build-artifact-location"></a>Yapı yapıt konumu

**I Live Unit Testing derleme yapıtlarının *. vs* klasörü altındaki varsayılan konum yerine belirli bir konuma gitmesini istiyor. Bunu nasıl değiştirebilirim?**

@No__t-0 Kullanıcı düzeyi ortam değişkenini Live Unit Testing derleme yapıtlarının kesilmesini istediğiniz yola ayarlayın. 

## <a name="test-explorer-versus-live-unit-testing"></a>Test Gezgini Live Unit Testing karşı

**Test Gezgini penceresinden testlerin Live Unit Testing testlerin çalıştırılmasının farkı nasıl çalışır?**

Çeşitli farklılıklar vardır:

- **Test Gezgini** penceresinde testleri çalıştırmak veya hata ayıklamak, düzenli ikili dosyalar çalıştırlarken Live Unit Testing, işaretlenmiş ikililer çalıştırır. Bir [hata ayıklayıcı](xref:System.Diagnostics.Debugger.Launch)ekleyerek, işaretlenmiş ikililer için hata ayıklama yapmak istiyorsanız. test yönteinizde  yöntem çağrısı, bu yöntem her yürütüldüğünde hata ayıklayıcının başlatılmasına neden olur (Live Unit Testing tarafından yürütüldüğü zaman dahil) ve sonra ekleyebilir ve işaretlenmiş ikilide hata ayıklayın. Bununla birlikte, umuyoruz çoğu kullanıcı senaryosunda sizin için şeffaf ve işaretlenmiş ikililerin hata ayıklamanıza gerek kalmaz.

- Live Unit Testing testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, ancak **Test Gezgini** penceresinden çalıştırılan testler yeni bir uygulama etki alanı oluşturur.

- Live Unit Testing testler sırayla her bir test derlemesindeki çalıştırır. **Test Gezgini**'nde, paralel olarak birden çok test çalıştırmayı seçebilirsiniz.

- Live Unit Testing testlerin bulunması ve yürütülmesi, `TestPlatform` ' ın 2. sürümünü kullanır, ancak **Test Gezgini** penceresi sürüm 1 ' i kullanır. Ancak çoğu durumda fark vermezsiniz.

- **Test Gezgini** , testleri tek iş parçacıklı bir grupta (STA) çalıştırır. Live Unit Testing, testleri çok iş parçacıklı bir grupta (MTA) çalıştırır. Live Unit Testing 'de STA 'da MSTest testlerini çalıştırmak için, test yöntemini veya içeren sınıfı, `MSTest.STAExtensions 1.0.3-beta` NuGet paketinde bulunan `<STATestMethod>` veya `<STATestClass>` özniteliğiyle süsledir. NUnit için, `<RequiresThread(ApartmentState.STA)>` özniteliğiyle ve xUnit için, `<STAFact>` özniteliğiyle test yöntemini süsle.

## <a name="exclude-tests"></a>Testleri hariç tut

**Nasıl yaparım? testlerin Live Unit Testing katılmasını hariç tutsın mı?**

Kullanıcıya özgü ayar için, [Visual Studio 'da Live Unit Testing kullanma](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) makalesindeki "test projelerini ve test yöntemlerini ekleme ve dışlama" bölümüne bakın. Belirli bir düzenleme oturumu için belirli bir test kümesini çalıştırmak veya kendi kişisel tercihlerinizi sürdürmek istediğinizde, testlerin dahil edilmesi veya dışlanması yararlı olur.

Çözüme özgü ayarlar için, <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> özniteliğini programlı bir şekilde, yöntemleri, özellikleri, sınıfları veya yapıları Live Unit Testing tarafından işaretlenmiş olarak hariç tutabilir. Ayrıca, projenin tamamını işaretlenmiş olarak hariç tutmak için `<ExcludeFromCodeCoverage>` özelliğini proje dosyanızda `true` olarak ayarlayabilirsiniz. Live Unit Testing, henüz eklenmemiş testleri çalıştırmaya devam eder, ancak kapsamı görselleştirilecektir.

Ayrıca, geçerli uygulama etki alanında `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` ' ın yüklenip yüklenmediğini denetleyebilir ve Testleri neden temel alarak devre dışı bırakabilirsiniz. Örneğin, xUnit ile aşağıdakine benzer bir şey yapabilirsiniz:

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

::: moniker range="vs-2017"

## <a name="win32-pe-headers"></a>Win32 PE üstbilgileri

**Canlı birim testi tarafından oluşturulan işaretlenmiş derlemelerde Win32 PE üstbilgileri neden farklıdır?**

Bu sorun düzeltildi ve Visual Studio 2017 sürüm 15,3 ve sonraki sürümlerde yok.

Visual Studio 2017 ' nin eski sürümleri için, Live Unit Testing derlemelerin aşağıdaki Win32 PE başlık verilerini ekleyememesi ile sonuçlanabileceğini belirten bilinen bir hata vardır:

- Dosya sürümü (kodda @System.Reflection.AssemblyFileVersionAttribute ile belirtilir).

- Win32 simgesi (komut satırında `/win32icon:` ile belirtilir).

- Win32 bildirimi (komut satırında `/win32manifest:` ile belirtilir).

Bu değerleri kullanan testler, canlı birim testi tarafından yürütüldüğünde başarısız olabilir.

::: moniker-end

## <a name="continuous-builds"></a>Sürekli derlemeler

**Canlı birim testi neden, hiç bir düzenleme yapmadığım halde çözümümüzü her zaman oluşturmaya devam ediyor?**

Yapı işlemi çözümün kendisinin parçası olan kaynak kodu oluşturursa ve yapı hedef dosyalarınızda uygun girişler ve çıktılar belirtilmemişse, çözümünüz, düzenleme yapmasanız bile oluşturabilir. MSBuild 'in uygun güncel denetimleri gerçekleştirebilmesi ve yeni bir derleme gerekip gerekmediğini belirleyebilmesi için, hedeflerin bir giriş ve çıkış listesi verilmelidir.

Live Unit Testing, kaynak dosyaların değiştiğini algıladığında bir derlemeyi başlatır. Çözümünüzün derlemesi kaynak dosyalar oluşturduğundan Live Unit Testing sonsuz bir derleme döngüsüne alınır. Ancak, Live Unit Testing ikinci derlemeyi başlattığında hedefin giriş ve çıkışları işaretlenirse (önceki derlemeden yeni oluşturulan kaynak dosyalarını algıladıktan sonra), girişler ve çıkışlar kontrol ettiğinden, derleme döngüsünün dışına çıkar. Her şey güncel.

## <a name="editor-icons"></a>Düzenleyici simgeleri

**Neden, çıkış penceresindeki iletilere göre testlerin çalıştırılmasına rağmen Live Unit Testing düzenleyicide hiç simge görmüyorum?**

Live Unit Testing üzerinde çalışan derlemeler herhangi bir nedenle işaretlenmemişse düzenleyicide simge göremeyebilirsiniz. Örneğin, Live Unit Testing `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>` olarak ayarlanmış projelerle uyumlu değildir. Bu durumda, derleme işleminizin bu ayarı kaldıracak şekilde güncelleştirilmesi veya Live Unit Testing çalışması için `true` olarak değiştirilmesi gerekir. 

## <a name="capture-logs"></a>Günlükleri yakala

**Hata raporlarına dosya eklemek için daha ayrıntılı Günlükler mi Nasıl yaparım??**

Daha ayrıntılı Günlükler toplamak için birkaç şey yapabilirsiniz:

- **Araçlar** > **seçeneklerine** > **Live Unit Testing** gidin ve günlük seçeneğini **verbose**olarak değiştirin. Ayrıntılı günlük kaydı, **Çıkış** penceresinde daha ayrıntılı günlüklerin gösterilmesine neden olur.

- @No__t-0 Kullanıcı ortam değişkenini, MSBuild günlüğünü yakalamak için kullanmak istediğiniz dosyanın adı olarak ayarlayın. Live Unit Testing derlemelerden ayrıntılı MSBuild günlük iletileri daha sonra bu dosyadan alınabilir.

- Test platformu günlüğünü yakalamak için `LiveUnitTesting_TestPlatformLog` Kullanıcı ortam değişkenini `1` olarak ayarlayın. Live Unit Testing çalıştırmalarının ayrıntılı test platformu günlük iletileri daha sonra `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` ' dan alınabilir.

- @No__t-0 adlı bir Kullanıcı düzeyi ortam değişkeni oluşturun ve bunu 1 (veya herhangi bir değere) olarak ayarlayın ve Visual Studio 'Yu yeniden başlatın. Artık Visual Studio 'daki **çıkış testleri** sekmesinde çok fazla günlük görmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Canlı Birim Testi](live-unit-testing.md)
