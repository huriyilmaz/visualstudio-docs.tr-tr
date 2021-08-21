---
title: Test Gezgini ile birim testleri çalıştırma
description: Test Gezgini ile test çalıştırma hakkında bilgi Visual Studio. Bu konu, derleme sonrasında otomatik test çalıştırmalarını etkinleştirme, test sonuçlarını görüntüleme, test listesini gruplama ve filtreleme, çalma listeleri oluşturma ve test kısayollarını kullanma konularını kapsar.
ms.date: 01/11/2021
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 97dd55ecfc5f66abc4df8becbecbe608d93a7dfb
ms.sourcegitcommit: e6aeefef5b659a56e6e433d155bfd269c46bceb0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2021
ms.locfileid: "122603638"
---
# <a name="run-unit-tests-with-test-explorer"></a>Test Gezgini ile birim testleri çalıştırma

Test Gezgini'ni kullanarak Visual Studio veya üçüncü taraf birim testi projelerinden birim testleri çalıştırın. Test Gezgini'ni kullanarak testleri kategorilere gruplandırabilir, test listesini filtreleyin ve test oynatma listeleri oluşturabilir, kaydedebilir ve çalıştırabilirsiniz. Test Gezgini'ni birim [testlerinde hata ayıklamak ve](../test/debug-unit-tests-with-test-explorer.md) kod Visual Studio Enterprise analiz etmek [için de kullanabilirsiniz.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

**Test Gezgini,** bir çözümde yer alan birden çok test projesinde ve üretim kodu projelerinin parçası olan test sınıflarından testleri çalıştırabilir. Test projeleri farklı birim testi çerçeveleri kullanabilir. Test altındaki kod .NET için yazıldığı zaman, test projesi hedef kodun dilinden bağımsız olarak .NET'i de hedef alan herhangi bir dilde yazabilir. Yerel C/C++ kod projeleri bir C++ birim testi çerçevesi kullanılarak test edilebilir.

## <a name="build-your-test-project"></a>Test projenizi oluşturma

Visual Studio çözümde ayarlanmış bir test projeniz yoksa, önce bir test projesi oluşturmanız ve derlemeniz gerekir.

- [Kullanmaya başlayın testi (.NET) ile ilgili genel bilgi](../test/getting-started-with-unit-testing.md)
- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

Visual Studio yönetilen ve yerel kod için Microsoft birim testi çerçevelerini içerir. Ancak, Test Gezgini bir Test Gezgini bağdaştırıcısı uygulayan herhangi bir birim testi çerçevesini de çalıştırabilirsiniz. Üçüncü taraf birim test çerçevelerini yükleme hakkında daha fazla bilgi için [bkz. Üçüncü taraf birim test çerçevelerini yükleme](../test/install-third-party-unit-test-frameworks.md)

## <a name="run-tests-in-test-explorer"></a>Test Gezgini'nde testleri çalıştırma

Test projesini derlemek için testler Test Gezgini'nde görünür. Test Gezgini görünmüyorsa, Visual Studio menüsünde **Test'i** seçin, Windows'ı seçin ve ardından **Test** Gezgini'ni seçin **(veya Ctrl** E , T  +  **tuşlarına** **basın).**

::: moniker range="vs-2017"
![Birim Testi Gezgini](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test Gezgini](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Testlerinizi çalıştırarak, yazarak ve yeniden çalıştırdığında, Test Gezgini sonuçları varsayılan Başarısız  Testler **,** **Başarılı** Testler , Atlanan Testler ve Testleri **Çalıştırmadı gruplarında görüntüler.** Test Gezgini'nin testlerinizi gruplama yolunu değiştirebilirsiniz.
::: moniker-end
::: moniker range=">=vs-2019"
Testlerinizi çalıştırarak, yazarak ve yeniden çalıştırarak, Test Gezgini sonuçları varsayılan gruplamada **Project**, **Ad Alanı** ve Sınıf olarak **görüntüler.** Test Gezgini'nin testlerinizi gruplama yolunu değiştirebilirsiniz.
::: moniker-end

Test Gezgini araç çubuğundan testleri bulma, düzenleme ve çalıştırma işleminin büyük **bir işlemini gerçekleştirebilirsiniz.**

::: moniker range="vs-2017"
![Test Gezgini araç çubuğundan testleri çalıştırma](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test Gezgini araç çubuğundan testleri çalıştırma](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

### <a name="run-tests"></a>Testleri çalıştırma

::: moniker range="vs-2017"
Çözümde tüm testleri, bir gruptaki tüm testleri veya sizin seçen bir dizi testi çalıştırarak bunu çalıştırarak. Aşağıdakilerden birini yapın:

- Bir çözümde tüm testleri çalıştırmak için, Hepsini Çalıştır'ı **seçin** (veya **Ctrl** R , V + **tuşlarına** **basın).**

- Varsayılan gruptaki tüm testleri çalıştırmak için Çalıştır'ı **ve** ardından menüden grubu seçin.

- Çalıştırmak istediğiniz testleri seçin, seçili testin sağ tıklama menüsünü açın ve  ardından Seçili Testleri Çalıştır'ı seçin **(veya Ctrl** + **R**, T tuşlarına **basın).**

- Tek tek testlerin herhangi bir sırada çalıştırılamalarını engelleyen bağımlılıkları yoksa, ile paralel test yürütmeyi ![Test Gezgini araç çubuğundaki Paralel test yürütme iki durumlu Visual Studio düğmesinin ekran görüntüsü. Bu düğme seçildiğinde testler paralel olarak çalıştırıldığında.](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğmeyi seçin. Bu, tüm testleri çalıştırmak için gereken zamanı önemli ölçüde azaltabilirsiniz.

Test **Gezgini penceresinin üst** kısmında yer alan **geçiş/başarısız** çubuğu, testler çalıştırıken animasyonlu olarak gösterilir. Test çalıştırması sonunda, tüm testler **başarılı olursa geçiş/başarısız** çubuğu yeşile, test başarısız olursa kırmızıya döner.
::: moniker-end
::: moniker range=">=vs-2019"
Çözümde tüm testleri, bir gruptaki tüm testleri veya sizin seçen bir dizi testi çalıştırarak bunu çalıştırarak. Aşağıdakilerden birini yapın:

- Bir çözümde tüm testleri çalıştırmak  için, Tüm Çalıştır simgesini seçin (veya **Ctrl** R , V + **tuşlarına** **basın).**

- Tüm testleri varsayılan grupta çalıştırmak için Çalıştır **simgesini ve** ardından menüden grubu seçin.

- Çalıştırmak istediğiniz testleri seçin, seçili testin sağ tıklama menüsünü açın ve  ardından Seçili Testleri Çalıştır'ı seçin **(veya Ctrl** + **R**, T tuşlarına **basın).**

- Tek tek testlerin herhangi bir sırada çalışmasına engel olan bağımlılıklar yoksa, araç çubuğunun ayarlar menüsünde paralel test yürütmeyi açın. Bu, tüm testleri çalıştırmak için gereken zamanı önemli ölçüde azaltabilirsiniz.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Her derlemeden sonra testleri çalıştırma
::: moniker range="vs-2017"
|Düğme|Description|
|-|-|
|![Derlemeden sonra çalıştır](../test/media/ute_runafterbuild_btn.png)|Birim testlerinizi her yerel derlemeden sonra çalıştırmak için standart  menüde **Test'i** ve ardından Test Gezgini araç çubuğunda Derlemeden Sonra Testleri **Çalıştır'ı** seçin.|

> [!NOTE]
> Her derlemeden sonra birim testlerinin çalıştır Visual Studio 2017 Enterprise veya 2019 Visual Studio gerekir. Bu Visual Studio 2019'da hem Community hem de Professional'a Enterprise.
::: moniker-end
::: moniker range=">=vs-2019"
Birim testlerinizi her yerel derlemeden sonra çalıştırmak için Test Gezgini araç çubuğunda ayarlar simgesini açın ve Derlemeden Sonra **Testleri Çalıştır'ı seçin.**
::: moniker-end

## <a name="view-test-results"></a>Test sonuçlarını görüntüleme

Testlerinizi çalıştırarak, yazarak ve yeniden çalıştırdığında, Test Gezgini sonuçları Başarısız  Testler **,** **Başarılı** Testler, Atlanan Testler ve Testleri **Çalıştırmadı gruplarında görüntüler.** Test Gezgini'nin alt veya tarafındaki ayrıntılar bölmesinde test çalıştırması özeti görüntülenir.

### <a name="view-test-details"></a>Test ayrıntılarını görüntüleme

Tek bir testin ayrıntılarını görüntülemek için testi seçin.

::: moniker range="vs-2017"
![Test yürütme ayrıntıları](../test/media/ute_testdetails.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test yürütme ayrıntıları](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end

Test ayrıntıları bölmesinde aşağıdaki bilgiler görüntülenir:

- Test yönteminin kaynak dosya adı ve satır numarası.

- Testin durumu.

- Test yönteminin çalışması için geçen süre.

Test başarısız olursa ayrıntılar bölmesi de şunları görüntüler:

- Test için birim testi çerçevesi tarafından döndürülen ileti.

- Test başarısız olduğu sırada yığın izlemesi.

### <a name="view-the-source-code-of-a-test-method"></a>Test yönteminin kaynak kodunu görüntüleme

Test yönteminin kaynak kodunu düzenleyicide görüntülemek Visual Studio testi seçin ve ardından sağ tıklama menüsünde **Testi** Aç'ı seçin (veya **F12 tuşuna basın).**

## <a name="group-and-filter-the-test-list"></a>Test listesini grupla ve filtrele

Test Gezgini, testlerinizi önceden tanımlanmış kategorilerde gruplamanızı sağlar. Test Gezgini'nde çalıştır edilen birim testi çerçevelerinin çoğu, testlerinizi gruplayarak kendi kategorilerinizi ve kategori/değer çiftlerinizi tanımlamanıza izin verir. Ayrıca, dizeleri test özellikleriyle eşleştirerek test listesini filtreleebilirsiniz.

### <a name="group-tests-in-the-test-list"></a>Test listesinde testleri grupla

::: moniker range="vs-2017"
Testleri düzenleme yolunu değiştirmek için, Gruplama Ölçütü düğmesinin yanındaki aşağı oku Test Gezgini grup düğmesini seçin ve yeni bir  ![ ](../test/media/ute_groupby_btn.png) gruplama ölçütü seçin.

![Test Gezgini'nde testleri kategoriye göre grupla](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
Test Gezgini, testlerinizi bir hiyerarşide gruplamanızı sağlar. Varsayılan hiyerarşi gruplama, **Project** **, Ad Alanı** ve ardından **Sınıf'tır.** Testleri düzenleme yolunu değiştirmek için, Test Gezgini **grup** düğmesini Seçerek Grupla düğmesini ![ seçin ve yeni bir ](../test/media/ute_groupby_btn.png) gruplama ölçütü seçin.

![Test Gezgini'nde testleri kategoriye göre grupla](../test/media/vs-2019/test-explorer-groupby-162.png)

Hiyerarşi ve grup düzeylerinizi State'e  ve  ardından Sınıf'a göre tanımlayabilirsiniz. Örneğin, tercih ettiğiniz sırayla Grupla seçeneğini belirleyin.

![Bir bölmede bir test Visual Studio ve diğer bölmede Sınıf ve Durum seçeneklerinin işaretli olduğu Grupla menüsünü gösteren Test Gezgini'nin ekran görüntüsü.](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Test Gezgini grupları

::: moniker range="vs-2017"
|Grup|Açıklama|
|-|-----------------|
|**Süre**|Gruplar yürütme süresine göre test ediyor: **Hızlı,** **Orta** ve **Yavaş.**|
|**Sonuç**|Testleri yürütme sonuçlarına göre **gruplar: Başarısız Testler**, **Atlanan Testler**, Başarılı **Testler**.|
|**Özellik**|Grupları test etmek için tanımladığınız kategori/değer çiftlerini kullanın. Nitelik kategorilerini ve değerlerini belirtme söz dizimi birim testi çerçevesi tarafından tanımlanır.|
|**Project**|Grupların testini projelerin adına göre sınar.|
::: moniker-end
::: moniker range=">=vs-2019"
|Grup|Açıklama|
|-|-----------------|
|**Süre**|Testleri yürütme süresine göre gruplar: **Hızlı,** **Orta** ve **Yavaş.**|
|**Durum**|Testleri yürütme sonuçlarına göre gruplar: **Başarısız Testler**, **Atlanan Testler**, Başarılı **Testler**, **Çalıştırılamadı**|
|**Hedef Çerçeve** | Testleri proje hedefi çerçevesine göre gruplar |
|**Ad Alanı**|Testleri içeren ad alanına göre gruplar.|
|**Project**|Testleri içeren projeye göre gruplar.|
|**Sınıf**|Testleri içeren sınıfına göre gruplar.|
::: moniker-end

### <a name="traits"></a>Özellik

Nitelik genellikle bir kategori adı/değer çiftidir, ancak tek bir kategori de olabilir. Nitelikler, birim testi çerçevesi tarafından test yöntemi olarak tanımlanan yöntemlere atanabilir. Birim testi çerçevesi nitelik kategorilerini tanımlayabilir. Nitelik kategorilerine değer eklemek için kendi kategori adı/değer çiftlerinizi tanımlayabilirsiniz. Nitelik kategorilerini ve değerlerini belirtme söz dizimi birim testi çerçevesi tarafından tanımlanır.

**Yönetilen Kod için Microsoft Birim Testi Çerçevesi'nin Özellikleri**

Yönetilen uygulamalar için Microsoft birim testi çerçevesinde bir öznitelikte nitelik adı/değer çifti  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> tanımlarsiniz. Test çerçevesi şu önceden tanımlanmış özellikleri de içerir:

|Özellik|Description|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Sahip kategorisi birim testi çerçevesi tarafından tanımlanır ve sahibin dize değerini sağlamanız gerekir.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Öncelik kategorisi birim testi çerçevesi tarafından tanımlanır ve önceliğe ait bir tamsayı değeri sağlamanız gerekir.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|TestCategory özniteliği, bir birim testinin kategorisini belirtmenize olanak sağlar.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|TestProperty özniteliği, nitelik kategorisi/değer çifti tanımlamaya olanak sağlar.|


**C++ için Microsoft Birim Testi Çerçevesi'nin Özellikleri**

Bkz. [C++ için Microsoft Birim Testi Çerçevesi'nin nasıl kullanımı.](how-to-use-microsoft-test-framework-for-cpp.md)

## <a name="create-custom-playlists"></a>Özel oynatma listeleri oluşturma

::: moniker range="vs-2017"
Grup olarak çalıştırmak veya görüntülemek istediğiniz testlerin listesini oluşturabilir ve kaydedebilirsiniz. Bir oynatma listesi seçerek, listede yer alan testler Test Gezgini'nde görüntülenir. Birden fazla oynatma listesine test ekleyebilirsiniz ve varsayılan Tüm Testler oynatma listesini seçtiğiniz zaman projenizin tüm **testleri** kullanılabilir.

![Oynatma listesi seçme](../test/media/ute_playlist.png)

**Oynatma listesi oluşturmak için** Test Gezgini'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde Oynatma Listesine EkleYeni Oynatma  >  **Listesi'ne tıklayın.** Dosyayı, Yeni Çalma Listesi Oluştur iletişim kutusunda belirttiğiniz ad **ve konumla** kaydedin.

**Bir çalma listesine testler eklemek için** Test Gezgini'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde Çalma Listesine **Ekle'yi** ve ardından testleri eklemek istediğiniz oynatma listesini seçin.

**Bir çalma listesi açmak** için, Visual Studio menüsünden **Test** Oynatma Listesi'ne tıklayın ve son kullanılan çalma listeleri listesinden birini seçin veya çalma listesinin adını ve konumunu belirtmek için Çalma Listesini Aç'ı >  seçin. 

Tek tek testlerin herhangi bir sırada çalıştırılamalarını engelleyen bağımlılıkları yoksa, ile paralel test yürütmeyi ![Test Gezgini araç çubuğundaki Paralel test yürütme iki durumlu Visual Studio düğmesinin ekran görüntüsü.](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğmeyi seçin. Bu, tüm testleri çalıştırmak için gereken zamanı önemli ölçüde azaltabilirsiniz.
::: moniker-end
::: moniker range=">=vs-2019"
Grup olarak çalıştırmak veya görüntülemek istediğiniz testlerin listesini oluşturabilir ve kaydedebilirsiniz. Bir oynatma listesi seçerek, listede yer alan testler yeni bir Test Gezgini sekmesinde görüntülenir. Birden fazla oynatma listesine test ekleyebilirsiniz.

**Oynatma listesi oluşturmak için** Test Gezgini'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde Oynatma Listesine Ekle Yeni **Oynatma Listesi'ne**  >  **tıklayın.**

![Oynatma listesi oluşturma](../test/media/vs-2019/test-explorer-playlist-16-2.png)

Oynatma listesi yeni bir Test Gezgini sekmesinde açılır. Bu oynatma listesini bir kez kullanabilir ve sonra  atabilir veya oynatma listesi penceresinin araç çubuğundaki Kaydet düğmesine tıklayabilirsiniz ve ardından çalma listesini kaydetmek için bir ad ve konum seçin.

![Oynatma listesi ayrı test gezgini sekmesinde açılır](../test/media/vs-2019/test-explorer-playlist-tab-16-7.png)

**Oynatma listesi oluşturmak için** Test Gezgini'nde bir veya daha fazla test seçin. Sağ tıklayın ve Oynatma Listesine **Ekle Yeni oynatma listesi'ne**  >  **tıklayın.**

**Bir oynatma listesi açmak** için, araç çubuğundaki Visual Studio simgesini seçin ve menüden daha önce kaydedilmiş bir oynatma listesi dosyasını seçin.

**Oynatma listesini düzenlemek için** herhangi bir teste sağ tıklar ve menü seçeneklerini kullanarak oynatma listesine ekleyebilir veya oynatma listesinden kaldırabilirsiniz.

2019 Visual Studio 16.7 sürümünden başlayarak araç çubuğunda **düzenle** düğmesini seçebilirsiniz. Hangi testlerin dahil olduğunu ve oynatma listesine dahil edilen testleri gösteren testlerinin yanında onay kutuları görüntülenir. Grupları dilediğiniz şekilde düzenleyin.

![Oynatma Listesini Düzenle düğmesi](../test/media/vs-2019/test-explorer-playlist-edit-16-7.png)

Hiyerarşide üst grupların kutularını da işaretlerini veya işaretini kaldırabilirsiniz. Bu eylem, o gruptaki testlere göre oynatma listesini her zaman güncelleştirmeye devam ediyor olan dinamik bir çalma listesi oluşturur. Örneğin, bir sınıfın yanına bir onay işareti eklersiniz, bu sınıftan eklenen tüm testler bu çalma listesinin bir parçası olur. Bu sınıftan bir testi silersiniz, bu test oynatma listesinden kaldırılır. Araç çubuğundaki Kaydet düğmesiyle oynatma listesini kaydederek ve diskiniz üzerinde oluşturulan *.playlist* dosyasını açarak kurallar hakkında daha fazla bilgi edinebilirsiniz. Bu dosyada, oynatma listesinin tüm kuralları ve tek tek testleri listele.

![Oynatma listesi xml dosyası](../test/media/vs-2019/test-explorer-playlist-xml-file.png)

Nitelikler için çalma listesi oluşturmak için MSTest için aşağıdaki biçimi kullanın.
```xml
<Playlist Version="2.0">
    <Rule Name="Includes" Match="Any">
        <Property Name="Trait" Value="SchemaUpdateBasic" />
    </Rule>
</Playlist>
```

xUnit için aşağıdaki biçimi kullanın. Adınızla arasında bir boşluk olduğundan `TestCategory` emin `[Value]` olun.
```xml
<Playlist Version="2.0">
  <Rule Name="Includes" Match="Any">
    <Rule Match="All">
      <Property Name="Solution" />
        <Rule Match="Any">
            <Property Name="Trait" Value="TestCategory [Value]" />
        </Rule>
    </Rule>
  </Rule>
</Playlist>
```

::: moniker-end

::: moniker range=">=vs-2019"
### <a name="test-explorer-columns"></a>Test Gezgini sütunları

Gruplar [Ayrıca](#test-explorer-groups) Nitelik, Yığın İzleme, Hata İletisi ve Tam Ad ile birlikte Test Gezgini'nde sütun olarak da kullanılabilir. Çoğu sütun varsayılan olarak görünür değildir ve hangi sütunları gördüğünüzi ve hangi sırada görüntüle olduklarını özelleştirebilirsiniz.

![Sütunlar'ın Visual Studio ve Süre, Nitelikler ve Hata İletisi'nin seçili olduğu bir alt menüyü gösteren Test Gezgini'nin ekran görüntüsü.](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Test sütunlarını filtreleme, sıralama ve yeniden düzenleme

Sütunlar filtrelenmiş, sıralanmış ve yeniden düzenlenebilir.
* Belirli niteliklere filtrelemek için Nitelikler sütununu en üst kısmında bulunan filtre simgesine tıklayın.

  ![Sütun filtresi](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* Sütunların sıralamalarını değiştirmek için bir sütun başlığına tıklayın ve bunu sola veya sağa sürükleyin.

* Bir sütunu sıralamak için sütun başlığına tıklayın. Her sütun sıralanamaz. Shift tuşunu basılı tutarak ve ek bir sütun **başlığına** tıklayarak ikincil sütuna göre de sıraabilirsiniz.

  ![Sütun sıralama](../test/media/vs-2019/test-explorer-sort-column-16-2.png)
::: moniker-end

## <a name="search-and-filter-the-test-list"></a>Test listesini arama ve filtreleme

Ayrıca, görüntülemek ve çalıştırmakta olduğu projelerde test yöntemlerini sınırlamak için Test Gezgini arama filtrelerini de kullanabilirsiniz.

**Test** Gezgini arama kutusuna bir dize yazın ve **Enter'ı** seçin. Test listesi yalnızca tam adları dizeyi içeren testleri görüntülemek için filtrelenmiş.

Farklı ölçütlere göre filtrelemek için:

1. Arama kutusunun sağ üst tarafından açılan listeyi açın.

2. Yeni bir ölçüt seçin.

3. Tırnak işaretleri arasına filtre değerini girin. Içeren bir eşleşme yerine dizede tam eşleşme aramak için iki nokta üst üste (iki nokta işareti) yerine eşittir işareti (=) :).

::: moniker range="vs-2017"
![Test Gezgini'nde testleri filtreleme](../test/media/ute_filtertestlist.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test Gezgini'nde testleri filtreleme](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

> [!NOTE]
> Aramalar büyük/büyük/büyük harfe duyarlı değildir ve belirtilen dizeyi ölçüt değerinin herhangi bir bölümüyle eşler.

::: moniker range="vs-2017"
|Niteleyici|Description|
|-|-----------------|
|**Özellik**|Eşleşmeler için hem nitelik kategorisini hem de değeri arar. Nitelik kategorilerini ve değerlerini belirtme söz dizimi birim testi çerçevesi tarafından tanımlanır.|
|**Project**|Test projesi adlarını eşleşmeler için arar.|
|**Hata İletisi**|Eşleşmeler için başarısız onaylar tarafından döndürülen kullanıcı tanımlı hata iletilerini arar.|
|**Dosya Yolu**|Eşleşmeler için test kaynak dosyalarının tam dosya adını arar.|
|**Tam Ad**|Eşleşmeler için test ad alanlarının, sınıfların ve yöntemlerin tam adını arar.|
|**Çıktı**|Standart çıkışa (stdout) veya standart hataya (stderr) yazılan kullanıcı tanımlı hata iletilerini arar. Çıkış iletilerini belirtme söz dizimi birim testi çerçevesi tarafından tanımlanır.|
|**Sonuç**|Test Gezgini kategori adlarını eşleşmeler için arar: **Başarısız Testler,** **Atlanan Testler**, **Başarılı Testler**.|
::: moniker-end
::: moniker range=">=vs-2019"
|Niteleyici|Description|
|-|-----------------|
|**Durum**|Test Gezgini kategori adlarını eşleşmeler için arar: **Başarısız Testler,** **Atlanan Testler**, **Başarılı Testler**.|
|**Özellik**|Eşleşmeler için hem nitelik kategorisini hem de değeri arar. Nitelik kategorilerini ve değerlerini belirtme söz dizimi birim testi çerçevesi tarafından tanımlanır.|
|**Tam Ad**|Eşleşmeler için test ad alanlarının, sınıfların ve yöntemlerin tam adını arar.|
|**Project**|Test projesi adlarını eşleşmeler için arar.|
|**Hedef Çerçeve**|Test Gezgini kategori adlarını eşleşmeler için arar: **Başarısız Testler,** **Atlanan Testler**, **Başarılı Testler**.|
|**Ad Alanı**|Test ad alanlarında eşleşmeleri arar.|
|**Sınıf**|Test sınıfları adlarını eşleşmeler için arar.|
::: moniker-end

Filtre sonuçlarının bir alt kümesini dışlamak için aşağıdaki söz dizimlerini kullanın:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Örneğin, adlarına "MyClass" içeren tüm testleri döndürür, ancak kendi adlarına `FullName:"MyClass" - FullName:"PerfTest"` "PerfTest" de içeren testler hariç.

### <a name="analyze-unit-test-code-coverage"></a>Birim testi kod kapsamı analiz etme

Visual Studio Enterprise yayınında bulunan Visual Studio kod kapsamı aracını kullanarak birim testleriniz tarafından gerçekten test edilen ürün kodu miktarını Visual Studio Enterprise. Seçilen testlerde veya bir çözümde yer alan tüm testlerde kod kapsamı çalıştırabilirsiniz.

Bir çözümde test yöntemleri için kod kapsamı çalıştırmak için:

::: moniker range="vs-2017"

1. Üst **menü çubuğunda Test'i** ve ardından Kod kapsamayı **çözümle'yi seçin.**

2. Alt menüden aşağıdaki komutlardan birini seçin:

    - **Seçilen testler,** Test Gezgini'nde seçtiğiniz test yöntemlerini çalıştırır.

    - **Tüm testler** çözümde tüm test yöntemlerini çalıştırır.

::: moniker-end

::: moniker range=">=vs-2019"

* Test Gezgini'ne sağ tıklayın ve Seçili testler **için Kod Kapsamasını Analiz Etme'yi seçin**

::: moniker-end

Kod **Kapsamı Sonuçları** penceresi satır, işlev, sınıf, ad alanı ve modül tarafından alıştırma yapılan ürün kodu bloklarının yüzdesini görüntüler.

Daha fazla bilgi için [bkz. Ne kadar kodun test olduğunu belirlemek için kod kapsamı kullanma.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

## <a name="test-shortcuts"></a>Test kısayolları

Testler, testte kod düzenleyicisine sağ tıklar ve Testi çalıştır'ı seçerek veya test düzenleyicisinde varsayılan Test Gezgini kısayollarını kullanarak [Test Gezgini'Visual Studio.](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)  Kısayollardan bazıları bağlam tabanlıdır. Bu, imlecinizin kod [düzenleyicisinde bulunduğu yere](../test/debug-unit-tests-with-test-explorer.md) göre testleri çalıştıracakları veya hata ayıklayacakları anlamına gelir. İmleciniz bir test yönteminin içinde yer alırsa bu test yöntemi çalışır. İmleciniz sınıf düzeyinde ise, o sınıftaki tüm testler çalıştır. Bu, ad alanı düzeyi için de aynıdır.

|Sık Kullanılan Komutlar| Klavye Kısayolları|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**Ctrl tuşunu basılı tutarak** + **R**, **Ctrl** + **T**|
|TestExplorer.RunAllTestsInContext|**Ctrl tuşunu basılı tutarak** + **R,** **T**|
|TestExplorer.RunAllTests|**Ctrl tuşunu basılı tutarak** + **R,** **A**|
|TestExplorer.RepeatLastRun|**Ctrl tuşunu basılı tutarak** + **R,** **L**|

> [!NOTE]
> Testler yalnızca soyut sınıflarda tanımlandığı ve örneklanmamış olduğu için bir testi soyut sınıfta çalıştıraabilirsiniz. Soyut sınıflarda testleri çalıştırmak için soyut sınıftan türetilen bir sınıf oluşturun.

::: moniker range=">=vs-2019"
## <a name="test-audio-cue"></a>Ses ipucu testi
Test Gezgini, bir test çalıştırması tamamlandığında ses çalabilirsiniz. İki ses var: Test çalıştırmanın tüm testlerden geçerek başarılı olduğunu gösteren bir ses ve test çalıştırması en az bir başarısız testle tamamlandıktan sonra ikinci bir ses. Bu sesleri varsayılan ses iletişim kutusunda Windows 10 ayarlayabilirsiniz. Bu özellik, Visual Studio 2019 Güncelleştirme 16.9 Önizleme 3'te başlayarak kullanılabilir.

1. Varsayılan ses iletişim Windows 10 açın.
2. Sesler **sekmesine** gidin.
3. Microsoft Visual Studio **bulun.** Önceden ayarlanmış **sesleri seçmek veya kendi** ses **dosyanıza** göz atmak için Test Çalıştırması Başarılı veya Test Çalıştırması Başarısız seslerini seçin.  
![Windows 10 iletişim kutusu](../test/media/default-windows-10-sound-dialog.png)

::: moniker-end
## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu birim testi](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testlerinde hata ayıklama](../test/debug-unit-tests-with-test-explorer.md)
- [64 bitlik bir işlem olarak birim testi çalıştırma](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Test Gezgini Hakkında SSS](test-explorer-faq.md)
