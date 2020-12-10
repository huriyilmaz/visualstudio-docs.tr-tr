---
title: Test Gezgini ile birim testleri çalıştırma
description: Visual Studio 'da test Gezgini ile testlerin nasıl çalıştırılacağını öğrenin. Bu konu, derleme sonrasında otomatik test çalıştırmalarını etkinleştirme, test sonuçlarını görüntüleme, test listesini gruplandırma ve filtreleme, çalma listeleri oluşturma ve test kısayollarını kullanma konularını ele alır.
ms.date: 07/14/2020
ms.topic: how-to
f1_keywords:
- vs.unittesting.testexplorer.overview
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3633f3084b875974adac17fc27e7ec7a695ed91
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996389"
---
# <a name="run-unit-tests-with-test-explorer"></a>Test Gezgini ile birim testleri çalıştırma

Visual Studio 'dan veya üçüncü taraf birim testi projelerinden birim testlerini çalıştırmak için test Gezgini 'ni kullanın. Testleri kategoriler halinde gruplamak, test listesini filtrelemek ve testlerin çalma listelerini oluşturmak, kaydetmek ve çalıştırmak için test Gezgini ' ni de kullanabilirsiniz. Ayrıca kod kapsamını ve [hata ayıklama birim testlerini](../test/debug-unit-tests-with-test-explorer.md)analiz edebilirsiniz.

**Test Gezgini** , bir çözümde ve üretim kodu projelerinin parçası olan test sınıflarından birden çok test projesinin testlerini çalıştırabilir. Test projeleri, farklı birim testi çerçeveleri kullanabilir. Test altındaki kod .NET için yazıldığında, hedef kodun dilinden bağımsız olarak, test projesi de .NET ' i hedefleyen herhangi bir dilde yazılabilir. Yerel C/C++ kod projeleri bir C++ birim testi çerçevesi kullanılarak test edilmiş olmalıdır.

## <a name="build-your-test-project"></a>Test projenizi derleme

Visual Studio çözümünüzde ayarlanmış bir test projeniz yoksa, önce bir test projesi oluşturmanız ve derlemeniz gerekir.

- [Birim testini kullanmaya başlama (.NET)](../test/getting-started-with-unit-testing.md)
- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

Visual Studio hem yönetilen hem de yerel kod için Microsoft birim testi çerçeveleri içerir. Ancak, test Gezgini, test Gezgini bağdaştırıcısı uygulayan herhangi bir birim test çerçevesini de çalıştırabilir. Üçüncü taraf birim testi çerçevelerini yükleme hakkında daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçeveleri yükleme](../test/install-third-party-unit-test-frameworks.md)

## <a name="run-tests-in-test-explorer"></a>Testleri test Gezgini 'nde Çalıştır

Test projesi oluşturduğunuzda, testler test Gezgini 'nde görünür. Test Gezgini görünür değilse, Visual Studio menüsünden **Test** ' i seçin, **Windows**' u ve ardından **Test Gezgini**' ni seçin.

::: moniker range="vs-2017"
![Birim test Gezgini](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test Gezgini](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, test Gezgini sonuçları **başarısız testler**, **başarılı** testler, **Atlanan** testler ve **çalıştırma** testleri için varsayılan gruplar halinde görüntüler. Test Gezgini 'nin testlerinizi gruplandırma yöntemini değiştirebilirsiniz.
::: moniker-end
::: moniker range=">=vs-2019"
Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, test Gezgini sonuçları varsayılan bir **Proje**, **ad alanı** ve **sınıf** gruplandırmasında görüntüler. Test Gezgini 'nin testlerinizi gruplandırma şeklini değiştirebilirsiniz.
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

Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, test Gezgini sonuçları **başarısız testler**, **başarılı** testler, **Atlanan testler** ve **çalıştırma testleri** gruplarında görüntüler. Test Gezgini 'nin alt veya tarafındaki Ayrıntılar bölmesi, Test çalıştırmasının bir özetini görüntüler.

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
Testlerin düzenlenme şeklini değiştirmek için **Gruplandırma ölçütü** düğme ![ Test Gezgini grubu düğmesinin yanındaki aşağı oku seçin ](../test/media/ute_groupby_btn.png) ve yeni bir gruplandırma ölçütü seçin.

![Test Gezgini 'nde kategoriye göre grup testleri](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
Test Gezgini, testlerinizi bir hiyerarşiye gruplandırmanıza olanak tanır. Varsayılan hiyerarşi gruplandırması **Proje**, **ad alanı** ve daha sonra **sınıftır**. Testlerin düzenlenme şeklini değiştirmek için **grupla** düğmesine tıklayın ![ Test Explorer grubu düğmesini seçin ](../test/media/ute_groupby_btn.png) ve yeni bir gruplandırma ölçütü seçin.

![Test Gezgini 'nde kategoriye göre grup testleri](../test/media/vs-2019/test-explorer-groupby-162.png)

Hiyerarşi ve gruplama düzeylerini **tanımlayabilir ve sonra** tercih ettiğiniz sırada grupla seçeneklerini belirleyerek **sınıfa** göre gruplandırabilirsiniz.

![Duruma göre Gruplandır ve sonra sınıfı](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Test Gezgini grupları

::: moniker range="vs-2017"
|Grup|Açıklama|
|-|-----------------|
|**Süre**|Yürütme zamanına göre test grupları: **hızlı**, **Orta** ve **yavaş**.|
|**Sonucu**|Testleri yürütme sonuçlarına göre gruplandırır: **başarısız testler**, **Atlanan testler**, **başarılı testler**.|
|**Lerdir**|Tanımladığınız kategori/değer çiftlerine göre test grupları. Nitelik kategorilerini ve değerlerini belirten sözdizimi, birim test çerçevesi tarafından tanımlanır.|
|**Project**|Projeler adına göre test grupları.|
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

Bireysel testlerin herhangi bir sırada çalıştırılmasını önleyen bir bağımlılığı yoksa, paralel test yürütme özelliğini ![UTE&#95;parallelicon&#45;küçük](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğme. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.
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

Benzer bir şekilde bir çalma listesi oluşturmak istiyorsanız aşağıdaki biçimi kullanın. Adınız ve ile arasında bir boşluk olduğundan emin olun `TestCategory` `[Value]` .
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

![Duruma göre Gruplandır ve sonra sınıfı](../test/media/vs-2019/test-explorer-columns-16-2.png)

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

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testlerinde hata ayıklama](../test/debug-unit-tests-with-test-explorer.md)
- [64 bitlik bir işlem olarak birim testi çalıştırma](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Test Gezgini Hakkında SSS](test-explorer-faq.md)
