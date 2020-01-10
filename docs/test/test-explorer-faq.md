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
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846818"
---
# <a name="visual-studio-test-explorer-faq"></a>Visual Studio Test Gezgini hakkında SSS
::: moniker range=">=vs-2019"

## <a name="where-is-group-by-traits-in-visual-studio-2019"></a>Visual Studio 2019 ' de grup nitelikleri nerede?
Bu nitelik gruplandırması bir sütun olacak şekilde taşındı. Visual Studio 2019 sürüm 16,2 ' deki çok katmanlı ve özelleştirilebilir hiyerarşiyle, nitelikleri gereksiz görsel karmaşıklık yaratan bir gruplandırma olarak da dahil ettik. Bu tasarımla ilgili geri bildirimde kesinlikle dinleme yaptık! https://developercommunity.visualstudio.com/content/problem/588029/no-longer-able-to-group-by-trait-in-test-explorer.html

Şimdilik, test Gezgini 'ndeki sütuna sağ tıklayıp sütunlar ' ı seçebilirsiniz. Nitelik sütununu kontrol edin ve test Gezgini 'nde görünür. Artık bu sütunu, ilgilendiğiniz nitelikleri filtreleyerek filtreleyebilirsiniz.

nitelik sütununu filtrelemek ![nitelik sütununu](media/vs-2019/trait-column.png)
![görüntüleyin](media/vs-2019/trait-column-filter.png)
::: moniker-end

## <a name="dynamic-test-discovery"></a>Dinamik test bulma

**Test Gezgini, dinamik olarak tanımlanan sınamalarımı bulmıyor. (Örneğin, bu özel bağdaştırıcılar, özel nitelikler, #ifdefs vb.) Bu testleri nasıl keşfedebilirim?**

::: moniker range=">=vs-2019"
Derleme tabanlı bulma çalıştırmak için projenizi derleyin.
::: moniker-end
::: moniker range="vs-2017"
Projenizi derleyin ve **araçlar** > **Seçenekler** > **Test**' de derleme tabanlı bulmanın açık olduğundan emin olun.
::: moniker-end
[Gerçek zamanlı test bulma](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) kaynak tabanlı test bulma. Çalışma zamanında tanımlandıklarından, bu, özel bağdaştırıcılar, özel nitelikler, `#ifdef` deyimlerini ve daha fazlasını kullanan testleri bulamaz. Bir derleme, bu testler doğru bir şekilde bulunması gereklidir. Visual Studio 2017 sürüm 15.6 ve daha sonra derleme tabanlı bulma (Geleneksel Bulucu) yalnızca derlemeler sonra çalışır. Bu yöntem gerçek zamanlı test bulma işleminin, düzenlerken mümkün olduğunca çok testleri ayarlama ve derleme tabanlı bulma, dinamik olarak tanımlanan testleri, derleme sonrası görünmesini sağlar. Gerçek zamanlı test bulma, yanıt hızını iyileştirir, ancak yine de bir derlemeden sonra tam ve kesin sonuçlar almanızı sağlar.

## <a name="test-explorer--plus-symbol"></a>Test Gezgini '+' (sembolü artı)

**Ne yaptığını '+' (artı) Test Gezgini ortalama ilk satırda görünen simge?**

' + ' (Artı) simgesi, derleme tabanlı bulma çalıştığında bir derlemeden sonra daha fazla testin bulunabileceğini gösterir. Test projenizde algılanan dinamik olarak tanımlanmışsa bu simge görünür.

![Artı özet satırı simgesi](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>Derleme tabanlı bulma

**Derleme tabanlı bulma artık projem için çalışmıyor. Nasıl yaparım? yeniden açılsın mı?**

**Araçlar** > **Seçenekler** > **Test** ' e gidin ve **derleme sonrasında oluşturulan derlemelerin testlerini ek olarak bul** kutusunu işaretleyin.

![Derleme tabanlı seçeneği](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Gerçek zamanlı test bulma

**Testler, projem oluşturmaya gerek kalmadan yazarken test Gezgini 'nde görünür. Ne değişti?**

Bu özelliğin adı [gerçek zamanlı test bulma](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/). Testleri bulmak ve Test Gezgini, projenizi oluşturmaya gerek kalmadan gerçek zamanlı olarak doldurmak için Roslyn çözümleyicinizi kullanır. Yer veya özel nitelikler gibi dinamik olarak tanımlanmış testlerin test bulma davranışı hakkında daha fazla bilgi için bkz. [dinamik test bulma](#dynamic-test-discovery).

## <a name="real-time-test-discovery-compatibility"></a>Gerçek zamanlı test bulma uyumluluğu

**Gerçek zamanlı Test bulma, hangi diller ve test çerçeveleri kullanabilir miyim?**

[Gerçek zamanlı test bulma](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) yalnızca yönetilen diller için çalışır (C# ve Visual Basic), bu yana Roslyn derleyicisi kullanılarak oluşturulmuştur. Şimdilik, gerçek zamanlı test bulma yalnızca xUnit, NUnit ve MSTest çerçeveleri çalışır.

## <a name="test-explorer-logs"></a>Test Gezgini günlükleri

**Test Gezgini için nasıl günlüklerini kapatırım?**

Gidin **Araçları** > **seçenekleri** > **Test** ve günlüğe kaydetme bölümü bulun.

## <a name="uwp-test-discovery"></a>UWP test bulma

**Neden testlerimi uygulamamı dağıtabilirim kadar bulunmayan UWP projelerinde?**

Uygulama dağıtıldığında UWP testler farklı bir çalışma zamanı hedef. Bu, doğru bir şekilde UWP projeleri için testleri bulmak için yalnızca derleme, ancak ayrıca dağıtmanız gerektiğini anlamına gelir.

## <a name="test-explorer-sorting"></a>Test Gezgini sıralama

**Sıralama test sonuçlarını hiyerarşi Görünümü'nde nasıl çalışır?**

Hiyerarşi görünümü alfabetik olarak öğesine test sonucuna göre sıralar. Diğer grubun ayarlarını normalde test sonuçlarını sonucuna göre sıralama ve alfabetik olarak. Aşağıdaki görüntüde karşılaştırma için seçenekleri tarafından farklı bir gruba bakın. Tasarım hakkında geri bildirim sağlayabilirsiniz [bu GitHub sorunu içinde](https://github.com/Microsoft/vstest/issues/1425).

![SortingExamples](media/testex-sortingex.png)

## <a name="test-explorer-hierarchy-view"></a>Test Gezgini hiyerarşi görünümü

**Hiyerarşi görünümünde, üst düğüm Gruplandırmaların yanında başarılı, başarısız, atlandı ve çalıştırılmadı simgeleri yok. Bu simgeler ne anlama geliyor?**

Proje ve Namespace sınıfını gruplandırmaları yanındaki simge, o grup içindeki testlerin durumunu gösterir. Aşağıdaki tabloya bakın.

![Test Gezgini hiyerarşi simgeleri](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Dosya yoluna göre arama

**Test Gezgini arama kutusuna artık "Dosya yolu" filtresi var.**

**Test Gezgini** arama kutusundaki dosya yolu filtresi, Visual Studio 2017 sürüm 15,7 ' de kaldırılmıştır. Bu özelliğin kullanımı düşük ve test Gezgini bu özelliği bırakarak test yöntemlerini hızlı bir şekilde alabilir. Bu değişiklik, geliştirme akışınızı keser, hakkında geri bildirim göndererek bize [Geliştirici topluluğu](https://developercommunity.visualstudio.com/).

## <a name="remove-undocumented-interfaces"></a>Belgelenmemiş arabirimleri Kaldır

**Visual Studio 2019 ' de test ile ilgili bazı API 'Ler artık mevcut değildir. Ne değişti?**

Visual Studio 2019 ', bazı test penceresi daha önce genel olarak işaretlenmiş, ancak hiçbir zaman resmi olarak belgelenen API'leri kaldırılacak. Bunlar, "Visual Studio uzantısı maintainers erken bir uyarı vermek için 2017'de kullanım dışı"olarak işaretlenmiş. Bizim bilgi için çok az sayıda uzantıları bu API'leri bulundu ve bir bağımlılık bunlar üzerinde gerçekleştirilen. Bunlar `IGroupByProvider`, `IGroupByProvider<T>`, `KeyComparer`, `ISearchFilter`, `ISearchFilterToken`, `ISearchToken`, ve `SearchFilterTokenType`. Bu değişiklik uzantınızı etkiliyorsa, üzerinde bir hatayı dosyalama bize [Geliştirici topluluğu](https://developercommunity.visualstudio.com).

## <a name="test-adapter-nuget-reference"></a>Test bağdaştırıcısı NuGet başvurusu

**Visual Studio 2017 sürüm 15,8 testlerimi bulunan, ancak yürütme yok.**

Tüm test projelerinde, .csproj dosyasında kendi .NET test bağdaştırıcısı NuGet başvuru içermelidir. Hizmet sağlanmıyorsa aşağıdaki test çıkışı projede derleme sonrası bulma bir test bağdaştırıcısı uzantısı tarafından başlatılır veya kullanıcı seçili testleri çalıştırmayı dener görünür:

**Test projesi {} hiçbir .NET NuGet bağdaştırıcısına başvurmuyor. Test bulma veya yürütme bu proje için çalışmayabilir. Çözümdeki her bir .NET Test projesinde NuGet test bağdaştırıcılarına başvurmak için önerilir.**

Test bağdaştırıcısı uzantılarından kullanmak yerine, projeleri test bağdaştırıcısı NuGet paketlerini kullanmak için gerekli değildir. Bu gereksinim, büyük ölçüde performansı artırır ve daha az sorunları ile sürekli tümleştirme neden olur. .NET Test bağdaştırıcısı uzantısı kullanımdan kaldırma hakkında daha fazla bilgiyi [sürüm notları](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension).

::: moniker range="vs-2017"
> [!NOTE]
> NUnit 3 test bağdaştırıcısı'na yükseltemedi olan ve NUnit 2 Test bağdaştırıcısı kullanıyorsanız, bu yeni Visual Studio sürümünde 15,8 bulma davranışı kapatabilirsiniz **Araçları** > **seçenekleri**  >  **Test**.

![Araçlar seçeneklerinde Gezgini bağdaştırıcısı davranışını sınama](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>UWP TestContainer bulunamadı

**UWP testleriniz artık Visual Studio 2017 sürüm 15,7 ve sonrasında yürütülmiyor.**

Son UWP test projeleri, test uygulamaları tanımlamak için daha iyi performans sağlayan bir test platformu yapı özelliğini belirtin. Visual Studio 15.7 Sürüm önce başlatıldı bir UWP test projesi varsa, bu hatayı görebilirsiniz **çıkış** > **testleri**:

**System. AggregateException: bir veya daha fazla hata oluştu. System. InvalidOperationException >---: aşağıdaki TestContainer bulunamadı {} Microsoft. VisualStudio. TestWindow. Controller. TestContainerProvider \<Gettestcontainsilinebilir Sync > d__61. MoveNext ()**

Bu hatayı düzeltmek için:

- Aşağıdaki kodu kullanarak, test projesi yapı özelliği güncelleştirin:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Aşağıdaki kodu kullanarak TestPlatform SDK sürümü güncelleştir:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```

## <a name="using-feature-flags"></a>Özellik bayraklarını kullanarak

**Yeni test özellikleri denemek için özellik bayraklarını üzerinde nasıl kapatabilir miyim?**

Özellik bayrakları, ürün özellikleri resmi olarak sevk etmeden önce geri bildirim sağlamak ister misiniz kullanıcılar avid Deneysel veya tamamlanmamış bölümlerini göndermeye kullanılır. Bunlar, IDE deneyimi kararlılığını. Yalnızca güvenli geliştirme ortamlarında, sanal makineler gibi bunları kullanın. Özellik bayrakları her zaman kullanın--your-kendi-riskli ayarlarıdır. Deneysel özellikler ile etkinleştirebilirsiniz [özellik bayraklarını uzantısı](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension), veya Geliştirici komut istemi aracılığıyla.

![Özellik bayrağı uzantısı](media/testex-featureflag.png)

Visual Studio Geliştirici komut istemi üzerinden bir özellik bayrağını etkinleştirmek için aşağıdaki komutu kullanın. Yol, Visual Studio makinenizde yüklü olduğu için ve kayıt defteri anahtarı istediğiniz özellik bayrağını değiştirin.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Dword sonra 1 yerine 0 değerini kullanarak aynı komutla bayrağı kapatabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Oluşturma ve mevcut koda yönelik birim testleri çalıştırma](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Birim testi kod](unit-test-your-code.md)
- [Canlı birim testi ile ilgili SSS](live-unit-testing-faq.md)
