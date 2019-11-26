---
title: Test Gezgini ile birim testleri çalıştırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
ms.assetid: 91b167a3-280a-498b-8fc2-f67859a2c64e
caps.latest.revision: 29
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 56f2d4cb0b02cc661177a4f781a5c40db924ee2c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302110"
---
# <a name="run-unit-tests-with-test-explorer"></a>Test Gezgini ile birim testleri çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio veya üçüncü taraf birim testi projelerinden birim testlerini çalıştırmak, testleri kategoriler halinde gruplamak, test listesini filtrelemek ve testlerin çalma listelerini oluşturmak, kaydetmek ve çalıştırmak için test Gezgini 'ni kullanın. Ayrıca, testlerin hatalarını ayıklayabilir ve test performansını ve kod kapsamını çözümleyebilirsiniz.

## <a name="BKMK_Contents"></a>Dekiler
 [Birim test çerçeveleri ve test projeleri](#BKMK_Unit_test_frameworks_and_test_projects)

 [Testleri test Gezgini 'nde Çalıştır](#BKMK_Run_tests_in_Test_Explorer)

 [Test sonuçlarını görüntüle](#BKMK_View_test_results)

 [Test listesini gruplandırma ve filtreleme](#BKMK_Group_and_filter_the_test_list)

 [Özel çalma listeleri oluşturma](#BKMK_Create_custom_playlists)

 [Hata ayıklama ve birim testlerini analiz etme](#BKMK_Debug_and_analyze_unit_tests)

 [Dış kaynaklar](#BKMK_External_resources)

## <a name="BKMK_Unit_test_frameworks_and_test_projects"></a>Birim test çerçeveleri ve test projeleri
 Visual Studio hem yönetilen hem de yerel kod için Microsoft birim testi çerçeveleri içerir. Ancak, test Gezgini, test Gezgini bağdaştırıcısı uygulayan herhangi bir birim test çerçevesini de çalıştırabilir. Üçüncü taraf birim testi çerçevelerini yükleme hakkında daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçeveleri yükleme](../test/install-third-party-unit-test-frameworks.md)

 Test Gezgini, bir çözümde birden çok test projesini ve üretim kodu projelerin bir parçası olan test sınıflarından testleri çalıştırabilirsiniz. Test projeleri, farklı birim testi çerçeveleri kullanabilir. Test edilen kod .NET Framework için yazıldığında, test projesi, hedef kodun dilinden bağımsız olarak, .NET Framework de hedefleyen herhangi bir dilde yazılabilir. Yerel C/C++ kod projeleri, bir C++ birim test çerçevesi kullanılarak test edilmelidir.

 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="BKMK_Run_tests_in_Test_Explorer"></a>Testleri test Gezgini 'nde Çalıştır
 [Testleri](#BKMK_Run_tests) **&#124;** Çalıştır [her derlemeden sonra Testleri Çalıştır](#BKMK_Run_tests_after_every_build)

 Test projesi oluşturduğunuzda, testler Test Gezgini'nde görünür. Test Gezgini görünür değilse, Visual Studio menüsünden **Test** ' i seçin, **Windows**' u ve ardından **Test Gezgini**' ni seçin.

 ![Birim test Gezgini](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

 Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, test Gezgini sonuçları **başarısız testler**, **başarılı**testler, **Atlanan** testler ve **çalıştırma**testleri için varsayılan gruplar halinde görüntüler. Test Gezgini'nin testlerinizi gruplandırma şeklini değiştirebilirsiniz.

 Test Gezgini araç çubuğundan testleri bulma, düzenleme ve çalıştırma işinin çoğunu yapabilirsiniz.

 ![Testleri test Gezgini araç çubuğundan Çalıştır](../test/media/ute-toolbar.png "UTE_ToolBar")

 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

### <a name="BKMK_Run_tests"></a>Testleri Çalıştır
 Tüm testler, Çözümdeki tüm testleri bir grup veya seçtiğiniz test kümesini çalıştırabilirsiniz. Aşağıdakilerden birini yapın:

- Bir Çözümdeki tüm testleri çalıştırmak için **Tümünü Çalıştır**' ı seçin.

- Varsayılan bir gruptaki tüm testleri çalıştırmak için **Çalıştır...** öğesini seçin ve ardından menüdeki grubu seçin.

- Çalıştırmak istediğiniz bireysel testleri seçin, seçili bir test için bağlam menüsünü açın ve ardından **Seçili Testleri Çalıştır**' ı seçin.

- Bireysel testlerin herhangi bir sırada çalıştırılmasını engelleyen bir bağımlılığı yoksa, araç çubuğundaki ![Ute&#95;paralellicon&#45;küçük](../test/media/ute-parallelicon-small.png "UTE_parallelicon-küçük") geçiş düğmesi ile paralel test yürütmeyi etkinleştirin. Bu durum, tüm testleri çalıştırmak için geçen süre önemli ölçüde azaltabilir.

  Testler çalışırken Test Gezgini penceresinin en üstündeki geçer/başarısız çubuğunda animasyon görünür. Tüm testler başarılı ya da herhangi bir test başarısız olursa kırmızıya döner test çalışması kılavuzumuzun geçer/başarısız çubuğu yeşile döner.

  ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

### <a name="BKMK_Run_tests_after_every_build"></a>Her derlemeden sonra Testleri Çalıştır

> [!WARNING]
> Visual Studio Enterprise içinde her derleme desteklendikten sonra birim testlerini çalıştırma.

|||
|-|-|
|![Derlemeden sonra Çalıştır](../test/media/ute-runafterbuild-btn.png "UTE_RunAfterBuild_btn")|Her yerel derlemeden sonra birim testlerinizi çalıştırmak için standart menüdeki **Test** ' i seçin ve ardından Test Gezgini araç çubuğunda **derlemeden sonra Testleri Çalıştır** ' ı seçin.|

 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="BKMK_View_test_results"></a>Test sonuçlarını görüntüle
 [Test ayrıntılarını](#BKMK_View_test_details) **&#124;** görüntüleme [test yönteminin kaynak kodunu görüntüleme](#BKMK_View_the_source_code_of_a_test_method)

 Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, test Gezgini sonuçları **başarısız testler**, **başarılı**testler, **Atlanan testler** ve **çalıştırma testleri**gruplarında görüntüler. Test Gezgini görüntüler altındaki ayrıntılar bölmesi test özeti çalıştırın.

### <a name="BKMK_View_test_details"></a>Test ayrıntılarını görüntüle
 Tek bir testin ayrıntılarını görüntülemek için testi seçin.

 ![Test yürütme ayrıntıları](../test/media/ute-testdetails.png "UTE_TestDetails")

 Test ayrıntıları bölmesinde aşağıdaki bilgileri görüntüler:

- Kaynak dosya adı ve test yönteminin satır sayısı.

- Testin durumu.

- Test yöntemini çalıştırmak için geçen geçen süre.

  Test başarısız olursa, Ayrıntılar bölmesinde de görüntüler:

- Test için birim test çerçevesi tarafından döndürülen ileti.

- Yığın izleme zaman test başarısız oldu.

  ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

### <a name="BKMK_View_the_source_code_of_a_test_method"></a>Test yönteminin kaynak kodunu görüntüleme
 Visual Studio düzenleyicisinde bir test yönteminin kaynak kodunu göstermek için, testi seçin ve bağlam menüsünde **testi aç** ' ı seçin (klavye: F12).

 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="BKMK_Group_and_filter_the_test_list"></a>Test listesini gruplandırma ve filtreleme
 [Test](#BKMK_Grouping_the_test_list) **&#124;** listesi [grubunu nitelikler](#BKMK_Group_by_traits) **&#124;** ile gruplandırma [ve test listesini filtreleme](#BKMK_Search_and_filter_the_test_list)

 Test Gezgini, testlerinizi önceden tanımlanmış kategoriler halinde gruplandırmanızı sağlar. Test Gezgini 'nde çalışan çoğu birim testi çerçevesi, testlerinizi gruplandırmak için kendi kategorilerinizi ve kategori/değer çiftlerini tanımlamanızı sağlar. Test özelliklerine karşılık dizeleri eşleştirerek, testlerin listesini de filtreleyebilirsiniz.

### <a name="BKMK_Grouping_the_test_list"></a>Test listesini gruplandırma
 Testlerin düzenlenme şeklini değiştirmek için **Gruplandırma ölçütü** düğme ![Test Gezgini grubu düğmesinin](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn") yanındaki aşağı oku seçin ve yeni bir gruplandırma ölçütü seçin.

 ![Test Gezgini 'nde kategoriye göre grup testleri](../test/media/ute-groupbycategory.png "UTE_GroupByCategory")

### <a name="test-explorer-groups"></a>Test Gezgini grupları

|Grup|Açıklama|
|-----------|-----------------|
|**Sürenin**|Yürütme zamanına göre test grupları: **hızlı**, **Orta**ve **yavaş**.|
|**Sonucu**|Testleri yürütme sonuçlarına göre gruplandırır: **başarısız testler**, **Atlanan testler**, **başarılı testler**.|
|**Lerdir**|Tanımladığınız kategori/değer çiftlerine göre test grupları. Nitelik kategorilerini ve değerlerini belirten sözdizimi, birim test çerçevesi tarafından tanımlanır.|
|**Proje**|Projeler adına göre test grupları.|

 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

### <a name="BKMK_Group_by_traits"></a>Nitelikleri göre Gruplandır
 Bir nitelik genellikle kategori adı/değer çiftidir, ancak tek bir kategori de olabilir. Nitelikler, birim test çerçevesi tarafından test yöntemi olarak tanımlanan yöntemlere atanabilir. Bir birim test çerçevesi, nitelik kategorilerini tanımlayabilir. Kendi Kategori ad/değer çiftlerinizi tanımlamak için nitelik kategorilerine değerler ekleyebilirsiniz. Nitelik kategorilerini ve değerlerini belirten sözdizimi, birim test çerçevesi tarafından tanımlanır.

 **Yönetilen kod için Microsoft birim testi çerçevesindeki nitelikler**

 Yönetilen uygulamalar için Microsoft birim testi çerçevesinde, bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> özniteliğinde bir nitelik ad/değer çifti tanımlarsınız. Test çerçevesi aşağıdaki önceden tanımlı nitelikleri de içerir:

|Nitelik|Açıklama|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Sahip kategorisi, birim test çerçevesi tarafından tanımlanır ve sahibin dize değerini sağlamanızı gerektirir.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Öncelik kategorisi, birim test çerçevesi tarafından tanımlanır ve öncelik için bir tamsayı değeri sağlamanızı gerektirir.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|TestCategory özniteliği değer olmadan bir kategori sağlamanıza olanak sağlar. TestCategory özniteliği tarafından tanımlanan bir kategori de bir TestProperty özniteliği kategorisi olabilir.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|TestProperty özniteliği nitelik kategori/değer çiftini tanımlamanızı sağlar.|

 **İçin Microsoft birim testi çerçevesindeki niteliklerC++**

 Bir nitelik tanımlamak için `TEST_METHOD_ATTRIBUTE` makrosunu kullanın. Örneğin, `TEST_MY_TRAIT`adlı bir nitelik tanımlamak için:

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

 Tanımlanan niteliği birim testlerinizde kullanmak için:

```
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>C++ ayırt edici öznitelik makroları

|Makrosu|Açıklama|
|-----------|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Ayırt edici nitelik tanımlamak için test_method_attrıbute makrosunu kullanın.|
|`TEST_OWNER(ownerAlias)`|Test yönteminin sahibini belirtmek için önceden tanımlanmış sahip ayırt edici niteliğini kullanın.|
|`TEST_PRIORITY(priority)`|Test yöntemlerinize göreli öncelikler atamak için önceden tanımlanmış öncelik ayırt edici niteliğini kullanın.|

 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

### <a name="BKMK_Search_and_filter_the_test_list"></a>Test listesini arama ve filtreleme
 Test Gezgini filtrelerini, görüntülediğiniz ve çalıştırdığınız projelerinizde test yöntemlerini sınırlandırmak için kullanabilirsiniz.

 Test Gezgini arama kutusuna bir dize yazdığınızda ve ENTER ' u seçtiğinizde, test listesi yalnızca tam adları dizeyi içeren testleri görüntüleyecek şekilde filtrelenir.

 Farklı ölçütlere göre filtrelemek için:

1. Arama kutusunun sağındaki açılan listeyi açın.

2. Yeni bir ölçüt seçin.

3. Tırnak işaretleri arasında filtre değeri girin.

   ![Test Gezgini 'nde testleri filtrele](../test/media/ute-filtertestlist.png "UTE_FilterTestList")

> [!NOTE]
> Aramalar büyük/küçük harfe duyarlıdır ve belirtilen dizeyle ölçüt değerinin herhangi bir bölümüyle eşleşir.

|Leyicisini|Açıklama|
|---------------|-----------------|
|**Nitelik**|Hem nitelik kategorisini hem de eşleşme değerlerini arar. Nitelik kategorilerini ve değerlerini belirten sözdizimi, birim test çerçevesi tarafından tanımlanır.|
|**Proje**|Test projesi adlarını eşleşmeler için arar.|
|**Hata Iletisi**|Eşleşmeler için başarısız Onaylamalar tarafından döndürülen Kullanıcı tanımlı hata iletilerini arar.|
|**Dosya yolu**|Test kaynak dosyalarının tam dosya adını eşleşmeler için arar.|
|**Tam nitelikli ad**|Test ad alanlarının, sınıfların ve yöntemlerin tam dosya adını eşleşmeler için arar.|
|**Output**|Standart çıkış (STDOUT) veya standart hata (stderr) ile yazılan Kullanıcı tanımlı hata iletilerini arar. Çıkış mesajlarını belirten sözdizimi, birim test çerçevesi tarafından tanımlanır.|
|**Sonucu**|Test Gezgini kategori adlarını eşleşmeler için arar: **başarısız testler**, **Atlanan testler**, **başarılı testler**.|

 Bir filtrenin sonuçlarının bir alt kümesini dışlamak için aşağıdaki sözdizimini kullanın:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

 Örneğin,

```
FullName:"MyClass" - FullName:"PerfTest"
```

 adında "PerfTest" da dahil olan testler hariç, adında "MyClass" içeren tüm testleri döndürür.

 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="BKMK_Create_custom_playlists"></a>Özel çalma listeleri oluşturma
 Çalıştırmak veya bir grup olarak görüntülemek istediğiniz testlerin listesini oluşturabilir ve kaydedebilirsiniz. Bir çalma listesi seçtiğinizde, listedeki testler test Gezgini ' nde görüntülenir. Birden fazla çalma listesine bir test ekleyebilirsiniz ve varsayılan **Tüm testler** çalma listesini seçtiğinizde projenizdeki tüm testler kullanılabilir.

 ![Bir çalma listesi seçin](../test/media/ute-playlist.png "UTE_Playlist")

 **Bir çalma listesi oluşturmak için**, test Gezgini 'nde bir veya daha fazla test seçin. Bağlam menüsünde, **çalma listesine ekle**, **NewPlaylist**' ı seçin. Dosyayı **Yeni çalma listesi oluştur** iletişim kutusunda belirttiğiniz ad ve konuma kaydedin.

 **Bir çalma listesine test eklemek için**, test Gezgini 'nde bir veya daha fazla test seçin. Bağlam menüsünde, **çalma listesine ekle**' yi seçin ve ardından testleri eklemek istediğiniz çalma listesini seçin.

 **Bir çalma listesi açmak için**, Visual Studio menüsünden test, çalma listesi ' ni seçin ve son kullanılan çalma listeleri listesinden seçin ya da çalma listesini aç ' ı seçerek şarkı listesinin adını ve konumunu belirtin.

 Bireysel testlerin herhangi bir sırada çalıştırılmasını engelleyen bir bağımlılığı yoksa, araç çubuğundaki ![Ute&#95;paralellicon&#45;küçük](../test/media/ute-parallelicon-small.png "UTE_parallelicon-küçük") geçiş düğmesi ile paralel test yürütmeyi etkinleştirin. Bu durum, tüm testleri çalıştırmak için geçen süre önemli ölçüde azaltabilir.

 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="BKMK_Debug_and_analyze_unit_tests"></a>Hata ayıklama ve birim testlerini analiz etme
 [Birim testlerinde](#BKMK_Debug_unit_tests) **&#124;** hata ayıklama [test yöntemi performans sorunlarını](#BKMK_Diagnose_test_method_performance_issues) **&#124;** tanılama [birim testi kod kapsamını analiz etme](#BKMK_Analyzeunit_test_code_coverage)

### <a name="BKMK_Debug_unit_tests"></a>Birim testlerinde hata ayıkla
 Test Gezgini, testleriniz için hata ayıklama oturumu başlatmak için kullanabilirsiniz. Kodunuzu Visual Studio hata ayıklayıcısı ile sorunsuz bir şekilde Adımlama, İleri ve geri birim testleri ve test altındaki projeye arasında sürer. Hata ayıklamayı başlatmak için:

1. Visual Studio düzenleyicisinde, hatalarını ayıklamak istediğiniz bir veya daha fazla test yöntemlerinde kesme noktası ayarlayın.

   > [!NOTE]
   > Test yöntemleri herhangi bir sırada çalışabileceğinden, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktalarını ayarlayın.

2. Test Gezgini ' nde, test yöntemlerini seçin ve bağlam menüsünde **Seçili testlerin hatalarını ayıkla** ' yı seçin.

   Hata ayıklayıcı hakkında daha fazla bilgi için bkz. [Visual Studio 'Da hata ayıklama](../debugger/debugging-in-visual-studio.md).

   ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

### <a name="BKMK_Diagnose_test_method_performance_issues"></a>Test yöntemi performans sorunlarını tanılama
 Test yönteminin neden çok fazla sürdüğünü tanılamak için test Gezgini 'nde yöntemi seçin ve bağlam menüsünde profil ' i seçin. Bkz. [Performans Gezgini](../profiling/performance-explorer.md).

### <a name="BKMK_Analyzeunit_test_code_coverage"></a>Birim testi kod kapsamını analiz etme

> [!NOTE]
> Birim testi kod kapsamı yalnızca Visual Studio Enterprise kullanılabilir.

 Visual Studio kod kapsamı aracını kullanarak, gerçekten birim testleriniz tarafından test edilen ürün kodunuzun miktarını belirleyebilirsiniz. Kod kapsamı Seçili testler ya da bir çözümdeki tüm testleri çalıştırabilirsiniz.

 Bir çözümde test yöntemleri için kod kapsamını çalıştırmak için:

1. Visual Studio menüsünde **testler** ' i seçin ve ardından **kod kapsamını çözümle**' yi seçin.

2. Alt menüden aşağıdaki komutlardan birini seçin:

   - **Seçili testler** , test Gezgini 'nde seçtiğiniz test yöntemlerini çalıştırır.

   - **Tüm testler** Çözümdeki tüm test yöntemlerini çalıştırır.

   Kod kapsamı sonuçları penceresi, satır, işlev, sınıf, ad alanı ve modül tarafından uygulanan ürün kodu bloklarının yüzdesini görüntüler.

   Daha fazla bilgi için bkz. kod [kapsamını kullanarak ne kadar kodun test edildiğini belirleme](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

   ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön

## <a name="BKMK_External_resources"></a>Dış kaynaklar

### <a name="BKMK_Guidance"></a>Kılavuzu
 [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 2: birim testi: Içini test etme](https://go.microsoft.com/fwlink/?LinkID=255188)

## <a name="see-also"></a>Ayrıca Bkz.
 [Birim testi kodunuz](../test/unit-test-your-code.md) [64 bitlik bir işlem olarak birim testi çalıştırma](../test/run-a-unit-test-as-a-64-bit-process.md)
