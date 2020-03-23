---
title: Test Gezgini ile çalıştırma ve hata ayıklama birim testleri
description: Visual Studio'da Test Explorer ile testleri nasıl çalıştırlayacağınızı öğrenin. Bu konu, yapıdan sonra otomatik test çalıştırmalarını etkinleştirmeyi, test sonuçlarını görüntülemeyi, test listesini gruplandırmayı ve filtrelemeyi, çalma listeleri oluşturmayı, hata ayıklama testlerini nasıl kullanacağını ve test kısayollarını nasıl kullanacağını kapsar.
ms.date: 07/29/2019
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b183c1939ed48351bc15dacff31c85af46286ad
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77278521"
---
# <a name="run-unit-tests-with-test-explorer"></a>Test Gezgini ile birim testleri çalıştırma

Visual Studio veya üçüncü taraf birim test projelerinden birim testleri çalıştırmak için Test Gezgini'ni kullanın. Testleri kategorilere ayırmak, test listesine filtre uygulama ve test çalma listeleri oluşturmak, kaydetmek ve çalıştırmak için Test Gezgini'ni de kullanabilirsiniz. Testleri hata ayıklayabilir ve test performansını ve kod kapsamını analiz edebilirsiniz.

Visual Studio, hem yönetilen hem de yerel kod için Microsoft birim sınayı çerçevelerini içerir. Ancak, Test Gezgini, Test Gezgini bağdaştırıcısı uygulamış herhangi bir birim test çerçevesi de çalıştırabilir. Üçüncü taraf birim test çerçevelerinin yüklenmesi hakkında daha fazla bilgi [için](../test/install-third-party-unit-test-frameworks.md) bkz.

**Test Gezgini,** bir çözümde birden çok test projesinden ve üretim kodu projelerinin bir parçası olan test sınıflarından testler çalıştırabilir. Test projeleri farklı birim test çerçeveleri kullanabilir. Test altındaki kod .NET için yazıldığında, test projesi hedef kodun dilinden bağımsız olarak .NET'i de hedefleyen herhangi bir dilde yazılabilir. Yerel C/C++ kod projeleri C++ birim test çerçevesi kullanılarak sınanmalıdır. Daha fazla bilgi için [C/C++ için birim testleri yaz'a](writing-unit-tests-for-c-cpp.md)bakın.

## <a name="run-tests-in-test-explorer"></a>Test Gezgini'nde testleri çalıştırma


Test projesini oluşturduğunuzda, testler Test Gezgini'nde görünür. Test Gezgini görünmüyorsa, Visual Studio menüsünde **Test'i** seçin, **Windows'u**seçin ve ardından **Test Gezgini'ni**seçin.


::: moniker range="vs-2017"
![Ünite Test Explorer](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test Gezgini](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Test Lerinizi çalıştırdığınızda, yazdıkça ve yeniden çalıştırırken, Test Gezgini sonuçları **Başarısız Testler**, Geçti **Testleri,** **Atlanan** testler ve **Çalıştırmama testlerinden**oluşan varsayılan gruplarhalinde görüntüler. Test Gezgini'nin testlerinizi gruplaştırış şeklini değiştirebilirsiniz.
::: moniker-end
::: moniker range=">=vs-2019"
Test Gezgini, testlerinizi çalıştırDığınızda, yazdıkça ve yeniden yazdıkça, sonuçları **Project,** **Namespace**ve **Class'ın**varsayılan gruplandırmasında görüntüler. Test Gezgini'nin testlerinizi gruplaştırış şeklini değiştirebilirsiniz.
::: moniker-end

**Test Gezgini** araç çubuğundan testleri bulma, düzenleme ve çalıştırma çalışmalarının çoğunu gerçekleştirebilirsiniz.

::: moniker range="vs-2017"
![Test Gezgini araç çubuğundan testleri çalıştırma](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test Gezgini araç çubuğundan testleri çalıştırma](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

### <a name="run-tests"></a>Testleri çalıştırma

::: moniker range="vs-2017"
Çözümdeki tüm testleri, bir gruptaki tüm testleri veya seçtiğiniz bir dizi testi çalıştırabilirsiniz. Aşağıdakilerden birini yapın:

- Tüm testleri bir çözümde çalıştırmak için **Tümlerini Çalıştır'ı**seçin.

- Varsayılan bir gruptatüm testleri çalıştırmak için **Çalıştır'ı** seçin ve ardından menüdeki grubu seçin.

- Çalıştırmak istediğiniz tek tek testleri seçin, seçili bir test için sağ tıklama menüsünü açın ve ardından **Seçili Testleri Çalıştır'ı**seçin.

- Tek tek testlerin herhangi bir sırada çalıştırılmalarını engelleyen bağımlılıkları yoksa, ![UTE&#95;parallelicon küçük&#45;](../test/media/ute_parallelicon-small.png) araç çubuğundaki geçiş düğmesini titretin. Bu, tüm testleri çalıştırmak için geçen süreyi belirgin bir şekilde azaltabilir.

**Test Gezgini** penceresinin üst kısmındaki **geçiş/başarısız çubuğu,** testler çalıştırılırken animasyonlur. Test çalışmasının sonunda, tüm testler geçerse veya herhangi bir test başarısız olursa **pas/başarısız çubuğu** yeşile döner.
::: moniker-end
::: moniker range=">=vs-2019"
Çözümdeki tüm testleri, bir gruptaki tüm testleri veya seçtiğiniz bir dizi testi çalıştırabilirsiniz. Aşağıdakilerden birini yapın:

- Tüm testleri bir çözümde çalıştırmak için **Tümlerini Çalıştır** simgesini seçin.

- Varsayılan bir grupta tüm testleri çalıştırmak için **Çalıştır** simgesini seçin ve ardından menüdeki grubu seçin.

- Çalıştırmak istediğiniz tek tek testleri seçin, seçili bir test için sağ tıklama menüsünü açın ve ardından **Seçili Testleri Çalıştır'ı**seçin.

- Tek tek testlerin herhangi bir sırada çalıştırılmalarını engelleyen bağımlılıkları yoksa, araç çubuğunun ayarlar menüsünde paralel test yürütmesini açın. Bu, tüm testleri çalıştırmak için geçen süreyi belirgin bir şekilde azaltabilir.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Her yapıdan sonra testleri çalıştırma
::: moniker range="vs-2017"
|Düğme|Açıklama|
|-|-|
|![Yapıdan sonra çalıştırın](../test/media/ute_runafterbuild_btn.png)|Birim testlerinizi her yerel yapıdan sonra çalıştırmak için standart menüde **Test et'i** seçin ve ardından **Test Gezgini** araç çubuğunda **Yap'tan sonra Testleri Çalıştır'ı** seçin.|

> [!NOTE]
> Her yapıdan sonra birim testleri çalıştırmak için Visual Studio 2017 Enterprise veya Visual Studio 2019 gerekmektedir. Visual Studio 2019'da Topluluk ve Profesyonel'in yanı sıra Enterprise'da da yer almaktadır.
::: moniker-end
::: moniker range=">=vs-2019"
Birim testlerinizi her yerel yapıdan sonra çalıştırmak için, Test Gezgini araç çubuğundaki ayarlar simgesini açın ve **Yapıdan Sonra Testleri Çalıştır'ı**seçin.
::: moniker-end

## <a name="view-test-results"></a>Test sonuçlarını görüntüleme

Test Gezgini, testlerinizi çalıştırırken, yazdıkça ve yeniden çalıştırdırken, Test Gezgini sonuçları Başarısız Testler , **Geçti Testleri,** **Failed Tests** **Atlanan Testler** ve **Çalıştırmama**Testlerinden oluşan gruplar halinde görüntüler. Test Gezgini'nin alt veya yan tarafındaki ayrıntılar bölmesi test çalışmasının bir özetini görüntüler.

### <a name="view-test-details"></a>Test ayrıntılarını görüntüleme

Tek bir testin ayrıntılarını görüntülemek için testi seçin.

::: moniker range="vs-2017"
![Test yürütme ayrıntıları](../test/media/ute_testdetails.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test yürütme ayrıntıları](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end

Test ayrıntıları bölmesi aşağıdaki bilgileri görüntüler:

- Kaynak dosya adı ve test yönteminin satır numarası.

- Testin durumu.

- Test yönteminin çalıştırmak için aldığı geçen süre.

Test başarısız olursa, ayrıntılar bölmesi de görüntüler:

- İleti, test için birim test çerçevesi tarafından döndürülür.

- Test başarısız olduğu anda yığın izi.

### <a name="view-the-source-code-of-a-test-method"></a>Test yönteminin kaynak kodunu görüntüleme

Visual Studio düzenleyicisinde bir test yönteminin kaynak kodunu görüntülemek için testi seçin ve ardından sağ tıklama menüsünde **Testi Aç'ı** seçin (Klavye: **F12).**

## <a name="group-and-filter-the-test-list"></a>Test listesini grupla ve filtrele

Test Gezgini, testlerinizi önceden tanımlanmış kategorilere ayırmanızı sağlar. Test Gezgini'nde çalışan çoğu birim test çerçevesi, testlerinizi gruplandırmak için kendi kategorilerinizi ve kategori/değer çiftlerinizi tanımlamanıza izin verebiliyor. Dizeleri test özellikleriyle eşleştirerek test listesini de filtreleyebilirsiniz.

### <a name="group-tests-in-the-test-list"></a>Test listesindeki testleri gruplandırma

::: moniker range="vs-2017"
Testlerin düzenlenme şeklini değiştirmek için, **Grup By** düğmesi ![Test Gezgini](../test/media/ute_groupby_btn.png) grup düğmesinin yanındaki aşağı oku seçin ve yeni bir gruplandırma ölçütleri seçin.

![Test Gezgini'nde kategoriye göre testleri gruplandırma](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
Test Gezgini, testlerinizi bir hiyerarşi içinde gruplandırmanızı sağlar. Varsayılan hiyerarşi gruplandırma **Sı,** **Ad Alanı**ve ardından **Sınıf**' dur. Testlerin düzenlenme şeklini değiştirmek için **Grup** By ![düğmesi Test](../test/media/ute_groupby_btn.png) Gezgini grup düğmesini seçin ve yeni bir gruplandırma ölçütleri seçin.

![Test Gezgini'nde kategoriye göre testleri gruplandırma](../test/media/vs-2019/test-explorer-groupby-162.png)

Tercih ettiğiniz sırada Grup A.Ş seçeneklerini seçerek kendi hiyerarşi ve grup düzeylerinizi **Duruma** göre ve ardından **Sınıfa** göre tanımlayabilirsiniz.

![Duruma göre gruplandırma ve ardından Sınıf](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Test Gezgini grupları

::: moniker range="vs-2017"
|Grup|Açıklama|
|-|-----------------|
|**Süre**|Yürütme süresine göre gruplar test: **Hızlı**, **Orta**, ve **Yavaş**.|
|**Sonuç**|Yürütme sonuçlarına göre testleri gruplandırın: **Başarısız Testler**, **Atlanan Testler**, Geçti **Testleri**.|
|**Özellik**|Tanımladığınız kategori/değer çiftleri tarafından test gruplat. Özellik kategorilerini ve değerlerini belirtmek için sözdizimi birim test çerçevesi tarafından tanımlanır.|
|**Proje**|Gruplar projelerin adına göre test.|
::: moniker-end
::: moniker range=">=vs-2019"
|Grup|Açıklama|
|-|-----------------|
|**Süre**|Yürütme süresine göre gruplar testleri: **Hızlı,** **Orta**ve **Yavaş**.|
|**Durum**|Yürütme sonuçlarına göre testleri gruplandırın: **Başarısız Testler**, **Atlanan Testler**, Geçti **Testleri**, **Çalıştırılmadı**|
|**Hedef Çerçeve** | Testleri projelerinin hedefi olan çerçeveye göre grupla |
|**Namespace**|Testleri içeren ad alanına göre gruplatır.|
|**Proje**|Testleri içeren projeye göre gruplatır.|
|**Sınıf**|Testleri içeren sınıfa göre grupla.|
::: moniker-end

### <a name="traits"></a>Özellik

Özellik genellikle bir kategori adı/değer çiftidir, ancak tek bir kategori de olabilir. Özellikler, birim test çerçevesi tarafından bir test yöntemi olarak tanımlanan yöntemlere atanabilir. Birim test çerçevesi özellik kategorilerini tanımlayabilir. Kendi kategori adınızı/değer çiftlerinizi tanımlamak için özellik kategorilerine değerler ekleyebilirsiniz. Özellik kategorilerini ve değerlerini belirtmek için sözdizimi birim test çerçevesi tarafından tanımlanır.

**Yönetilen Kod için Microsoft Birimi Test Çerçevesi'ndeki özellikler**

Yönetilen uygulamalar için Microsoft birim test çerçevesinde, bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> öznitelikte bir özellik adı/ değer çifti tanımlarsınız. Test çerçevesi aynı zamanda bu önceden tanımlanmış özellikleri de içerir:

|Özellik|Açıklama|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Sahip kategorisi birim test çerçevesi tarafından tanımlanır ve sahibinin bir dize değeri sağlamanızı gerektirir.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Öncelik kategorisi birim test çerçevesi tarafından tanımlanır ve önceliğin tamsayı değerini sağlamanızı gerektirir.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|TestKategorisi özniteliği, değeri olmayan bir kategori sağlamanıza olanak tanır.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|TestProperty özniteliği, özellik kategorisi/değer çiftini tanımlamanızı sağlar.|


**C++ için Microsoft Birim Test Çerçevesi'ndeki özellikler**

[C++ için Microsoft Birimi Test Çerçevesi'ni nasıl kullanacağız](how-to-use-microsoft-test-framework-for-cpp.md)bkz.

## <a name="create-custom-playlists"></a>Özel çalma listeleri oluşturma

::: moniker range="vs-2017"
Çalıştırmak veya grup olarak görüntülemek istediğiniz testlerin listesini oluşturabilir ve kaydedebilirsiniz. Bir çalma listesi seçtiğinizde, listedeki testler Test Gezgini'nde görüntülenir. Birden fazla çalma listesine bir test ekleyebilirsiniz ve varsayılan **Tüm Testler** çalma listesini seçtiğinizde projenizdeki tüm testler kullanılabilir.

![Çalma listesi seçin](../test/media/ute_playlist.png)

**Bir çalma listesi oluşturmak için**Test Gezgini'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde, **Çalma Listesi** > **Yeni Oynatma Listesine**Ekle'yi seçin. **Dosyayı Yeni Çalma Listesi Oluştur** iletişim kutusunda belirttiğiniz ad ve konuma kaydedin.

**Bir çalma listesine test eklemek için**Test Gezgini'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde, **Oynatma Listesine Ekle'yi**seçin ve ardından testleri eklemek istediğiniz çalma listesini seçin.

**Bir çalma listesi açmak için**Visual Studio menüsünden **Test** > **Çalma Listesi'ni** seçin ve en son kullanılan çalma listeleri listesinden seçim yapın veya çalma listesinin adını ve konumunu belirtmek için Açık **Çalma Listesi'ni** seçin.

Tek tek testlerin herhangi bir sırada çalıştırılmalarını engelleyen bağımlılıkları yoksa, ![UTE&#95;parallelicon küçük&#45;](../test/media/ute_parallelicon-small.png) araç çubuğundaki geçiş düğmesini titretin. Bu, tüm testleri çalıştırmak için geçen süreyi belirgin bir şekilde azaltabilir.
::: moniker-end
::: moniker range=">=vs-2019"
Çalıştırmak veya grup olarak görüntülemek istediğiniz testlerin listesini oluşturabilir ve kaydedebilirsiniz. Bir çalma listesi seçtiğinizde, listedeki testler yeni bir Test Gezgini sekmesinde görüntülenir. Birden fazla çalma listesine test ekleyebilirsiniz.

**Bir çalma listesi oluşturmak için**Test Gezgini'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde, **Çalma Listesine** > Ekle**Yeni Çalma Listesi'ni**seçin.

![Çalma listesi oluşturma](../test/media/vs-2019/test-explorer-playlist-16-2.png)

Çalma listesi yeni bir Test Gezgini sekmesinde açılır. Bu çalma listesini bir kez kullanabilirsiniz ve sonra atabilirsiniz veya çalma listesi penceresinin araç çubuğundaki **Kaydet** düğmesini tıklatıp çalma listesini kaydetmek için bir ad ve konum seçebilirsiniz.

![Çalma listesi ayrı test gezgini sekmesinde açılır](../test/media/vs-2019/test-explorer-playlist-tab-16-2.png)

**Bir çalma listesi oluşturmak için**Test Gezgini'nde bir veya daha fazla test seçin. Sağ tıklayın ve **Playlist** > Yeni**çalma listesine**ekle seçin.

**Bir çalma listesi açmak için**Visual Studio araç çubuğundaki çalma listesi simgesini seçin ve menüden daha önce kaydedilmiş bir çalma listesi dosyasını seçin.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="test-explorer-columns"></a>Test Explorer sütunları

[Gruplar,](#test-explorer-groups) Özellik, Yığın İzleme, Hata İletisi ve Tam Nitelikli Ad ile birlikte Test Gezgini'nde sütun olarak da kullanılabilir. Çoğu sütun varsayılan olarak görünmez ve hangi sütunları gördüğünüze ve göründükleri sırayı özelleştirebilirsiniz.

![Duruma göre gruplandırma ve ardından Sınıf](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Test sütunlarını filtreleme, sıralama ve yeniden düzenleme

Sütunlar filtrelenebilir, sıralanabilir ve yeniden düzenlenebilir.
* Belirli özelliklere filtre sağlamak için Özellikler sütununun üst kısmındaki filtre simgesini tıklatın.

  ![Sütun filtresi](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* Sütunların sırasını değiştirmek için, bir sütun üstbilgisini tıklatın ve sola veya sağa sürükleyin.

* Bir sütunu sıralamak için sütun üstbilgisini tıklatın. Her sütun sıralanamaz. **Ayrıca, Shift** tuşunu basılı tutarak ve ek bir sütun üstbilgisini tıklatarak ikinci bir sütuna göre sıralayabilirsiniz.

  ![Sütun sıralama](../test/media/vs-2019/test-explorer-sort-column-16-2.png)
::: moniker-end

## <a name="search-and-filter-the-test-list"></a>Test listesini arama ve filtreleme

Görüntülediğiniz ve çalıştırdığınız projelerinizdeki test yöntemlerini sınırlamak için Test Gezgini arama filtrelerini de kullanabilirsiniz.

**Test Gezgini** arama kutusuna bir dize yazdığınızda ve **Enter'u**seçtiğinizde, test listesi yalnızca tam nitelikli adları dizeyi içeren testleri görüntülemek için filtrelenir.

Farklı bir ölçüte göre filtrelemek için:

1. Açılan listeyi arama kutusunun sağında açın.

2. Yeni bir ölçüt seçin.

3. Tırnak işaretleri arasındaki filtre değerini girin. İçeren bir eşleşme yerine dize üzerinde tam bir eşleşme aramak istiyorsanız, iki nokta üst üste (:)) yerine eşit ler işareti (=) kullanın.

::: moniker range="vs-2017"
![Test Gezgini'nde filtre testleri](../test/media/ute_filtertestlist.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test Gezgini'nde filtre testleri](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

> [!NOTE]
> Aramalar büyük/küçük harf duyarsızdır ve belirtilen dizeyle ölçüt değerinin herhangi bir bölümüyle eşleşir.

::: moniker range="vs-2017"
|Niteleyici|Açıklama|
|-|-----------------|
|**Özellik**|Eşleşmeler için hem özellik kategorisi hem de değeri arar. Özellik kategorilerini ve değerlerini belirtmek için sözdizimi birim test çerçevesi tarafından tanımlanır.|
|**Proje**|Eşleşmeler için test proje adlarını arar.|
|**Hata İletisi**|Eşleşmeler için başarısız asserts tarafından döndürülen kullanıcı tanımlı hata iletilerini arar.|
|**Dosya Yolu**|Eşleşmeler için test kaynağı dosyalarının tam nitelikli dosya adını arar.|
|**Tam Nitelikli Ad**|Test ad alanlarının, sınıfların ve eşleşmelerin yöntemlerinin tam nitelikli adını arar.|
|**Çıktı**|Standart çıktı (stdout) veya standart hata (stderr) için yazılmış kullanıcı tanımlı hata iletilerini arar. Çıktı iletilerini belirtmek için sözdizimi birim test çerçevesi tarafından tanımlanır.|
|**Sonuç**|Eşleşmeler için Test Gezgini kategori adlarını arar: **Başarısız Testler**, **Atlanan Testler**, Geçti **Testleri**.|
::: moniker-end
::: moniker range=">=vs-2019"
|Niteleyici|Açıklama|
|-|-----------------|
|**Durum**|Eşleşmeler için Test Gezgini kategori adlarını arar: **Başarısız Testler**, **Atlanan Testler**, Geçti **Testleri**.|
|**Özellik**|Eşleşmeler için hem özellik kategorisi hem de değeri arar. Özellik kategorilerini ve değerlerini belirtmek için sözdizimi birim test çerçevesi tarafından tanımlanır.|
|**Tam Nitelikli Ad**|Test ad alanlarının, sınıfların ve eşleşmelerin yöntemlerinin tam nitelikli adını arar.|
|**Proje**|Eşleşmeler için test proje adlarını arar.|
|**Hedef Çerçeve**|Eşleşmeler için Test Gezgini kategori adlarını arar: **Başarısız Testler**, **Atlanan Testler**, Geçti **Testleri**.|
|**Namespace**|Eşleşmeler için test ad alanlarını arar.|
|**Sınıf**|Eşleşmeler için test sınıfları adlarını arar.|
::: moniker-end

Filtre sonuçlarının bir alt kümesini hariç tutmak için aşağıdaki sözdizimini kullanın:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Örneğin, `FullName:"MyClass" - FullName:"PerfTest"` adlarında "PerfTest" de bulunan testler dışında, adlarında "MyClass" içeren tüm testleri döndürür.

## <a name="debug-and-analyze-unit-tests"></a>Hata ayıklama ve analiz ünitesi testleri

Test Gezgini'ni, testleriniz için hata ayıklama oturumu başlatmak için kullanabilirsiniz. Visual Studio hata ayıklayıcı ile kodunuzu sorunsuz bir şekilde gözden geçirmek, ünite testleri ile test altındaki proje arasında ileri geri götürmenizi ister. Hata ayıklamaya başlamak için:

1. Visual Studio düzenleyicisinde, hata ayıklamak istediğiniz bir veya daha fazla test yönteminde bir kesme noktası ayarlayın.

    > [!NOTE]
    > Sınama yöntemleri herhangi bir sırada çalıştırılabildiği için, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktaları ayarlayın.

2. Test Gezgini'nde, test yöntemlerini seçin ve ardından sağ tıklama menüsünde **Hata Ayıklama Seçili Testler'i** seçin.

   Hata ayıklama hakkında daha fazla bilgi için [Visual Studio'da Hata Ayıklama bölümüne](../debugger/debugger-feature-tour.md)bakın.

### <a name="diagnose-test-method-performance-issues"></a>Test yöntemi performans sorunlarını tanıla

Bir test yönteminin neden çok fazla zaman aldığını anlamak için, Test Gezgini'nde yöntemi seçin ve ardından sağ tıklama menüsünde **Profil Seçili Test'i** seçin. Bkz. [Instrumentation profil oluşturma raporu.](../profiling/understanding-instrumentation-data-values.md?view=vs-2017)

### <a name="analyze-unit-test-code-coverage"></a>Birim test kodu kapsamını analiz et

Visual Studio Enterprise sürümünde bulunan Visual Studio kod kapsama aracını kullanarak birim testleriniz tarafından gerçekten test edilen ürün kodu miktarını belirleyebilirsiniz. Bir çözümde, seçili testlerde veya tüm testlerde kod kapsamı çalıştırabilirsiniz.

Çözümde test yöntemleri için kod kapsamı çalıştırmak için:

::: moniker range="vs-2017"

1. Üst menü çubuğunda **Test'i** seçin ve ardından **kod kapsamını analiz et'i**seçin.

2. Alt menüden aşağıdaki komutlardan birini seçin:

    - **Seçili testler,** Test Gezgini'nde seçtiğiniz test yöntemlerini çalıştırın.

    - **Tüm testler** çözümdeki tüm test yöntemlerini çalıştırZ.

::: moniker-end

::: moniker range=">=vs-2019"

* Test Gezgini'nde sağ tıklatın ve **Seçili testler için Kod Kapsamını Analiz'i** seçin

::: moniker-end

**Kod Kapsamı Sonuçları** penceresi, satır, işlev, sınıf, ad alanı ve modül tarafından yapılan ürün kodu bloklarının yüzdesini görüntüler.

Daha fazla bilgi için [bkz.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

## <a name="test-shortcuts"></a>Kısayolları test edin

Testler, testteki kod düzenleyicisi'ne sağ tıklayarak ve **Testi Çalıştır'ı** seçerek veya Visual Studio'daki varsayılan [Test Gezgini kısayollarını](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) kullanarak Test Gezgini'nden çalıştırılabilir. Kısayollardan bazıları bağlam tabanlıdır. Bu, imlecin kod düzenleyicisinde nerede olduğuna bağlı olarak testleri çalıştırdıkları veya hata ayıklama yaptıkları anlamına gelir. İmleciniz bir test yönteminin içindeyse, bu test yöntemi çalışır. İmleciniz sınıf düzeyindeyse, o sınıftaki tüm testler çalıştırılır. Bu ad alanı düzeyi için de aynıdır.

|Sık Kullanılan Komutlar| Klavye Kısayolları|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**Ctrl**+**R**, **Ctrl**+**T**|
|TestExplorer.RunAllTestsInContext|**Ctrl**+**R**, **T**|
|TestExplorer.RunAllTests|**Ctrl**+**R**, **A**|
|TestExplorer.RepeatLastRun|**Ctrl**+**R**, **L**|

> [!NOTE]
> Testler yalnızca soyut sınıflarda tanımlandığı ve anlık olarak tanımlanmadığından, bir testi soyut bir sınıfta çalıştıramazsınız. Soyut sınıflarda testleri çalıştırmak için soyut sınıftan türeyen bir sınıf oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [Birim kodunuzu test edin](../test/unit-test-your-code.md)
- [64 bitlik bir işlem olarak birim testi çalıştırma](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Test Gezgini Hakkında SSS](test-explorer-faq.md)
