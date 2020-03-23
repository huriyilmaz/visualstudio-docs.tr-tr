---
title: Test Gezgini Hakkında SSS
ms.date: 08/14/2019
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
manager: jillfra
ms.openlocfilehash: cec8ea3ea091ab1ea65bcad2bd4cca139fd74042
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75846818"
---
# <a name="visual-studio-test-explorer-faq"></a>Visual Studio Test Explorer SSS
::: moniker range=">=vs-2019"

## <a name="where-is-group-by-traits-in-visual-studio-2019"></a>Visual Studio 2019'da Özellikler'e göre grup nerede?
Bu Özellik gruplandırmabir sütun olarak taşındı. Visual Studio 2019 sürüm 16.2'deki çok katmanlı ve özelleştirilebilir hiyerarşi ile, bir gruplama olarak özelliklerin gereksiz görsel karmaşıklık yarattığını düşündük. Biz kesinlikle bu tasarım geribildirim dinliyoruz! https://developercommunity.visualstudio.com/content/problem/588029/no-longer-able-to-group-by-trait-in-test-explorer.html

Şimdilik, Test Gezgini'ndeki sütuna sağ tıklayıp Sütunlar'ı seçebilirsiniz. Özellik sütununa bakın ve Test Gezgini'nde görünecektir. Artık bu sütunu ilgilendiğiniz özelliklere göre filtreleyebilirsiniz.

![Özellik sütununa](media/vs-2019/trait-column.png)
![filtre uygulayın özellik sütunu](media/vs-2019/trait-column-filter.png)
::: moniker-end

## <a name="dynamic-test-discovery"></a>Dinamik test bulma

**Test Gezgini dinamik olarak tanımlanmış testlerimi keşfetmiyor. (Örneğin, teoriler, özel adaptörler, özel özellikler, #ifdefs, vb.) Bu testleri nasıl keşfedebilirim?**

::: moniker range=">=vs-2019"
Derleme tabanlı keşfi çalıştırmak için projenizi oluşturun.
::: moniker-end
::: moniker range="vs-2017"
**Projenizi** > oluşturun ve Araçlar **Seçenekleri** > **Testi'nde**montaj tabanlı keşfin açık olduğundan emin olun.
::: moniker-end
[Gerçek zamanlı test bulma](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) kaynak tabanlı test bulma. Çalışma zamanında tanımlandıkları için teorileri, özel bağdaştırıcıları, özel özellikleri, `#ifdef` ifadeleri ve daha fazlasını kullanan testleri keşfedemez. Bu testlerin doğru bir şekilde bulunabilmek için bir yapı gereklidir. Visual Studio 2017 sürüm 15.6 ve sonraki sürümlerinde, montaj tabanlı keşif (geleneksel kaşif) yalnızca yapılardan sonra çalışır. Bu ayar, gerçek zamanlı test bulmanın siz düzenlerken olabildiğince çok test bulduğu anlamına gelir ve derleme tabanlı bulma, bir yapıdan sonra dinamik olarak tanımlanmış testlerin görünmesini sağlar. Gerçek zamanlı test bulma yanıt geliştirir, ama yine de bir yapı sonra tam ve kesin sonuçlar elde etmenizi sağlar.

## <a name="test-explorer--plus-symbol"></a>Test Gezgini '+' (artı) simgesi

**Test Gezgini'nin üst satırında görünen '+' (artı) sembolü ne anlama gelir?**

'+' (artı) sembolü, derleme tabanlı keşif çalıştığında bir yapıdan sonra daha fazla testin keşfedilen olabileceğini gösterir. Projenizde dinamik olarak tanımlanmış testler algılanırsa bu sembol görüntülenir.

![Artı sembolü özet satırı](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>Montaj tabanlı keşif

**Derleme tabanlı keşif artık projem için çalışmıyor. Nasıl açabilirim?**

**Araçlar** > **Seçenekleri** > **Testi'ne** gidin ve **yapılardan sonra yerleşik derlemelerin testlerini ek olarak keşfetmek** için kutuyu işaretleyin.

![Derleme tabanlı seçenek](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Gerçek zamanlı test bulma

**Testleri şimdi test gezgini ben yazarken görünür, benim proje oluşturmak zorunda kalmadan. Ne değişti?**

Bu özellik [Gerçek zamanlı test bulma](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/)olarak adlandırılır. Projenizi oluşturmanıza gerek kalmadan testleri bulmak ve Test Gezgini'ni gerçek zamanlı olarak doldurmak için bir Roslyn çözümleyicisi kullanır. Teoriler veya özel özellikler gibi dinamik olarak tanımlanmış testler için test bulma davranışı hakkında daha fazla bilgi için [Dinamik test keşfine](#dynamic-test-discovery)bakın.

## <a name="real-time-test-discovery-compatibility"></a>Gerçek zamanlı test bulma uyumluluğu

**Hangi diller ve test çerçeveleri Gerçek Zamanlı Test Bulma'yı kullanabilir?**

[Gerçek zamanlı test bulma,](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) Roslyn derleyicisi kullanılarak üretildiği için yalnızca yönetilen dillerde (C# ve Visual Basic) çalışır. Şimdilik, gerçek zamanlı test bulma yalnızca xUnit, NUnit ve MSTest çerçeveleri için çalışır.

## <a name="test-explorer-logs"></a>Test Gezgini günlükleri

**Test Gezgini için günlükleri nasıl açabilirim?**

**Araçlar** > **Seçenekleri** > **Testi'ne** gidin ve GünlükLe bölümünü buradan bulun.

## <a name="uwp-test-discovery"></a>UWP test bulma

**Uygulamamı dağıtana kadar UWP projelerindeki testlerim neden keşfedilmedi?**

UWP testleri, uygulama dağıtıldığında farklı bir çalışma süresini hedeflemeyi hedeflemez. Bu, UWP projeleri için testleri doğru bulmak için yalnızca projenizi oluşturmanız değil, aynı zamanda dağıtmanız gerektiği anlamına gelir.

## <a name="test-explorer-sorting"></a>Test Gezgini sıralama

**Sıralama testi sonuçları hiyerarşi görünümünde nasıl çalışır?**

Hiyerarşi görünümü, sonuçları yerine testleri alfabetik olarak sıralar. Diğer grup ayarlarına göre normalde sonuç ve sonra alfabetik test sonuçlarını sıralamak. Karşılaştırma için aşağıdaki resimdeki seçeneklere göre farklı gruba bakın. [Bu GitHub sayısında](https://github.com/Microsoft/vstest/issues/1425)tasarım hakkında geri bildirim sağlayabilirsiniz.

![Sıralama Örnekleri](media/testex-sortingex.png)

## <a name="test-explorer-hierarchy-view"></a>Test Gezgini hiyerarşi görünümü

**Hiyerarşi görünümünde, geçti, başarısız, atlanır ve üst düğüm gruplandırmaları yanında simgeleri çalıştırılamadı. Bu simgeler ne anlama geliyor?**

Project, Namespace ve Class gruplandırmalarının yanındaki simgeler, bu gruplandırmadaki testlerin durumunu gösterir. Aşağıdaki tabloya bakın.

![Gezgin Hiyerarşi Simgelertest](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Dosya yoluna göre arama

**Test Gezgini arama kutusunda artık bir "Dosya Yolu" filtresi yok.**

**Test Gezgini** arama kutusundaki dosya yolu filtresi Visual Studio 2017 sürüm 15.7'de kaldırıldı. Bu özellik düşük kullanıma sahipti ve Test Gezgini bu özelliği dışarıda bırakarak test yöntemlerini daha hızlı alabilir. Bu değişiklik geliştirme akışınızı kesintiye uğrayırsa, [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/)hakkında geri bildirim göndererek bize bildirin.

## <a name="remove-undocumented-interfaces"></a>Belgelenmemiş arabirimleri kaldırma

**Testle ilgili bazı API'ler Visual Studio 2019'da artık mevcut değildir. Ne değişti?**

Visual Studio 2019'da, daha önce herkese açık olarak işaretlenmiş ancak resmi olarak belgelenmemiş bazı test penceresi API'leri kaldırılacaktır. Visual Studio 2017'de uzatmacılarına erken uyarı vermek için "amortismana uğradılar" olarak işaretlendiler. Bilgimiz için, çok az uzantıları bu API'ler bulmuş ve onlara bir bağımlılık almıştır. Bunlar `IGroupByProvider`arasında `IGroupByProvider<T>` `KeyComparer`, `ISearchFilter` `ISearchFilterToken`, `ISearchToken`, `SearchFilterTokenType`, , , ve . Bu değişiklik uzantınızı etkiliyorsa, Geliştirici [Topluluğu'na](https://developercommunity.visualstudio.com)bir hata doldurarak bize bildirin.

## <a name="test-adapter-nuget-reference"></a>Test adaptörü NuGet referansı

**Visual Studio 2017 sürüm 15.8'de testlerim keşfedildi, ancak yürütmeyin.**

Tüm test projeleri .NET test bağdaştırıcısı NuGet başvurularını .csproj dosyasına içermelidir. Bunu yapmazlarsa, bir test bağdaştırıcısı uzantısı tarafından keşfe başladıktan sonra veya kullanıcı seçili testleri çalıştırmaya çalışırsa, projede aşağıdaki test çıktısı görüntülenir:

**Test {} projesi herhangi bir .NET NuGet bağdaştırıcısına başvurulmaz. Test bulma veya yürütme bu proje için çalışmayabilir. Çözümdeki her bir .NET test projesinde NuGet test bağdaştırıcılarına başvurulması önerilir.**

Test bağdaştırıcıuzantıları kullanmak yerine, projelerin test bağdaştırıcısı NuGet paketlerini kullanması gerekir. Bu gereksinim performansı büyük ölçüde artırır ve sürekli tümleştirme ile ilgili daha az soruna neden olur. .NET Test Adaptörü Uzantısı amortismanı hakkında daha fazla bilgi [için yayın notlarında](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension).

::: moniker range="vs-2017"
> [!NOTE]
> NUnit 2 Test Bağdaştırıcısını kullanıyorsanız ve NUnit 3 test bağdaştırıcısına geçiremiyorsanız, **Araçlar** > **Seçenekleri** > **Testi'ndeki**Visual Studio sürüm 15.8'deki bu yeni keşif davranışını kapatabilirsiniz.

![Araçlar seçeneklerinde Explorer Bağdaştırıcısı davranışını test edin](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>UWP TestContainer bulunamadı

**UWP testlerim artık Visual Studio 2017 sürüm 15.7 ve sonraki sürümlerde yürütülmemektedir.**

Son UWP test projeleri, test uygulamalarını tanımlamak için daha iyi performans sağlayan bir test platformu oluşturma özelliği belirtir. Visual Studio sürüm 15.7'den önce başharfe çevrilmiş bir UWP test projeniz varsa, **Çıktı** > **Testleri'nde**bu hatayı görebilirsiniz:

**System.AggregateException: Bir veya daha fazla hata oluştu. ---> System.InvalidOperationException: Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider {} \<GetTestContainerAsync>d__61.MoveNext() adresinde aşağıdaki TestContainer bulunamadı**

Bu hatayı düzeltmek için:

- Test proje oluşturma özelliğinizi aşağıdaki kodu kullanarak güncelleştirin:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- TestPlatform SDK sürümünü aşağıdaki kodu kullanarak güncelleyin:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```

## <a name="using-feature-flags"></a>Özellik bayraklarını kullanma

**Yeni test özelliklerini denemek için özellik bayraklarını nasıl açabilirim?**

Özellik bayrakları, özelliklerin resmi olarak sevkinden önce geri bildirimde bulunan hevesli kullanıcılara ürünün deneysel veya bitmemiş parçalarını sevk etmek için kullanılır. IDE deneyiminizi bozabilir. Bunları yalnızca sanal makineler gibi güvenli geliştirme ortamlarında kullanın. Özellik bayrakları her zaman kendi risk ayarlarınızı kullanır. [Özellik bayrakları uzantısı](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension)ile veya geliştirici komut istemi aracılığıyla deneysel özellikleri açabilirsiniz.

![Özellik Bayrağı Uzantısı](media/testex-featureflag.png)

Visual Studio geliştirici komut istemi aracılığıyla bir özellik bayrağını açmak için aşağıdaki komutu kullanın. Görsel Stüdyo'nun makinenizde yüklü olduğu yolu değiştirin ve kayıt defteri anahtarını istediğiniz özellik bayrağıyla değiştirin.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Dword'den sonra 1 yerine 0 değerini kullanarak bayrağı aynı komutla kapatabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Varolan kod için birim testleri oluşturma ve çalıştırma](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Birim kodunuzu test edin](unit-test-your-code.md)
- [Canlı ünite testi SSS](live-unit-testing-faq.md)
