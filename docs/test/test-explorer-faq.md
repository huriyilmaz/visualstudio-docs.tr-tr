---
title: Test Gezgini Hakkında SSS
description: Visual Studio Test Gezgini hakkında, yaygın olarak karşılaşılan bazı sorunları içeren bu sık sorulan sorulara bakın.
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
ms.openlocfilehash: 22ac969ba2ad918fcbeb7c53e04cd3f2b03a0431
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798576"
---
# <a name="visual-studio-test-explorer-faq"></a>Visual Studio Test Gezgini hakkında SSS

## <a name="dynamic-test-discovery"></a>Dinamik test bulma

**Test Gezgini, dinamik olarak tanımlanan sınamalarımı bulmıyor. (Örneğin, bu özel bağdaştırıcılar, özel nitelikler, #ifdefs vb.) Bu testleri nasıl keşfedebilirim?**

::: moniker range=">=vs-2019"
Derleme tabanlı bulma çalıştırmak için projenizi derleyin.
::: moniker-end
::: moniker range="vs-2017"
Projenizi derleyin ve **Araçlar** > **Seçenekler** > **testinde** derleme tabanlı bulmanın açık olduğundan emin olun.
::: moniker-end
Gerçek zamanlı test bulma, kaynak tabanlı test [bulgusunu](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) . Çalışma zamanında tanımlandıklarından, bu, özel bağdaştırıcılar, özel nitelikler, `#ifdef` deyimler ve daha fazlasını kullanan testleri bulamaz. Bu testlerin doğru şekilde bulunması için bir derleme gereklidir. Visual Studio 2017 sürüm 15,6 ve üzeri sürümlerde, derleme tabanlı bulma (geleneksel Discoverer) yalnızca derlemeler sonrasında çalışır. Bu ayar, gerçek zamanlı test bulmanın, düzenlemekte olduğunuz kadar çok test bulduğu ve derleme tabanlı bulma, dinamik olarak tanımlanan testlerin bir derlemeden sonra görünmesine izin veriyor demektir. Gerçek zamanlı test bulma, yanıt hızını iyileştirir, ancak yine de bir derlemeden sonra tam ve kesin sonuçlar almanızı sağlar.

## <a name="test-explorer--plus-symbol"></a>Test Gezgini ' + ' (artı) simgesi

**Test Gezgini 'nin en üst satırında görünen ' + ' (artı) simgesi ne anlama geliyor?**

' + ' (Artı) simgesi, derleme tabanlı bulma çalıştığında bir derlemeden sonra daha fazla testin bulunabileceğini gösterir. Projenizde dinamik olarak tanımlanmış testler algılanırsa bu simge görüntülenir.

![Artı simgesi özet çizgisi](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>Bütünleştirilmiş kod tabanlı bulma

**Derleme tabanlı bulma artık projem için çalışmıyor. Nasıl yaparım? yeniden açılsın mı?**

**Araçlar** > **Seçenekler** > **Test** ' e gidin ve **derleme sonrasında oluşturulan derlemelerin testlerini ek olarak bul** kutusunu işaretleyin.

![Derleme tabanlı seçenek](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Gerçek zamanlı test bulma

**Testler artık projemi derlemek zorunda kalmadan yazma sırasında Test Gezgini'nde görünür. Ne değişti?**

Bu özellik, gerçek [zamanlı test bulma olarak adlandırılan bir özelliktir.](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) Projenizi derlemenize gerek kalmadan testleri bulmak ve Test Gezgini'ni gerçek zamanlı olarak doldurmak için Roslyn çözümleyicisini kullanır. Teoriler veya özel nitelikler gibi dinamik olarak tanımlanmış testlerde test bulma davranışı hakkında daha fazla bilgi için [bkz. Dinamik test bulma](#dynamic-test-discovery).

## <a name="real-time-test-discovery-compatibility"></a>Gerçek zamanlı test bulma uyumluluğu

**Hangi diller ve test çerçeveleri Gerçek Zamanlı Test Bulma kullanabilir?**

[Roslyn derleyicisi](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) kullanılarak derlenmiş olduğu için gerçek zamanlı test bulma yalnızca yönetilen diller (C# ve Visual Basic) için çalışır. Şimdilik, gerçek zamanlı test bulma yalnızca xUnit, NUnit ve MSTest çerçeveleri için çalışır.

## <a name="test-explorer-logs"></a>Test Gezgini günlükleri

**Test Gezgini için günlükleri nasıl açabilirsiniz?**

Araçlar Seçenekler  >  **Testi'ne**  >  **gidin** ve Orada Günlük bölümünü bulun.

## <a name="uwp-test-discovery"></a>UWP test bulma

**Uygulamamı dağıtana kadar UWP projelerinde testlerim neden keşfedilmedi?**

Uygulama dağıtıldığında UWP testleri farklı bir çalışma zamanının hedefini yapar. Bu, UWP projeleri için testleri doğru şekilde bulmak için yalnızca projenizi derlemenize değil aynı zamanda dağıtmanıza da gerek olduğu anlamına gelir.

## <a name="test-explorer-sorting"></a>Test Gezgini sıralama

**Hiyerarşi görünümünde test sonuçlarını sıralama nasıl çalışır?**

Hiyerarşi görünümü testleri sonuç yerine alfabetik olarak sıralar. Ayarlara göre önceki gruplandırma, test sonuçlarını sonuca göre sıralar ve sonra alfabetik olarak sıralanır. Test Gezgini 'nde sütun başlığına sağ tıklayıp durum sütununu etkinleştirerek ve sonra bu sütuna sıralama uygulamak için durum sütunu başlığına tıklayarak sonuçlara göre sıralamayı etkinleştirebilirsiniz. Bu [GitHub sorununun](https://github.com/Microsoft/vstest/issues/1425)tasarımı hakkında geri bildirim sağlayabilirsiniz.

## <a name="test-explorer-hierarchy-view"></a>Test Gezgini hiyerarşi görünümü

**Hiyerarşi görünümünde, üst düğüm Gruplandırmaların yanında başarılı, başarısız, atlandı ve çalıştırılmadı simgeleri yok. Bu simgeler ne anlama geliyor?**

Projenin, ad alanının ve sınıf Gruplandırmaların yanındaki simgeler, bu gruplandırma içindeki testlerin durumunu gösterir. Aşağıdaki tabloya bakın.

![Test Gezgini hiyerarşi simgeleri](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Dosya yoluna göre ara

**Test Gezgini arama kutusunda artık bir "dosya yolu" filtresi yoktur.**

**Test Gezgini** arama kutusundaki dosya yolu filtresi, Visual Studio 2017 sürüm 15,7 ' de kaldırılmıştır. Bu özelliğin kullanımı düşük ve test Gezgini bu özelliği bırakarak test yöntemlerini hızlı bir şekilde alabilir. Bu değişiklik geliştirme akışınızı kesintiye uğratır, [Geliştirici topluluğu](https://aka.ms/feedback/suggest?space=8)hakkında geri bildirim göndererek bize bilgi verin.

## <a name="remove-undocumented-interfaces"></a>Belgelenmemiş arabirimleri kaldır

**Visual Studio 2019 ' de test ile ilgili bazı API 'Ler artık mevcut değildir. Ne değişti?**

Visual Studio 2019 ' de, daha önce genel olarak işaretlenmiş ancak hiç resmi olarak belgelenmeyen bazı test penceresi API 'Leri kaldırılacaktır. Uzantıya bir erken uyarı vermek için Visual Studio 2017 ' de "kullanım dışı" olarak işaretlenmişler. Bilgimize çok az sayıda uzantı bu API 'Leri bulmuştur ve bunlara bir bağımlılık aldı. Bunlar,,,,, `IGroupByProvider` `IGroupByProvider<T>` ve içerir `KeyComparer` `ISearchFilter` `ISearchFilterToken` `ISearchToken` `SearchFilterTokenType` . Bu değişiklik uzantınızı etkiliyorsa, [Geliştirici topluluğu](https://aka.ms/feedback/suggest?space=8)'nda bir hata kaydederek bize bilgi verin.

## <a name="test-adapter-nuget-reference"></a>Test bağdaştırıcısı NuGet başvurusu

**Bu Visual Studio 2017 sürüm 15.8'de testlerim bulundu, ancak yürütülmedi.**

Tüm test projelerinin .csproj dosyalarında .NET test bağdaştırıcısı NuGet başvurularını içermesi gerekir. Yoksa, bir derlemeden sonra bir test bağdaştırıcısı uzantısı tarafından bulmanın ardından veya kullanıcı seçilen testleri çalıştırmayı deniyorsa, projede aşağıdaki test çıktısı görüntülenir:

**Test projesi {} herhangi bir .NET NuGet bağdaştırıcısına başvurur. Test bulma veya yürütme bu proje için çalışmıyor olabilir. Çözümdeki her .NET test projesinde NuGet test bağdaştırıcılarına başvurulmanız önerilir.**

Test bağdaştırıcısı uzantıları kullanmak yerine projelerin test bağdaştırıcısı NuGet paketlerini kullanması gerekir. Bu gereksinim performansı büyük ölçüde artırır ve sürekli tümleştirmeyle ilgili daha az soruna neden olur. Sürüm notlarında .NET Test Bağdaştırıcısı Uzantısının kullanım dışı bırakılası hakkında daha [fazla bilgi edinebilirsiniz.](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension)

::: moniker range="vs-2017"
> [!NOTE]
> NUnit 2 Test Bağdaştırıcısı kullanıyorsanız ve NUnit 3 test bağdaştırıcısına geçiremiyorsanız, Araçlar Seçenekler Testi'nin Visual Studio sürüm 15.8'de bu yeni bulma davranışını   >    >  **kapatabilirsiniz.**

![Araçlar seçeneklerinde Test Gezgini Bağdaştırıcı davranışı](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>UWP TestContainer bulunamadı

**UWP testlerim artık 2017 Visual Studio 15.7 ve sonraki sürümlerde yürütülmeyecek.**

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

Visual Studio 2019 ' de **araçlar > seçenekler > ortam > Önizleme özellikleri**' nde önizleme özelliklerine sahip olabilirsiniz.
::: moniker-end
::: moniker range=">=vs-2017"
## <a name="using-feature-flags"></a>Özellik bayraklarını kullanma

**Yeni test özelliklerini denemek için özellik bayraklarını nasıl etkinleştirebilirim?**

Özellik bayrakları, ürünün deneysel veya tamamlanmamış parçalarını, Özellikler resmi olarak göndermeden önce geri bildirimde bulunmak isteyen AVID kullanıcılarına göndermek için kullanılır. IDE deneyiminizin kararlılığını bozabilir. Onları yalnızca sanal makineler gibi güvenli geliştirme ortamlarında kullanın. Özellik bayrakları her zaman kendi kendinize ait risk ayarlarını kullanır. [Özellik bayrakları uzantısıyla](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension)veya geliştirici komut istemi aracılığıyla deneysel özellikleri açabilirsiniz.

![Özellik bayrağı uzantısı](media/testex-featureflag.png)

Visual Studio Geliştirici komut istemi aracılığıyla bir özellik bayrağını açmak için aşağıdaki komutu kullanın. Yolu, Visual Studio 'Nun makinenizde yüklü olduğu konum olarak değiştirin ve kayıt defteri anahtarını istediğiniz özellik bayrağıyla değiştirin.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> DWORD sonrasında 1 yerine 0 değerini kullanarak bayrağı aynı komutla devre dışı bırakabilirsiniz.
::: moniker-end
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Mevcut kod için birim testleri oluşturma ve çalıştırma](/previous-versions/dd293546(v=vs.110))
- [Kodunuzun birim testi](unit-test-your-code.md)
- [Canlı birim testi SSS](live-unit-testing-faq.yml)