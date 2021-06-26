---
title: Test Gezgini ile birim testleri çalıştırma
description: Visual Studio'da Test Gezgini ile test çalıştırmayı Visual Studio. Bu konu, derleme sonrasında otomatik test çalıştırmalarını etkinleştirme, test sonuçlarını görüntüleme, test listesini gruplama ve filtreleme, çalma listeleri oluşturma ve test kısayollarını kullanma konularını kapsar.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 26dbed25f42f40614597075ad26c855398b56025
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925130"
---
# <a name="run-unit-tests-with-test-explorer"></a>Test Gezgini ile birim testleri çalıştırma

Test Gezgini'ni kullanarak Visual Studio veya üçüncü taraf birim testi projelerinden birim testleri çalıştırın. Test Gezgini'ni kullanarak testleri kategorilere gruplandırabilir, test listesini filtreleyin ve test oynatma listeleri oluşturabilir, kaydedebilir ve çalıştırabilirsiniz. Kod kapsamı ve birim testlerinde hata [ayıklamayı da analiz edersiniz.](../test/debug-unit-tests-with-test-explorer.md)

**Test Gezgini,** bir çözümde yer alan birden çok test projesinde ve üretim kodu projelerinin parçası olan test sınıflarından testleri çalıştırabilir. Test projeleri farklı birim testi çerçeveleri kullanabilir. Test altındaki kod .NET için yazıldığı zaman, test projesi hedef kodun dilinden bağımsız olarak .NET'i de hedef alan herhangi bir dilde yazabilir. Yerel C/C++ kod projeleri bir C++ birim testi çerçevesi kullanılarak test edilebilir.

## <a name="build-your-test-project"></a>Test projenizi oluşturma

Visual Studio çözümde ayarlanmış bir test projeniz yoksa, önce bir test projesi oluşturmanız ve derlemeniz gerekir.

- [Kullanmaya başlayın testi ile ilgili genel bilgi (.NET)](../test/getting-started-with-unit-testing.md)
- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

Visual Studio yönetilen ve yerel kod için Microsoft birim testi çerçevelerini içerir. Ancak, Test Gezgini bir Test Gezgini bağdaştırıcısı uygulayan herhangi bir birim testi çerçevesini de çalıştırabilirsiniz. Üçüncü taraf birim test çerçevelerini yükleme hakkında daha fazla bilgi için [bkz. Üçüncü taraf birim test çerçevelerini yükleme](../test/install-third-party-unit-test-frameworks.md)

## <a name="run-tests-in-test-explorer"></a>Test Gezgini'nde testleri çalıştırma

Test projesini derlemek için testler Test Gezgini'nde görünür. Test Gezgini görünmüyorsa, test menüsünde **Test'Visual Studio** **Windows'u** seçin ve ardından **Test** Gezgini'ni seçin **(veya Ctrl** E , T  +  **tuşlarına** **basın).**

::: moniker range="vs-2017"
![Birim Testi Gezgini](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test Gezgini](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Testlerinizi çalıştırarak, yazarak ve yeniden çalıştırdığında, Test Gezgini sonuçları varsayılan Başarısız  Testler **,** **Başarılı** Testler , Atlanan Testler ve **Testleri Çalıştırmadı gruplarında görüntüler.** Test Gezgini'nin testlerinizi gruplama yolunu değiştirebilirsiniz.
::: moniker-end
::: moniker range=">=vs-2019"
Testlerinizi çalıştırarak, yazarak ve yeniden çalıştırarak, Test Gezgini sonuçları **varsayılan proje,** ad alanı ve sınıf **gruplamalarında** **görüntüler.** Test Gezgini'nin testlerinizi gruplama yolunu değiştirebilirsiniz.
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
Çözümde tüm testleri, bir gruptaki tüm testleri veya sizin seçerek bir dizi testi çalıştırarak bunu çalıştırarak. Aşağıdakilerden birini yapın:

- Bir çözümde tüm testleri çalıştırmak için, Hepsini Çalıştır'ı **seçin** (veya **Ctrl** R , V + **tuşlarına** **basın).**

- Varsayılan gruptaki tüm testleri çalıştırmak için Çalıştır'ı **ve** ardından menüden grubu seçin.

- Çalıştırmak istediğiniz testleri seçin, seçili testin sağ tıklama menüsünü açın ve  ardından Seçili Testleri Çalıştır'ı seçin **(veya Ctrl** + **R**, T tuşlarına **basın).**

- Tek tek testlerin herhangi bir sırada çalışmasına engel olan bağımlılıklar yoksa, ile paralel test yürütmesini ![Test Gezgini araç çubuğundaki Paralel test yürütme iki durumlu Visual Studio düğmesinin ekran görüntüsü. Bu düğme seçildiğinde testler paralel olarak çalıştırıldığında.](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğmeyi seçin. Bu, tüm testleri çalıştırmak için gereken zamanı önemli ölçüde azaltabilirsiniz.

Test **Gezgini penceresinin üst** kısmında yer alan **geçiş/başarısız** çubuğu, testler çalıştırıken animasyonlu olarak gösterilir. Test çalıştırması sonunda, tüm testler **başarılı olursa geçiş/başarısız** çubuğu yeşile, test başarısız olursa kırmızıya döner.
::: moniker-end
::: moniker range=">=vs-2019"
Çözümde tüm testleri, bir gruptaki tüm testleri veya sizin seçerek bir dizi testi çalıştırarak bunu çalıştırarak. Aşağıdakilerden birini yapın:

- Bir çözümde tüm testleri çalıştırmak  için, Tüm Çalıştır simgesini seçin (veya **Ctrl** R , V + **tuşlarına** **basın).**

- Tüm testleri varsayılan grupta çalıştırmak için Çalıştır **simgesini ve** ardından menüden grubu seçin.

- Çalıştırmak istediğiniz testleri seçin, seçili testin sağ tıklama menüsünü açın ve  ardından Seçili Testleri Çalıştır'ı seçin **(veya Ctrl** + **R**, T tuşlarına **basın).**

- Tek tek testlerin herhangi bir sırada çalışmasına engel olan bağımlılıklar yoksa, araç çubuğunun ayarlar menüsünde paralel test yürütmeyi açın. Bu, tüm testleri çalıştırmak için gereken zamanı önemli ölçüde azaltabilirsiniz.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Her derlemeden sonra testleri çalıştırma
::: moniker range="vs-2017"
|Düğme|Açıklama|
|-|-|
|![Derlemeden sonra çalıştır](../test/media/ute_runafterbuild_btn.png)|Birim testlerinizi her yerel derlemeden sonra çalıştırmak için standart  menüde **Test'i** ve ardından Test Gezgini araç çubuğunda Derlemeden Sonra Testleri **Çalıştır'ı** seçin.|

> [!NOTE]
> Her derlemeden sonra birim testlerinin çalıştırılma Visual Studio 2017 Enterprise veya Visual Studio 2019 gerekir. Bu Visual Studio 2019'da Community, Professional ve Enterprise'a dahil edildi.
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

Test yönteminin kaynak kodunu Visual Studio görüntülemek için testi seçin ve ardından sağ tıklama menüsünde **Testi** Aç'ı seçin (veya **F12 tuşuna basın).**

## <a name="group-and-filter-the-test-list"></a>Test listesini grupla ve filtrele

Test Gezgini, testlerinizi önceden tanımlanmış kategorilerde gruplamanızı sağlar. Test Gezgini'nde çalıştır edilen birim testi çerçevelerinin çoğu, testlerinizi gruplayarak kendi kategorilerinizi ve kategori/değer çiftlerinizi tanımlamanıza izin verir. Ayrıca, dizeleri test özellikleriyle eşleştirerek test listesini filtreleebilirsiniz.

### <a name="group-tests-in-the-test-list"></a>Test listesinde testleri grupla

::: moniker range="vs-2017"
Testleri düzenleme yolunu değiştirmek için, Gruplama Ölçütü düğmesinin yanındaki aşağı oku Test Gezgini grup düğmesini seçin ve yeni bir  ![ ](../test/media/ute_groupby_btn.png) gruplama ölçütü seçin.

![Test Gezgini'nde testleri kategoriye göre grupla](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
Test Gezgini, testlerinizi bir hiyerarşide gruplamanızı sağlar. Varsayılan hiyerarşi grubu **Proje,** Ad **Alanı ve** ardından **Sınıf'tır.** Testleri düzenleme yolunu değiştirmek için, Test Gezgini **grup** düğmesini Seçerek Grupla düğmesini ![ seçin ve yeni bir ](../test/media/ute_groupby_btn.png) gruplama ölçütü seçin.

![Test Gezgini'nde testleri kategoriye göre grupla](../test/media/vs-2019/test-explorer-groupby-162.png)

Hiyerarşi ve grup düzeylerinizi State'e  ve  ardından Sınıf'a göre tanımlayabilirsiniz. Örneğin, tercih ettiğiniz sırayla Grupla seçeneğini belirleyin.

![Bir bölmede bir test Visual Studio diğer bölmede Sınıf ve Durum seçeneklerinin işaretli olduğu Grupla menüsünü gösteren Test Gezgini'nin ekran görüntüsü.](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Test Gezgini grupları

::: moniker range="vs-2017"
|Grup|Açıklama|
|-|-----------------|
|**Süre**|Gruplar yürütme süresine göre test ediyor: **Hızlı,** **Orta** ve **Yavaş.**|
|**Sonuç**|Testleri yürütme sonuçlarına göre **gruplar: Başarısız Testler**, **Atlanan Testler**, Başarılı **Testler**.|
|**Özellik**|Grupları test etmek için tanımladığınız kategori/değer çiftlerini kullanın. Nitelik kategorilerini ve değerlerini belirtmek için söz dizimi birim testi çerçevesi tarafından tanımlanır.|
|**Project**|Grupların testini projelerin adına göre sınar.|
::: moniker-end
::: moniker range=">=vs-2019"
|Grup|Açıklama|
|-|-----------------|
|**Süre**|Testleri yürütme zamanına göre gruplandırır: **hızlı**, **Orta** ve **yavaş**.|
|**Durum**|Testleri yürütme sonuçlarına göre gruplandırır: **başarısız testler**, **Atlanan testler**, **başarılı testler**, **çalıştırılmadı**|
|**Hedef Çerçeve** | Testleri, projeleri hedeflerine göre gruplandırır |
|**Ad Alanı**|Testleri içerilen ad alanına göre gruplandırır.|
|**Project**|Testleri içeren proje tarafından gruplandırır.|
|**Sınıf**|Testleri içerilen sınıfa göre gruplandırır.|
::: moniker-end

### <a name="traits"></a>Lerdir

Bir nitelik genellikle kategori adı/değer çiftidir, ancak tek bir kategori de olabilir. Nitelikler, birim test çerçevesi tarafından test yöntemi olarak tanımlanan yöntemlere atanabilir. Bir birim test çerçevesi, nitelik kategorilerini tanımlayabilir. Kendi Kategori ad/değer çiftlerinizi tanımlamak için nitelik kategorilerine değerler ekleyebilirsiniz. Nitelik kategorilerini ve değerlerini belirten sözdizimi, birim test çerçevesi tarafından tanımlanır.

**Yönetilen kod için Microsoft birim testi çerçevesindeki nitelikler**

Yönetilen uygulamalar için Microsoft birim testi çerçevesinde, bir öznitelikte nitelik ad/değer çifti tanımlarsınız  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> . Test çerçevesi aşağıdaki önceden tanımlı nitelikleri de içerir:

|Nitelik|Açıklama|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Sahip kategorisi, birim test çerçevesi tarafından tanımlanır ve sahibin dize değerini sağlamanızı gerektirir.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Öncelik kategorisi, birim test çerçevesi tarafından tanımlanır ve öncelik için bir tamsayı değeri sağlamanızı gerektirir.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|TestCategory özniteliği bir birim testinin kategorisini belirtmenize olanak sağlar.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|TestProperty özniteliği nitelik kategori/değer çiftini tanımlamanızı sağlar.|


**C++ için Microsoft birim testi çerçevesindeki nitelikler**

Bkz. [C++ Için Microsoft birim testi çerçevesini kullanma](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="create-custom-playlists"></a>Özel çalma listeleri oluşturma

::: moniker range="vs-2017"
Çalıştırmak veya bir grup olarak görüntülemek istediğiniz testlerin listesini oluşturabilir ve kaydedebilirsiniz. Bir çalma listesi seçtiğinizde, listedeki testler test Gezgini 'nde görüntülenir. Birden fazla çalma listesine bir test ekleyebilirsiniz ve varsayılan **Tüm testler** çalma listesini seçtiğinizde projenizdeki tüm testler kullanılabilir.

![Bir çalma listesi seçin](../test/media/ute_playlist.png)

**Bir çalma listesi oluşturmak için**, test Gezgini 'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde, **Yapılacaklar** listesi  >  **NewPlaylist** listesine ekle ' yi seçin. Dosyayı **Yeni çalma listesi oluştur** iletişim kutusunda belirttiğiniz ad ve konuma kaydedin.

**Bir çalma listesine test eklemek için**, test Gezgini 'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde, **çalma listesine ekle**' yi seçin ve ardından testleri eklemek istediğiniz çalma listesini seçin.

**Bir çalma listesi açmak için**  > Visual Studio menüsünden test **listesi** ' ni seçin ve son kullanılan çalma listeleri listesinden seçim yapın veya çalma listesini **Aç** ' ı seçerek şarkı listesinin adını ve konumunu belirtin.

Bireysel testlerin herhangi bir sırada çalıştırılmasını önleyen bir bağımlılığı yoksa, paralel test yürütme özelliğini ![Visual Studio Test Gezgini araç çubuğundaki paralel test yürütme geçiş düğmesi ekran görüntüsü.](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğme. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.
::: moniker-end
::: moniker range=">=vs-2019"
Çalıştırmak veya bir grup olarak görüntülemek istediğiniz testlerin listesini oluşturabilir ve kaydedebilirsiniz. Bir çalma listesi seçtiğinizde, listedeki testler yeni bir test Gezgini sekmesinde görüntülenir. Birden fazla çalma listesine bir test ekleyebilirsiniz.

**Bir çalma listesi oluşturmak için**, test Gezgini 'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde, **Yapılacaklar** listesi  >  **Yeni çalma listesine** Ekle ' yi seçin.

![Çalma listesi oluşturma](../test/media/vs-2019/test-explorer-playlist-16-2.png)

Yeni bir test Gezgini sekmesinde çalma listesi açılır. Bu çalma listesini bir kez kullanarak atabilir veya çalma listesi penceresinin araç çubuğunda **Kaydet** düğmesine tıklayabilir ve sonra da bir ad ve konum seçerek çalma listesini kaydedebilirsiniz.

![Çalma listesi ayrı test Gezgini sekmesinde açılıyor](../test/media/vs-2019/test-explorer-playlist-tab-16-7.png)

**Bir çalma listesi oluşturmak için**, test Gezgini 'nde bir veya daha fazla test seçin. Sağ tıklayın ve yeni çalma listesine **Ekle**' yi seçin  >  .

**Bir çalma listesi açmak için**, Visual Studio araç çubuğunda çalma listesi simgesini seçin ve menüden önceden kaydedilmiş bir çalma listesi dosyası seçin.

**Bir çalma listesini düzenlemek için** herhangi bir teste sağ tıklayıp Menü seçeneklerini kullanarak bir çalma listesine ekleyin veya kaldırabilirsiniz.

Visual Studio 2019 sürüm 16,7 ' den başlayarak, araç çubuğunda **Düzenle** düğmesini seçebilirsiniz. Testlerin yanında, çalma listesine nelerin ekleneceğini ve dışlanacağını gösteren onay kutuları görünür. Grupları dilediğiniz şekilde düzenleyin.

![Çalma listesini Düzenle düğmesi](../test/media/vs-2019/test-explorer-playlist-edit-16-7.png)

Ayrıca hiyerarşideki üst grupların kutularını denetleyebilir veya işaretini kaldırabilirsiniz. Bu eylem, o gruptaki testlere göre her zaman çalma listesini güncelleştiren dinamik bir çalma listesi oluşturur. Örneğin, bir sınıfın yanına bir onay işareti koyarsanız, bu sınıftan eklenen herhangi bir test, bu çalma listesinin bir parçası haline gelir. Bu sınıftan bir testi silerseniz, bu, çalma listesinden kaldırılır. Araç çubuğundan Kaydet düğmesini kaydederek ve diskinizde oluşturulan *. Playlist* dosyasını açarak kurallar hakkında daha fazla bilgi edinebilirsiniz. Bu dosya, bir çalma listesi oluşturan tüm kuralları ve bireysel testleri listeler.

![Playlist XML dosyası](../test/media/vs-2019/test-explorer-playlist-xml-file.png)

Benzer bir şekilde bir çalma listesi oluşturmak isterseniz, MSTest için aşağıdaki biçimi kullanın.
```xml
<Playlist Version="2.0">
    <Rule Name="Includes" Match="Any">
        <Property Name="Trait" Value="SchemaUpdateBasic" />
    </Rule>
</Playlist>
```

XUnit için aşağıdaki biçimi kullanın. Adınız ve ile arasında bir boşluk olduğundan emin olun `TestCategory` `[Value]` .
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

[Gruplar](#test-explorer-groups) , test Gezgini 'nde nitelik, yığın Izleme, hata Iletisi ve tam ad gibi sütunlar olarak da kullanılabilir. Çoğu sütun varsayılan olarak görünmez ve gördüğünüz sütunları ve görünecekleri sırayı özelleştirebilirsiniz.

![Seçili sütunların bulunduğu bir menüyü ve süresi, nitelikleri ve hata Iletisini içeren bir alt menüyü gösteren Visual Studio Test Gezgini 'nin ekran görüntüsü.](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Test sütunlarını filtreleme, sıralama ve yeniden düzenleme

Sütunlar filtrelenebilir, sıralanabilir ve yeniden düzenlenebilir.
* Belirli nitelikleri filtrelemek için nitelikler sütununun en üstündeki filtre simgesine tıklayın.

  ![Sütun filtresi](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* Sütunların sırasını değiştirmek için, bir sütun başlığına tıklayın ve sola veya sağa sürükleyin.

* Bir sütunu sıralamak için sütun başlığına tıklayın. Her sütun sıralanamaz. Ayrıca, **SHIFT** tuşunu basılı tutarak ve ek bir sütun başlığına tıklayarak ikincil bir sütuna göre sıralama yapabilirsiniz.

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
|**Project**|Test projesi adlarını eşleşmeler için arar.|
|**Hata Iletisi**|Eşleşmeler için başarısız Onaylamalar tarafından döndürülen Kullanıcı tanımlı hata iletilerini arar.|
|**Dosya yolu**|Test kaynak dosyalarının tam dosya adını eşleşmeler için arar.|
|**Tam nitelikli ad**|Test ad alanları, sınıflar ve yöntemlerin tam adını eşleşmeler için arar.|
|**Çıktı**|Standart çıkış (STDOUT) veya standart hata (stderr) ile yazılan Kullanıcı tanımlı hata iletilerini arar. Çıkış mesajlarını belirten sözdizimi, birim test çerçevesi tarafından tanımlanır.|
|**Sonucu**|Test Gezgini kategori adlarını eşleşmeler için arar: **başarısız testler**, **Atlanan testler**, **başarılı testler**.|
::: moniker-end
::: moniker range=">=vs-2019"
|Leyicisini|Açıklama|
|-|-----------------|
|**Durum**|Test Gezgini kategori adlarını eşleşmeler için arar: **başarısız testler**, **Atlanan testler**, **başarılı testler**.|
|**Lerdir**|Hem nitelik kategorisini hem de eşleşme değerlerini arar. Nitelik kategorilerini ve değerlerini belirten sözdizimi, birim test çerçevesi tarafından tanımlanır.|
|**Tam nitelikli ad**|Test ad alanları, sınıflar ve yöntemlerin tam adını eşleşmeler için arar.|
|**Project**|Test projesi adlarını eşleşmeler için arar.|
|**Hedef Çerçeve**|Test Gezgini kategori adlarını eşleşmeler için arar: **başarısız testler**, **Atlanan testler**, **başarılı testler**.|
|**Ad Alanı**|Test ad alanlarını eşleşmeler için arar.|
|**Sınıf**|Test sınıfları adlarını eşleşmeler için arar.|
::: moniker-end

Bir filtrenin sonuçlarının bir alt kümesini dışlamak için aşağıdaki sözdizimini kullanın:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Örneğin, adında " `FullName:"MyClass" - FullName:"PerfTest"` PerfTest" da dahil olan testler hariç, adında "MyClass" içeren tüm testleri döndürür.

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

Testler test Gezgini 'nden, test üzerindeki kod düzenleyicisine sağ tıklayıp **Test Çalıştır** ' ı seçerek veya Visual Studio 'Daki varsayılan [Test Gezgini kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) kullanılarak çalıştırılabilir. Bazı kısayollar bağlam tabanlıdır. Bu, imlecinizin kod düzenleyicisinde olduğu yere göre testleri çalıştırdıkları veya [hata ayıkladıkları](../test/debug-unit-tests-with-test-explorer.md) anlamına gelir. İmlecinizin bir test yöntemi içindeyse, bu test yöntemi çalışır. İmlecinizin sınıf düzeyi ise, o sınıftaki tüm testler çalıştırılır. Bu, ad alanı düzeyi için de aynıdır.

|Sık kullanılan komutlar| Klavye Kısayolları|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**CTRL** + **R**, **CTRL** + **T**|
|TestExplorer.RunAllTestsInContext|**CTRL** + **R**, **T**|
|TestExplorer.RunAllTests|**CTRL** + **R**, **A**|
|TestExplorer.RepeatLastRun|**CTRL** + **R**, **L**|

> [!NOTE]
> Testler yalnızca soyut sınıflarda tanımlandığından ve örneklenmemiş olduğundan, bir testi soyut bir sınıfta çalıştıramazsınız. Testleri soyut sınıflarda çalıştırmak için soyut sınıftan türeten bir sınıf oluşturun.

::: moniker range=">=vs-2019"
## <a name="test-audio-cue"></a>Test ses destesi
Test Gezgini, bir test çalıştırması tamamlandığında bir ses oynayabilir. İki ses vardır: Test çalıştırmasının tüm geçen testlerle başarılı olduğunu belirten bir ses ve Test çalıştırmasının en az bir başarısız test ile tamamlandığını belirten ikinci bir ses. Bu sesleri varsayılan Windows 10 Ses iletişim kutusunda ayarlayabilirsiniz. Bu özellik Visual Studio 2019 güncelleştirme 16,9 Preview 3 ' te başlayarak kullanılabilir.

1. Varsayılan Windows 10 Ses iletişim kutusunu açın.
2. **Sesler** sekmesine gidin.
3. **Microsoft Visual Studio** kategorisini bulun. Önceden ayarlanmış sesleri seçmek veya kendi ses dosyanıza gitmek için **test çalıştırması başarılı** veya **test çalıştırması başarısız** sesler ' i seçin.  
![Windows 10 Ses iletişim kutusu](../test/media/default-windows-10-sound-dialog.png)

::: moniker-end
## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testlerinde hata ayıklama](../test/debug-unit-tests-with-test-explorer.md)
- [64 bitlik bir işlem olarak birim testi çalıştırma](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Test Gezgini Hakkında SSS](test-explorer-faq.md)
