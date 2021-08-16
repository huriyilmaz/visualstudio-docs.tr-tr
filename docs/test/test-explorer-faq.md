---
title: Test Gezgini Hakkında SSS
description: Test Gezgini ile ilgili sık sorulan Visual Studio sık karşılaşılan sorun giderme adımlarına bakın.
ms.custom: SEO-VS-2020
ms.date: 06/25/2020
ms.topic: conceptual
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 6e5cd80c4523d74b2cf26887362e9bbffaa82d0f5369aa0f4666b02edc894a05
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352466"
---
# <a name="visual-studio-test-explorer-faq"></a>Visual Studio Test Gezgini hakkında SSS

## <a name="dynamic-test-discovery"></a>Dinamik test bulma

**Test Gezgini dinamik olarak tanımlanan testlerimi keşfeder. (Örneğin teoriler, özel bağdaştırıcılar, özel nitelikler, #ifdefs vb.) Bu testleri nasıl bula bilmiyorum?**

::: moniker range=">=vs-2019"
Derleme tabanlı bulma çalıştırmak için projenizi derleme.
::: moniker-end
::: moniker range="vs-2017"
Projenizi derleme ve Araç Seçenekleri Testi'nde  derleme tabanlı bulmanın açık > **olduğundan emin** > **olun.**
::: moniker-end
[Gerçek zamanlı test bulma,](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) kaynak tabanlı test bulmadır. Çalışma zamanında tanımlandığı için teorileri, özel bağdaştırıcıları, özel özellikleri, deyimleri ve daha fazlasını kullanan `#ifdef` testleri keşfeder. Bu testlerin doğru şekilde bulun olması için bir derleme gereklidir. 2017 Visual Studio 15.6 ve sonraki sürümlerde derleme tabanlı bulma (geleneksel bulma) yalnızca derlemeler sonrasında çalışır. Bu ayar, gerçek zamanlı test bulmanın düzenleme sırasında mümkün olan en fazla sayıda test bulduğu anlamına gelir ve derleme tabanlı bulma, dinamik olarak tanımlanan testlerin derlemeden sonra görünmesini sağlar. Gerçek zamanlı test bulma, yanıt hızını artırmasına rağmen derlemeden sonra tam ve kesin sonuçlar elde etmek için size olanak sağlar.

## <a name="test-explorer--plus-symbol"></a>Test Gezgini '+' (artı) simgesi

**Test Gezgini'nin üst satırına görünen '+' (artı) simgesi ne anlama geliyor?**

'+' (artı) simgesi, derleme tabanlı bulma çalıştırıldıktan sonra daha fazla testin keşfedil olduğunu gösterir. Projeniz içinde dinamik olarak tanımlanmış testler algılanırsa bu simge görünür.

![Artı simgesi özet satırı](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>Derleme tabanlı bulma

**Derleme tabanlı bulma artık projem için çalışmıyor. Nasıl yaparım? açmak mı?**

Araçlar  Seçenekler > **Testi'ne** > **gidin** ve Derlemelerden sonra yerleşik derlemelerden testleri ek **olarak bulma kutusunu işaretleyin.**

![Derleme tabanlı seçenek](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Gerçek zamanlı test bulma

**Testler artık projemi derlemek zorunda kalmadan yazma sırasında Test Gezgini'nde görünür. Ne değişti?**

Bu özellik, gerçek [zamanlı test bulma olarak adlandırılan bir özelliktir.](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) Projenizi derlemenize gerek kalmadan testleri bulmak ve Test Gezgini'ni gerçek zamanlı olarak doldurmak için Roslyn çözümleyicisini kullanır. Teoriler veya özel nitelikler gibi dinamik olarak tanımlanmış testler için test bulma davranışı hakkında daha fazla bilgi için [bkz. Dinamik test bulma](#dynamic-test-discovery).

## <a name="real-time-test-discovery-compatibility"></a>Gerçek zamanlı test bulma uyumluluğu

**Gerçek Zamanlı Test Bulma hangi dilleri ve test çerçevelerini kullanabilir?**

[Roslyn derleyicisi](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) kullanılarak derlenmiş olduğu için gerçek zamanlı test bulma yalnızca yönetilen diller (C# ve Visual Basic) için çalışır. Şimdilik, gerçek zamanlı test bulma yalnızca xUnit, NUnit ve MSTest çerçeveleri için çalışır.

## <a name="test-explorer-logs"></a>Test Gezgini günlükleri

**Test Gezgini için günlükleri nasıl açabilirsiniz?**

Araçlar Seçenekler  >  **Testi'ne**  >  **gidin** ve Orada Günlük bölümünü bulun.

## <a name="uwp-test-discovery"></a>UWP test bulma

**Uygulamamı dağıtana kadar UWP projelerinde testlerim neden keşfedilmedi?**

Uygulama dağıtıldığında UWP testleri farklı bir çalışma zamanının hedefini yapar. Bu, UWP projeleri için testleri doğru şekilde bulmak için yalnızca projenizi derlemenize değil aynı zamanda dağıtmanıza da gerek olduğu anlamına gelir.

## <a name="test-explorer-sorting"></a>Test Gezgini sıralama

**Hiyerarşi görünümünde test sonuçlarını sıralama nasıl çalışır?**

Hiyerarşi görünümü testleri sonuç yerine alfabetik olarak sıralar. Ayarlara göre önceki grup, test sonuçlarını sonuca ve ardından alfabetik olarak sıralanmış. Test Gezgini'nde sütun üst bilgisinde sağ tıklayarak, State sütununu etkinleştirerek ve ardından State sütun başlığına tıklayarak bu sütuna sıralama uygulamak için sonuca göre sıralamayı etkinleştirebilirsiniz. Bu sorunda tasarım hakkında geri bildirim [GitHub sebilirsiniz.](https://github.com/Microsoft/vstest/issues/1425)

## <a name="test-explorer-hierarchy-view"></a>Test Gezgini hiyerarşi görünümü

**Hiyerarşi görünümünde, üst düğüm gruplamaları yanında geçirilen, başarısız olan, atlanan ve çalıştıramayan simgeler vardır. Bu simgeler ne anlama geliyor?**

Project, Namespace ve Class gruplamalarının yanındaki simgeler, bu gruplama içindeki testlerin durumunu gösterir. Aşağıdaki tabloya bakın.

![Test Gezgini Hiyerarşi Simgeleri](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Dosya yoluna göre arama

**Test Gezgini arama kutusunda artık "Dosya Yolu" filtresi yoktur.**

**Test** Gezgini arama kutusunda dosya yolu filtresi, 2017 Visual Studio 15.7 sürümünde kaldırıldı. Bu özelliğin kullanımı düşüktü ve Test Gezgini bu özelliği bırakarak test yöntemlerini daha hızlı alabilir. Bu değişiklik geliştirme akışınızı kesintiye uğratması için Geliştirici hesabı hakkında geri bildirim göndererek [Community.](https://aka.ms/feedback/suggest?space=8)

## <a name="remove-undocumented-interfaces"></a>Belgelenmemiş arabirimleri kaldırma

**Testle ilgili bazı API'ler artık Visual Studio 2019'da mevcut değil. Ne değişti?**

Bu Visual Studio 2019'da daha önce genel olarak işaretlenmiş ancak hiçbir zaman resmi olarak belgelenmiş olan bazı test penceresi API'leri kaldırılacaktır. Uzantı bakımcılara erken uyarı vermek için Visual Studio 2017'de "kullanım dışı" olarak işaretlendi. Çok az uzantının bu API'leri bulduğu ve bunlara bağımlı olduğu bilgisini edindi. Bunlar , `IGroupByProvider` , , , , ve `IGroupByProvider<T>` `KeyComparer` `ISearchFilter` `ISearchFilterToken` `ISearchToken` 'dır. `SearchFilterTokenType` Bu değişiklik uzantınızı etkiliyorsa, Developer Community üzerinde bir hata [doldurarak bize Community.](https://aka.ms/feedback/suggest?space=8)

## <a name="test-adapter-nuget-reference"></a>Test bağdaştırıcısı NuGet başvurusu

**Bu Visual Studio 2017 sürüm 15.8'de testlerim bulundu, ancak yürütülmedi.**

Tüm test projelerinin .csproj dosyalarında .NET test NuGet başvurularını içermesi gerekir. Yoksa, bir derlemeden sonra bir test bağdaştırıcısı uzantısı tarafından bulmanın ardından veya kullanıcı seçilen testleri çalıştırmayı deniyorsa, projede aşağıdaki test çıktısı görüntülenir:

**Test projesi {} herhangi bir .NET ağ bağdaştırıcısına NuGet değil. Test bulma veya yürütme bu proje için çalışmıyor olabilir. Çözümdeki her .NET test NuGet test bağdaştırıcılarına başvurulmanız önerilir.**

Test bağdaştırıcısı uzantılarını kullanmak yerine, projelerin test bağdaştırıcısını ve paketleri NuGet gerekir. Bu gereksinim performansı büyük ölçüde artırır ve sürekli tümleştirmeyle ilgili daha az soruna neden olur. Sürüm notlarında .NET Test Bağdaştırıcısı Uzantısının kullanım dışı bırakılası hakkında daha [fazla bilgi edinebilirsiniz.](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension)

::: moniker range="vs-2017"
> [!NOTE]
> NUnit 2 Test Bağdaştırıcısı kullanıyorsanız ve NUnit 3 test bağdaştırıcısına geçiremiyorsanız, Araçlar Seçenekler Testi'nin Visual Studio sürüm 15.8'de bu yeni bulma davranışını   >    >  **kapatabilirsiniz.**

![Araçlar seçeneklerinde Test Gezgini Bağdaştırıcı davranışı](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>UWP TestContainer bulunamadı

**UWP testlerim artık 2017 sürüm 15.7 ve Visual Studio yürütülmeyecek.**

Son UWP test projeleri, test uygulamalarını tanımlamak için daha iyi performans sağlayan bir test platformu derleme özelliği belirtir. Sürüm 15.7'den önce başlatılan bir UWP test Visual Studio, Çıktı Testlerinde bu **hatayı**  >  **alabilirsiniz:**

**System.AggregateException: Bir veya daha fazla hata oluştu. ---> System.InvalidOperationException: Aşağıdaki TestContainer {} Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider \<GetTestContainerAsync> d__61.MoveNext() içinde bulunamadı**

Bu hatayı düzeltmek için:

- Aşağıdaki kodu kullanarak test projesi derleme özelliğinizi güncelleştirin:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Aşağıdaki kodu kullanarak TestPlatform SDK sürümünü güncelleştirin:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```
::: moniker range=">=vs-2019"
## <a name="using-preview-features"></a>Önizleme özelliklerini kullanma

2019'Visual Studio'da Araçlar ve Seçenekler > **Ortam > Önizleme** Özellikleri'> seçebilirsiniz.
::: moniker-end
::: moniker range=">=vs-2017"
## <a name="using-feature-flags"></a>Özellik bayraklarını kullanma

**Yeni test özelliklerini denemek için özellik bayraklarını nasıl açabilirsiniz?**

Özellik bayrakları, ürünün deneysel veya tamamlanmamış bölümlerini, özellikler resmi olarak göndermeden önce geri bildirim vermek isteyen kullanıcılara göndermesi için kullanılır. IDE deneyiminizin kararsız hale geldi. Bunları yalnızca sanal makineler gibi güvenli geliştirme ortamlarında kullanın. Özellik bayrakları her zaman kendi risk ayarlarınıza göre kullanılır. Özellik bayrakları uzantısıyla veya [geliştirici komut istemi aracılığıyla](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension)deneysel özellikleri açabilirsiniz.

![Özellik Bayrağı Uzantısı](media/testex-featureflag.png)

Bir özellik bayrağını geliştirici komut istemi Visual Studio açmak için aşağıdaki komutu kullanın. Yolu makinenize Visual Studio ve kayıt defteri anahtarını istediğiniz özellik bayrağıyla değiştirebilirsiniz.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> dword sonrasında 1 yerine 0 değeri kullanarak bayrağını aynı komutla kapatabilirsiniz.
::: moniker-end
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Mevcut kod için birim testleri oluşturma ve çalıştırma](/previous-versions/dd293546(v=vs.110))
- [Kodunuzu birim testi](unit-test-your-code.md)
- [Canlı birim testi hakkında SSS](live-unit-testing-faq.yml)