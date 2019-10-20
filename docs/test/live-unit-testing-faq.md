---
title: Live Unit Testing SSS
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: jillre
ms.author: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8db8264268eb04edc3140d0e2a6ece5896692e38
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653046"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing sık sorulan sorular

## <a name="supported-frameworks"></a>Desteklenen çerçeveler

**Hangi test çerçeveleri Live Unit Testing destekler ve desteklenen en düşük sürüm nedir?**

Live Unit Testing, aşağıdaki tabloda listelenen üç popüler birim testi çerçevesi ile birlikte kullanılabilir. Bağdaştırıcıların ve çerçevelerinin desteklenen minimum sürümü tabloda de listelenmiştir. Birim test çerçevelerinin tümü NuGet.org adresinden kullanılabilir.

|Test çerçevesi  |Visual Studio bağdaştırıcısı en düşük sürüm  |Framework minimum sürümü  |
|---------|---------|---------|
|xUnit.net |xUnit. Runner. VisualStudio sürüm 2.2.0-Beta3-build1187 |xUnit 1.9.2 |
|NUnit |NUnit3TestAdapter sürümü 3.7.0 |NUnit sürümü 3.5.0 |
|MSTest |MSTest. TestAdapter 1.1.4-Önizleme |MSTest. TestFramework 1.0.5-Önizleme |

@No__t_0 başvuruda bulunan daha önce MSTest tabanlı test projelerine sahipseniz ve yeni MSTest NuGet paketlerine geçmek istemiyorsanız, Visual Studio 2019 veya Visual Studio 2017 sürümüne yükseltin.

Bazı durumlarda, Live Unit Testing çalışması için çözümdeki projeler tarafından başvurulan NuGet paketlerini açıkça geri yüklemeniz gerekebilir. Çözümün açık bir derlemesini gerçekleştirerek veya çözüm üzerinde sağ tıklayıp **NuGet paketlerini geri yükle** ' yi seçerek paketleri geri yükleyebilirsiniz. ( **derleme**  > **çözümü** seçin , oturma birimi testini etkinleştirmeden önce.

## <a name="net-core-support"></a>.NET Core desteği

**Live Unit Testing .NET Core ile çalışıyor mu?**

Evet. Live Unit Testing .NET Core ve .NET Framework ile birlikte kullanılabilir.

## <a name="configuration"></a>Yapılandırma

**Bu öğeyi kapatdığımda neden Live Unit Testing çalışmıyor?**

Çıkış penceresi (Live Unit Testing açılan pencere seçildiğinde) Live Unit Testing neden çalışmadığını anlamalıdır. Aşağıdaki nedenlerden biri için Live Unit Testing çalışmayabilir:

- Çözümdeki projeler tarafından başvurulan NuGet paketleri geri yüklenemediğinde Live Unit Testing çalışmaz. Çözümün açık bir derlemesini yapmak veya Live Unit Testing açılmadan önce çözümde NuGet paketlerini geri yüklemek, bu sorunu çözmelidir.

- Projelerinizde MSTest tabanlı testler kullanıyorsanız, `Microsoft.VisualStudio.QualityTools.UnitTestFramework` başvurusunu kaldırdığınızdan ve en son MSTest NuGet paketlerine başvuruları eklediğinizden emin olun, `MSTest.TestAdapter` (en düşük sürüm 1.1.11 gereklidir) ve `MSTest.TestFramework` (en düşük sürüm 1.1.11 gereklidir) . Daha fazla bilgi için, [Visual Studio 'da Live Unit Testing kullanma](live-unit-testing.md#supported-test-frameworks) makalesindeki "desteklenen test çerçeveleri" bölümüne bakın.

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

Çözümünüz, "normal" işaretlenmiş olmayan derleme için gerekli olmayan izleme (Live Unit Testing) için derleme için özel adımlar gerektiriyorsa, projenize veya *. targets* dosyalarınıza, `BuildingForLiveUnitTesting` özelliğini denetleyen bir kod ekleyebilirsiniz ve özel ön/sonrası oluşturma adımları gerçekleştirir. Ayrıca, belirli derleme adımlarını (paket yayımlama veya oluşturma gibi) ya da bu proje özelliğine dayalı Live Unit Testing bir yapıya derleme adımları (örneğin, önkoşulları kopyalama) eklemeyi seçebilirsiniz. Bu özelliğe göre yapınızı özelleştirmek, normal derlemenizi herhangi bir şekilde değiştirmez ve yalnızca Live Unit Testing yapıları etkiler.

Örneğin, normal bir derleme sırasında NuGet paketleri üreten bir hedef olabilir. Yaptığınız her Düzenlemeden sonra NuGet paketlerinin oluşturulmasını istemezsiniz. Bu nedenle, aşağıdaki gibi bir şey yaparak Live Unit Testing derlemesinde bu hedefi devre dışı bırakabilirsiniz:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-or-outdir"></a>@No__t_0OutputPath > veya \<OutDir olan hata iletileri >

**Live Unit Testing çözümümüzü derlemeyi denediğinde neden aşağıdaki hatayı alıyorum: "... koşulsuz olarak ayarlı `<OutputPath>` veya `<OutDir>` görünür. Live Unit Testing, çıkış derlemesinden testleri yürütmez "?**

Çözümünüze yönelik derleme işlemi `<OutputPath>` veya `<OutDir>` `<BaseOutputPath>` alt dizini olmaması adına koşulsuz olarak geçersiz kıldığında bu hatayı alabilirsiniz. Bu gibi durumlarda Live Unit Testing, derleme yapıtlarının `<BaseOutputPath>` altındaki bir klasöre bırakıldığından emin olmak için bu değerleri geçersiz kıldığından çalışmayacaktır. Yapı yapıtlarınızın düzenli bir yapıda kesilmesini istediğiniz konumu geçersiz kılmanız gerekiyorsa, `<BaseOutputPath>` göre koşullu `<OutputPath>` geçersiz kılın.

Örneğin, derlemeniz aşağıda gösterildiği gibi `<OutputPath>` geçersiz kılıyorsa:

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

Bu, `<OutputPath>` `<BaseOutputPath>` klasörünün içinde olmasını sağlar.

Yapı sürecinizdeki `<OutDir>` doğrudan geçersiz kılmayın; derleme yapıtlarını belirli bir konuma bırakmak yerine `<OutputPath>` geçersiz kılın.

## <a name="build-artifact-location"></a>Yapı yapıt konumu

**Live Unit Testing derleme yapıtlarının, *. vs* klasörü altındaki varsayılan konum yerine belirli bir konuma gitmesini istiyorum. Bunu nasıl değiştirebilirim?**

@No__t_0 Kullanıcı düzeyi ortam değişkenini Live Unit Testing derleme yapıtlarının kesilmesini istediğiniz yola ayarlayın. 

## <a name="test-explorer-versus-live-unit-testing"></a>Test Gezgini Live Unit Testing karşı

**Test Gezgini penceresinden testlerin Live Unit Testing testlerin çalıştırılmasının farkı nasıl çalışır?**

Çeşitli farklılıklar vardır:

- **Test Gezgini** penceresinde testleri çalıştırmak veya hata ayıklamak, düzenli ikili dosyalar çalıştırlarken Live Unit Testing, işaretlenmiş ikililer çalıştırır. Bir [hata ayıklayıcı](xref:System.Diagnostics.Debugger.Launch) ekleyerek, işaretlenmiş ikililer için hata ayıklama yapmak istiyorsanız. test yönteinizde başlatma  method çağrısı, yöntemin her yürütüldüğü zaman hata ayıklayıcının başlatılmasına neden olur (Live Unit Testing tarafından yürütüldüğü zaman dahil) ve daha sonra ekleyebilir ve işaretlenmiş ikilide hata ayıklayın. Bununla birlikte, umuyoruz çoğu kullanıcı senaryosunda sizin için şeffaf ve işaretlenmiş ikililerin hata ayıklamanıza gerek kalmaz.

- Live Unit Testing testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, ancak **Test Gezgini** penceresinden çalıştırılan testler yeni bir uygulama etki alanı oluşturur.

- Live Unit Testing her bir test derlemesindeki testleri sırayla çalıştırır. **Test Gezgini**'nde, paralel olarak birden çok test çalıştırmayı seçebilirsiniz.

- Live Unit Testing testlerin keşfi ve yürütülmesi `TestPlatform` sürüm 2 ' yi kullanır, ancak **Test Gezgini** penceresi sürüm 1 ' i kullanır. Ancak çoğu durumda fark vermezsiniz.

- **Test Gezgini** , testleri tek iş parçacıklı bir grupta (STA) çalıştırır. Live Unit Testing, testleri çok iş parçacıklı bir grupta (MTA) çalıştırır. Live Unit Testing içinde STA 'da MSTest testlerini çalıştırmak için, test yöntemini veya içeren sınıfı, `MSTest.STAExtensions 1.0.3-beta` NuGet paketinde bulunan `<STATestMethod>` veya `<STATestClass>` özniteliğiyle süsledir. NUnit için, `<RequiresThread(ApartmentState.STA)>` özniteliğiyle ve xUnit için `<STAFact>` özniteliğiyle test yöntemini süsle.

## <a name="exclude-tests"></a>Testleri hariç tut

**Nasıl yaparım? testlerin Live Unit Testing katılmasını hariç tutsın mı?**

Kullanıcıya özgü ayar için, [Visual Studio 'da Live Unit Testing kullanma](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) makalesindeki "test projelerini ve test yöntemlerini ekleme ve dışlama" bölümüne bakın. Belirli bir düzenleme oturumu için belirli bir test kümesini çalıştırmak veya kendi kişisel tercihlerinizi sürdürmek istediğinizde, testlerin dahil edilmesi veya dışlanması yararlı olur.

Çözüme özgü ayarlar için, Live Unit Testing tarafından işaretlenmiş yöntemlerin, özelliklerin, sınıfların veya yapıların hariç tutulması için <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> özniteliğini programlı bir şekilde uygulayabilirsiniz. Ayrıca, projenin tamamını işaretlenmiş olarak hariç tutmak için `<ExcludeFromCodeCoverage>` özelliğini proje dosyanızda `true` olarak ayarlayabilirsiniz. Live Unit Testing, henüz eklenmemiş testleri çalıştırmaya devam eder, ancak kapsamı görselleştirilecektir.

Ayrıca, `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` geçerli uygulama etki alanında yüklenip yüklenmediğini denetleyebilir ve Testleri neden temel alarak devre dışı bırakabilirsiniz. Örneğin, xUnit ile aşağıdakine benzer bir şey yapabilirsiniz:

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

- Dosya sürümü (kodda @System.Reflection.AssemblyFileVersionAttribute tarafından belirtilen).

- Win32 simgesi (komut satırında `/win32icon:` tarafından belirtilir).

- Win32 bildirimi (komut satırında `/win32manifest:` tarafından belirtilir).

Bu değerleri kullanan testler, canlı birim testi tarafından yürütüldüğünde başarısız olabilir.

::: moniker-end

## <a name="continuous-builds"></a>Sürekli derlemeler

**Canlı birim testi neden, hiç bir düzenleme yapmadığım halde çözümümüzü her zaman oluşturmaya devam ediyor?**

Yapı işlemi çözümün kendisinin parçası olan kaynak kodu oluşturursa ve yapı hedef dosyalarınızda uygun girişler ve çıktılar belirtilmemişse, çözümünüz, düzenleme yapmasanız bile oluşturabilir. MSBuild 'in uygun güncel denetimleri gerçekleştirebilmesi ve yeni bir derleme gerekip gerekmediğini belirleyebilmesi için, hedeflerin bir giriş ve çıkış listesi verilmelidir.

Live Unit Testing, kaynak dosyaların değiştiğini algıladığında bir derlemeyi başlatır. Çözümünüzün derlemesi kaynak dosyalar oluşturduğundan Live Unit Testing sonsuz bir derleme döngüsüne alınır. Ancak, Live Unit Testing ikinci derlemeyi başlattığında hedefin giriş ve çıkışları işaretlenirse (önceki derlemeden yeni oluşturulan kaynak dosyalarını algıladıktan sonra), girişler ve çıkışlar kontrol ettiğinden, derleme döngüsünün dışına çıkar. Her şey güncel.

## <a name="editor-icons"></a>Düzenleyici simgeleri

**Neden, çıkış penceresindeki iletilere göre testlerin çalıştırılmasına rağmen Live Unit Testing düzenleyicide hiç simge görmüyorum?**

Live Unit Testing üzerinde çalışan derlemeler herhangi bir nedenle işaretlenmemişse düzenleyicide simge göremeyebilirsiniz. Örneğin, Live Unit Testing `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>` ayarlanmış projelerle uyumlu değildir. Bu durumda, bu ayarı kaldırmak veya Live Unit Testing çalışması için `true` değiştirmek üzere derleme işleminizin güncelleştirilmesi gerekir. 

## <a name="capture-logs"></a>Günlükleri yakala

**Hata raporlarına dosya eklemek için daha ayrıntılı Günlükler mi Nasıl yaparım??**

Daha ayrıntılı Günlükler toplamak için birkaç şey yapabilirsiniz:

- **Araçlar**  > **Seçenekler**  > **Live Unit Testing** gidin ve günlük seçeneğini **verbose**olarak değiştirin. Ayrıntılı günlük kaydı, **Çıkış** penceresinde daha ayrıntılı günlüklerin gösterilmesine neden olur.

- @No__t_0 Kullanıcı ortam değişkenini, MSBuild günlüğünü yakalamak için kullanmak istediğiniz dosyanın adı olarak ayarlayın. Live Unit Testing derlemelerden ayrıntılı MSBuild günlük iletileri daha sonra bu dosyadan alınabilir.

- Test platformu günlüğünü yakalamak için `LiveUnitTesting_TestPlatformLog` Kullanıcı ortam değişkenini `1` olarak ayarlayın. Live Unit Testing çalıştırmalarının ayrıntılı test platformu günlük iletileri daha sonra `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` alabilir.

- @No__t_0 adlı bir Kullanıcı düzeyi ortam değişkeni oluşturun ve bunu 1 (veya herhangi bir değere) olarak ayarlayın ve Visual Studio 'Yu yeniden başlatın. Artık Visual Studio 'daki **çıkış testleri** sekmesinde çok fazla günlük görmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Canlı Birim Testi](live-unit-testing.md)
