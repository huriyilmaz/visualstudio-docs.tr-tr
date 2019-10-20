---
title: Test Gezgini ile birim testlerini çalıştırma ve hata ayıklama
description: Visual Studio 'da test Gezgini ile testlerin nasıl çalıştırılacağını öğrenin. Bu konu, derleme sonrasında otomatik test çalıştırmalarını etkinleştirme, test sonuçlarını görüntüleme, test listesini gruplandırma ve filtreleme, çalma listeleri oluşturma, testleri hata ayıklama ve test kısayollarını kullanma konularını ele alır.
ms.date: 07/29/2019
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65c5d872462b4397078231eed2a9bec56131dec0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646639"
---
# <a name="run-unit-tests-with-test-explorer"></a>Test Gezgini ile birim testleri çalıştırma

Visual Studio 'dan veya üçüncü taraf birim testi projelerinden birim testlerini çalıştırmak için test Gezgini 'ni kullanın. Testleri kategoriler halinde gruplamak, test listesini filtrelemek ve testlerin çalma listelerini oluşturmak, kaydetmek ve çalıştırmak için test Gezgini ' ni de kullanabilirsiniz. Testlerde hata ayıklama yapabilir ve test performansını ve kod kapsamını çözümleyebilirsiniz.

Visual Studio hem yönetilen hem de yerel kod için Microsoft birim testi çerçeveleri içerir. Ancak, test Gezgini, test Gezgini bağdaştırıcısı uygulayan herhangi bir birim test çerçevesini de çalıştırabilir. Üçüncü taraf birim testi çerçevelerini yükleme hakkında daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçeveleri yükleme](../test/install-third-party-unit-test-frameworks.md)

**Test Gezgini** , bir çözümde ve üretim kodu projelerinin parçası olan test sınıflarından birden çok test projesinin testlerini çalıştırabilir. Test projeleri, farklı birim testi çerçeveleri kullanabilir. Test altındaki kod .NET için yazıldığında, hedef kodun dilinden bağımsız olarak, test projesi de .NET ' i hedefleyen herhangi bir dilde yazılabilir. Yerel C/C++ kod projelerinin bir C++ birim test çerçevesi kullanılarak test olması gerekir. Daha fazla bilgi için bkz. [C/C++Için birim testleri yazma](writing-unit-tests-for-c-cpp.md).

## <a name="run-tests-in-test-explorer"></a>Testleri test Gezgini 'nde Çalıştır


Test projesi oluşturduğunuzda, testler test Gezgini 'nde görünür. Test Gezgini görünür değilse, Visual Studio menüsünden **Test** ' i seçin, **Windows**' u ve ardından **Test Gezgini**' ni seçin.


::: moniker range="vs-2017"
![Birim test Gezgini](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test Gezgini](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, test Gezgini sonuçları **başarısız testler**, **başarılı**testler, **Atlanan** testler ve **çalıştırma**testleri için varsayılan gruplar halinde görüntüler. Test Gezgini 'nin testlerinizi gruplandırma yöntemini değiştirebilirsiniz.
::: moniker-end
::: moniker range=">=vs-2019"
Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, test Gezgini sonuçları varsayılan bir **Proje**, **ad alanı**ve **sınıf**gruplandırmasında görüntüler. Test Gezgini 'nin testlerinizi gruplandırma şeklini değiştirebilirsiniz.
::: moniker-end

**Test Gezgini** araç çubuğundan testleri bulma, düzenleme ve çalıştırma işinin çoğunu yapabilirsiniz.

::: moniker range="vs-2017"
![Testleri test Gezgini araç çubuğundan Çalıştır](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Testleri test Gezgini araç çubuğundan Çalıştır](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

### <a name="run-tests"></a>Testleri çalıştırma

::: moniker range="vs-2017"
Çözümdeki tüm testleri, bir gruptaki tüm testleri veya seçtiğiniz bir test kümesini çalıştırabilirsiniz. Aşağıdakilerden birini yapın:

- Bir Çözümdeki tüm testleri çalıştırmak için **Tümünü Çalıştır**' ı seçin.

- Varsayılan bir gruptaki tüm testleri çalıştırmak için **Çalıştır** ' ı seçin ve ardından menüdeki grubu seçin.

- Çalıştırmak istediğiniz bireysel testleri seçin, seçili bir test için sağ tıklama menüsünü açın ve ardından **Seçili Testleri Çalıştır**' ı seçin.

- Bireysel testlerin herhangi bir sırada çalıştırılmasını önleyen bir bağımlılığı yoksa, paralel test yürütme özelliğini ![UTE&#95;parallelicon&#45;küçük](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğme. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.

**Test Gezgini** penceresinin en üstündeki **geçiş/başarısızlık çubuğu** , testler çalışırken hareketlendirilir. Test çalıştırmasının sonunda, herhangi bir test başarısız olursa tüm testler başarılı veya Red durumunda, **geçiş/başarısızlık çubuğu** yeşile dönüşür.
::: moniker-end
::: moniker range=">=vs-2019"
Çözümdeki tüm testleri, bir gruptaki tüm testleri veya seçtiğiniz bir test kümesini çalıştırabilirsiniz. Aşağıdakilerden birini yapın:

- Bir Çözümdeki tüm testleri çalıştırmak için **Tümünü Çalıştır** simgesini seçin.

- Varsayılan bir gruptaki tüm testleri çalıştırmak için **Çalıştır** simgesini seçin ve sonra menüdeki grubu seçin.

- Çalıştırmak istediğiniz bireysel testleri seçin, seçili bir test için sağ tıklama menüsünü açın ve ardından **Seçili Testleri Çalıştır**' ı seçin.

- Bireysel testlerin herhangi bir sırada çalıştırılmasını engelleyen bir bağımlılığı yoksa, araç çubuğunun ayarlar menüsünde paralel test yürütme ' yi açın. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Her derlemeden sonra Testleri Çalıştır
::: moniker range="vs-2017"
|Düğme|Açıklama|
|-|-|
|![Derlemeden sonra Çalıştır](../test/media/ute_runafterbuild_btn.png)|Her yerel derlemeden sonra birim testlerinizi çalıştırmak için standart menüdeki **Test** ' i seçin ve ardından **Test Gezgini** araç çubuğunda **derlemeden sonra Testleri Çalıştır** ' ı seçin.|

> [!NOTE]
> Her derleme sonrasında birim testlerini çalıştırmak, Visual Studio 2017 Enterprise veya Visual Studio 2019 gerektirir. Visual Studio 2019 ' de Community ve Professional 'a ve Enterprise 'a dahildir.
::: moniker-end
::: moniker range=">=vs-2019"
Her yerel derlemeden sonra birim testlerinizi çalıştırmak için, test Gezgini araç çubuğunda Ayarlar simgesini açın ve **derlemeden sonra Testleri Çalıştır**' ı seçin.
::: moniker-end

## <a name="view-test-results"></a>Test sonuçlarını görüntüle

Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, test Gezgini sonuçları **başarısız testler**, **başarılı**testler, **Atlanan testler** ve **çalıştırma testleri**gruplarında görüntüler. Test Gezgini 'nin alt veya tarafındaki Ayrıntılar bölmesi, Test çalıştırmasının bir özetini görüntüler.

### <a name="view-test-details"></a>Test ayrıntılarını görüntüle

Tek bir testin ayrıntılarını görüntülemek için, testi seçin.

::: moniker range="vs-2017"
![Test yürütme ayrıntıları](../test/media/ute_testdetails.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test yürütme ayrıntıları](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end

Test ayrıntıları bölmesi aşağıdaki bilgileri görüntüler:

- Test yönteminin kaynak dosya adı ve satır numarası.

- Testin durumu.

- Test yönteminin çalışması için geçen geçen süre.

Test başarısız olursa, Ayrıntılar bölmesi şunları da görüntüler:

- Test için birim test çerçevesi tarafından döndürülen ileti.

- Testin başarısız olduğu zamanda yığın izlemesi.

### <a name="view-the-source-code-of-a-test-method"></a>Test yönteminin kaynak kodunu görüntüleme

Visual Studio düzenleyicisinde bir test yönteminin kaynak kodunu göstermek için, testi seçin ve sağ tıklama menüsünde **testi aç** ' ı seçin (klavye: **F12**).

## <a name="group-and-filter-the-test-list"></a>Test listesini gruplandırma ve filtreleme

Test Gezgini, testlerinizi önceden tanımlanmış kategoriler halinde gruplandırmanızı sağlar. Test Gezgini 'nde çalışan çoğu birim testi çerçevesi, testlerinizi gruplandırmak için kendi kategorilerinizi ve kategori/değer çiftlerini tanımlamanızı sağlar. Test özelliklerine karşılık dizeleri eşleştirerek, testlerin listesini de filtreleyebilirsiniz.

### <a name="group-tests-in-the-test-list"></a>Test listesindeki testleri gruplandırma

::: moniker range="vs-2017"
Testlerin düzenlenme şeklini değiştirmek için **Gruplandırma ölçütü** düğmesine ![Test gezgin grubu düğmesi ' nün yanındaki aşağı oku seçin ](../test/media/ute_groupby_btn.png) ve yeni bir gruplandırma ölçütü seçin.

![Test Gezgini 'nde kategoriye göre grup testleri](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
Test Gezgini, testlerinizi bir hiyerarşiye gruplandırmanıza olanak tanır. Varsayılan hiyerarşi gruplandırması **Proje**, **ad alanı**ve daha sonra **sınıftır**. Testlerin düzenlenme biçimini değiştirmek için, **grupla** düğmesine ![Test gezgin grubu düğmesini ](../test/media/ute_groupby_btn.png) ve yeni bir gruplandırma ölçütü seçin.

![Test Gezgini 'nde kategoriye göre grup testleri](../test/media/vs-2019/test-explorer-groupby-162.png)

Hiyerarşi ve gruplama düzeylerini **tanımlayabilir ve sonra** tercih ettiğiniz sırada grupla seçeneklerini belirleyerek **sınıfa** göre gruplandırabilirsiniz.

![Duruma göre Gruplandır ve sonra sınıfı](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Test Gezgini grupları

::: moniker range="vs-2017"
|Grup|Açıklama|
|-|-----------------|
|**Sürenin**|Yürütme zamanına göre test grupları: **hızlı**, **Orta**ve **yavaş**.|
|**Sonucu**|Testleri yürütme sonuçlarına göre gruplandırır: **başarısız testler**, **Atlanan testler**, **başarılı testler**.|
|**Lerdir**|Tanımladığınız kategori/değer çiftlerine göre test grupları. Nitelik kategorilerini ve değerlerini belirten sözdizimi, birim test çerçevesi tarafından tanımlanır.|
|**Proje**|Projeler adına göre test grupları.|
::: moniker-end
::: moniker range=">=vs-2019"
|Grup|Açıklama|
|-|-----------------|
|**Sürenin**|Testleri yürütme zamanına göre gruplandırır: **hızlı**, **Orta**ve **yavaş**.|
|**State**|Testleri yürütme sonuçlarına göre gruplandırır: **başarısız testler**, **Atlanan testler**, **başarılı testler**, **çalıştırılmadı**|
|**Hedef Çerçeve** | Testleri, projeleri hedeflerine göre gruplandırır |
|**Uzayına**|Testleri içerilen ad alanına göre gruplandırır.|
|**Proje**|Testleri içeren proje tarafından gruplandırır.|
|**Sınıfı**|Testleri içerilen sınıfa göre gruplandırır.|
::: moniker-end

### <a name="traits"></a>Lerdir

Bir nitelik genellikle kategori adı/değer çiftidir, ancak tek bir kategori de olabilir. Nitelikler, birim test çerçevesi tarafından test yöntemi olarak tanımlanan yöntemlere atanabilir. Bir birim test çerçevesi, nitelik kategorilerini tanımlayabilir. Kendi Kategori ad/değer çiftlerinizi tanımlamak için nitelik kategorilerine değerler ekleyebilirsiniz. Nitelik kategorilerini ve değerlerini belirten sözdizimi, birim test çerçevesi tarafından tanımlanır.

**Yönetilen kod için Microsoft birim testi çerçevesindeki nitelikler**

Yönetilen uygulamalar için Microsoft birim testi çerçevesinde, bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> özniteliğinde bir nitelik ad/değer çifti tanımlarsınız. Test çerçevesi aşağıdaki önceden tanımlı nitelikleri de içerir:

|Nitelik|Açıklama|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Sahip kategorisi, birim test çerçevesi tarafından tanımlanır ve sahibin dize değerini sağlamanızı gerektirir.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Öncelik kategorisi, birim test çerçevesi tarafından tanımlanır ve öncelik için bir tamsayı değeri sağlamanızı gerektirir.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|TestCategory özniteliği değer olmadan bir kategori sağlamanıza olanak sağlar.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|TestProperty özniteliği nitelik kategori/değer çiftini tanımlamanızı sağlar.|


**İçin Microsoft birim testi çerçevesindeki niteliklerC++**

[Için C++Microsoft birim testi çerçevesini kullanma ](how-to-use-microsoft-test-framework-for-cpp.md)konusuna bakın.

## <a name="create-custom-playlists"></a>Özel çalma listeleri oluşturma

::: moniker range="vs-2017"
Çalıştırmak veya bir grup olarak görüntülemek istediğiniz testlerin listesini oluşturabilir ve kaydedebilirsiniz. Bir çalma listesi seçtiğinizde, listedeki testler test Gezgini 'nde görüntülenir. Birden fazla çalma listesine bir test ekleyebilirsiniz ve varsayılan **Tüm testler** çalma listesini seçtiğinizde projenizdeki tüm testler kullanılabilir.

![Bir çalma listesi seçin](../test/media/ute_playlist.png)

**Bir çalma listesi oluşturmak için**, test Gezgini 'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde,**newplaylist** >  **Yapılacaklar listesine ekle** ' yi seçin. Dosyayı **Yeni çalma listesi oluştur** iletişim kutusunda belirttiğiniz ad ve konuma kaydedin.

**Bir çalma listesine test eklemek için**, test Gezgini 'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde, **çalma listesine ekle**' yi seçin ve ardından testleri eklemek istediğiniz çalma listesini seçin.

**Bir çalma listesi açmak için**, Visual Studio menüsünden **Test** > **çalma** listesi ' ni seçin ve son kullanılan çalma listeleri listesinden seçim yapın ya da çalma listesini **Aç** ' ı seçerek şarkı listesinin adını ve konumunu belirtin.

Bireysel testlerin herhangi bir sırada çalıştırılmasını önleyen bir bağımlılığı yoksa, paralel test yürütme özelliğini ![UTE&#95;parallelicon&#45;küçük](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğme. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.
::: moniker-end
::: moniker range=">=vs-2019"
Çalıştırmak veya bir grup olarak görüntülemek istediğiniz testlerin listesini oluşturabilir ve kaydedebilirsiniz. Bir çalma listesi seçtiğinizde, listedeki testler yeni bir test Gezgini sekmesinde görüntülenir. Birden fazla çalma listesine bir test ekleyebilirsiniz.

**Bir çalma listesi oluşturmak için**, test Gezgini 'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde,**Yeni çalma listesi** >  **çalma listesine ekle** ' yi seçin.

![Çalma listesi oluşturma](../test/media/vs-2019/test-explorer-playlist-16-2.png)

Yeni bir test Gezgini sekmesinde çalma listesi açılır. Bu çalma listesini bir kez kullanarak atabilir veya çalma listesi penceresinin araç çubuğunda **Kaydet** düğmesine tıklayabilir ve sonra da bir ad ve konum seçerek çalma listesini kaydedebilirsiniz.

![Çalma listesi ayrı test Gezgini sekmesinde açılıyor](../test/media/vs-2019/test-explorer-playlist-tab-16-2.png)

**Bir çalma listesi oluşturmak için**, test Gezgini 'nde bir veya daha fazla test seçin. Sağ tıklayın ve**Yeni çalma**listesi  >  **Yapılacaklar listesine ekle** ' yi seçin.

**Bir çalma listesi açmak için**, Visual Studio araç çubuğunda çalma listesi simgesini seçin ve menüden önceden kaydedilmiş bir çalma listesi dosyası seçin.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="test-explorer-columns"></a>Test Gezgini sütunları

[Gruplar](#test-explorer-groups) , test Gezgini 'nde nitelik, yığın Izleme, hata Iletisi ve tam ad gibi sütunlar olarak da kullanılabilir. Çoğu sütun varsayılan olarak görünmez ve gördüğünüz sütunları ve görünecekleri sırayı özelleştirebilirsiniz.

![Duruma göre Gruplandır ve sonra sınıfı](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Test sütunlarını filtreleme, sıralama ve yeniden düzenleme

Sütunlar filtrelenebilir, sıralanabilir ve yeniden düzenlenebilir.
* Belirli nitelikleri filtrelemek için nitelikler sütununun en üstündeki filtre simgesine tıklayın.

  ![Sütun filtresi](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* Sütunların sırasını değiştirmek için, bir sütun başlığına tıklayın ve sola veya sağa sürükleyin.

* Bir sütunu sıralamak için sütun başlığına tıklayın. Tüm sütunlar sıralanmayabilir. Ayrıca, **SHIFT** tuşunu basılı tutarak ve ek bir sütun başlığına tıklayarak ikincil bir sütuna göre sıralama yapabilirsiniz.

  ![Sütun sıralaması](../test/media/vs-2019/test-explorer-sort-column-16-2.png)
::: moniker-end

## <a name="search-and-filter-the-test-list"></a>Test listesini arama ve filtreleme

Ayrıca, görüntülediğiniz ve çalıştırdığınız projelerinizde test yöntemlerini sınırlandırmak için test Gezgini arama filtrelerini de kullanabilirsiniz.

**Test Gezgini** arama kutusuna bir dize yazdığınızda ve **ENTER**' u seçtiğinizde, test listesi yalnızca tam adları dizeyi içeren testleri görüntüleyecek şekilde filtrelenir.

Farklı ölçütlere göre filtrelemek için:

1. Arama kutusunun sağındaki açılan listeyi açın.

2. Yeni bir ölçüt seçin.

3. Tırnak işaretleri arasında filtre değeri girin. Dizeyi içeren bir eşleşme yerine tam eşleşme aramak istiyorsanız, iki nokta (:) yerine bir eşittir işareti (=) kullanın.

::: moniker range="vs-2017"
![Test Gezgini 'nde testleri filtrele](../test/media/ute_filtertestlist.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test Gezgini 'nde testleri filtrele](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

> [!NOTE]
> Aramalar büyük/küçük harfe duyarlıdır ve belirtilen dizeyle ölçüt değerinin herhangi bir bölümüyle eşleşir.

::: moniker range="vs-2017"
|Leyicisini|Açıklama|
|-|-----------------|
|**Nitelik**|Hem nitelik kategorisini hem de eşleşme değerlerini arar. Nitelik kategorilerini ve değerlerini belirten sözdizimi, birim test çerçevesi tarafından tanımlanır.|
|**Proje**|Test projesi adlarını eşleşmeler için arar.|
|**Hata Iletisi**|Eşleşmeler için başarısız Onaylamalar tarafından döndürülen Kullanıcı tanımlı hata iletilerini arar.|
|**Dosya yolu**|Test kaynak dosyalarının tam dosya adını eşleşmeler için arar.|
|**Tam nitelikli ad**|Test ad alanları, sınıflar ve yöntemlerin tam adını eşleşmeler için arar.|
|**Output**|Standart çıkış (STDOUT) veya standart hata (stderr) ile yazılan Kullanıcı tanımlı hata iletilerini arar. Çıkış mesajlarını belirten sözdizimi, birim test çerçevesi tarafından tanımlanır.|
|**Sonucu**|Test Gezgini kategori adlarını eşleşmeler için arar: **başarısız testler**, **Atlanan testler**, **başarılı testler**.|
::: moniker-end
::: moniker range=">=vs-2019"
|Leyicisini|Açıklama|
|-|-----------------|
|**State**|Test Gezgini kategori adlarını eşleşmeler için arar: **başarısız testler**, **Atlanan testler**, **başarılı testler**.|
|**Lerdir**|Hem nitelik kategorisini hem de eşleşme değerlerini arar. Nitelik kategorilerini ve değerlerini belirten sözdizimi, birim test çerçevesi tarafından tanımlanır.|
|**Tam nitelikli ad**|Test ad alanları, sınıflar ve yöntemlerin tam adını eşleşmeler için arar.|
|**Proje**|Test projesi adlarını eşleşmeler için arar.|
|**Hedef Çerçeve**|Test Gezgini kategori adlarını eşleşmeler için arar: **başarısız testler**, **Atlanan testler**, **başarılı testler**.|
|**Uzayına**|Test ad alanlarını eşleşmeler için arar.|
|**Sınıfı**|Test sınıfları adlarını eşleşmeler için arar.|
::: moniker-end

Bir filtrenin sonuçlarının bir alt kümesini dışlamak için aşağıdaki sözdizimini kullanın:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Örneğin, `FullName:"MyClass" - FullName:"PerfTest"` adı içinde "PerfTest" da dahil olan testler hariç, adında "MyClass" içeren tüm testleri döndürür.

## <a name="debug-and-analyze-unit-tests"></a>Hata ayıklama ve birim testlerini analiz etme

Testleriniz için bir hata ayıklama oturumu başlatmak üzere test Gezgini ' ni kullanabilirsiniz. Visual Studio hata ayıklayıcı ile kodunuzda adım adım geçiş, birim testleri ve test edilen proje arasında sorunsuz bir şekilde geri ve ileri doğru bir şekilde gerçekleşir. Hata ayıklamayı başlatmak için:

1. Visual Studio düzenleyicisinde, hata ayıklamak istediğiniz bir veya daha fazla test yöntemlerinde bir kesme noktası ayarlayın.

    > [!NOTE]
    > Test yöntemleri herhangi bir sırada çalıştırılabildiğinden, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktaları ayarlayın.

2. Test Gezgini 'nde test yöntemlerini seçin ve sağ tıklama menüsünde **Seçili testlerin hatalarını ayıkla** ' yı seçin.

   Hata ayıklayıcı hakkında daha fazla bilgi için bkz. [Visual Studio 'Da hata ayıklama](../debugger/debugger-feature-tour.md).

### <a name="diagnose-test-method-performance-issues"></a>Test yöntemi performans sorunlarını tanılama

Bir test yönteminin neden çok fazla zaman aldığını tanılamak için test Gezgini 'nde yöntemi seçin ve sağ tıklama menüsünde **profil seçili test** ' i seçin. Bkz. [Performans Gezgini](../profiling/performance-explorer.md).

### <a name="analyze-unit-test-code-coverage"></a>Birim testi kod kapsamını analiz etme

Visual Studio Enterprise sürümünde kullanılabilir olan Visual Studio kod kapsamı aracını kullanarak birim testleriniz tarafından test edilen ürün kodu miktarını belirleyebilirsiniz. Seçili testlerde veya bir Çözümdeki tüm testlerde kod kapsamını çalıştırabilirsiniz.

Bir çözümde test yöntemleri için kod kapsamını çalıştırmak için:

::: moniker range="vs-2017"

1. Üstteki menü çubuğunda **Test** ' i seçin ve ardından **kod kapsamını analiz et**' i seçin.

2. Alt menüden aşağıdaki komutlardan birini seçin:

    - **Seçili testler** , test Gezgini 'nde seçtiğiniz test yöntemlerini çalıştırır.

    - **Tüm testler** Çözümdeki tüm test yöntemlerini çalıştırır.

::: moniker-end

::: moniker range=">=vs-2019"

* Test Gezgini ' ne sağ tıklayın ve **Seçili testler Için kod kapsamını çözümle** ' yi seçin.

::: moniker-end

**Kod kapsamı sonuçları** penceresi, satır, işlev, sınıf, ad alanı ve modül tarafından uygulanan ürün kodu bloklarının yüzdesini görüntüler.

Daha fazla bilgi için bkz. kod [kapsamını kullanarak ne kadar kodun test edildiğini belirleme](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="test-shortcuts"></a>Test kısayolları

Testler test Gezgini 'nden, test üzerindeki kod düzenleyicisine sağ tıklayıp **Test Çalıştır** ' ı seçerek veya Visual Studio 'Daki varsayılan [Test Gezgini kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) kullanılarak çalıştırılabilir. Bazı kısayollar bağlam tabanlıdır. Bu, imlecinizin kod düzenleyicisinde olduğu yere göre testleri çalıştırdıkları veya hata ayıkladıkları anlamına gelir. İmlecinizin bir test yöntemi içindeyse, bu test yöntemi çalışır. İmlecinizin sınıf düzeyi ise, o sınıftaki tüm testler çalıştırılır. Bu, ad alanı düzeyi için de aynıdır.

|Sık kullanılan komutlar| Klavye Kısayolları|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**Ctrl** +**R**, **CTRL** +**t**|
|TestExplorer.RunAllTestsInContext|**Ctrl** +**R**, **t**|
|TestExplorer.RunAllTests|**Ctrl** +**R**, **A**|
|TestExplorer.RepeatLastRun|**Ctrl** +**R**, **L**|

> [!NOTE]
> Testler yalnızca soyut sınıflarda tanımlandığından ve örneklenmemiş olduğundan, bir testi soyut bir sınıfta çalıştıramazsınız. Testleri soyut sınıflarda çalıştırmak için soyut sınıftan türeten bir sınıf oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](../test/unit-test-your-code.md)
- [64 bitlik bir işlem olarak birim testi çalıştırma](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Test Gezgini Hakkında SSS](test-explorer-faq.md)
