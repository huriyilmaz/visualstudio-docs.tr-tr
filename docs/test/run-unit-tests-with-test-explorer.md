---
title: Test Gezgini ile birim testleri çalıştırma
description: Visual Studio ' de test Gezgini ile testlerin nasıl çalıştırılacağını öğrenin. Bu konu, derleme sonrasında otomatik test çalıştırmalarını etkinleştirme, test sonuçlarını görüntüleme, test listesini gruplandırma ve filtreleme, çalma listeleri oluşturma ve test kısayollarını kullanma konularını ele alır.
ms.date: 12/16/2021
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 1ba7d81c3d408ade040dc5c763d7e07c3c0e1f73
ms.sourcegitcommit: d3578c384959f1b76dd06fb4b5d075fb052f8c69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2021
ms.locfileid: "135375344"
---
# <a name="run-unit-tests-with-test-explorer"></a>Test Gezgini ile birim testleri çalıştırma

Visual Studio veya üçüncü taraf birim testi projelerinden birim testlerini çalıştırmak için Test gezgini 'ni kullanın. Testleri kategoriler halinde gruplamak, test listesini filtrelemek ve testlerin çalma listelerini oluşturmak, kaydetmek ve çalıştırmak için test Gezgini ' ni de kullanabilirsiniz. ayrıca, Test gezgini 'ni kullanarak [birim testlerinde hata ayıklayın](../test/debug-unit-tests-with-test-explorer.md) ve Visual Studio Enterprise ' de [kod kapsamını analiz](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)edebilirsiniz.

**Test Gezgini** , bir çözümde ve üretim kodu projelerinin parçası olan test sınıflarından birden çok test projesinin testlerini çalıştırabilir. Test projeleri, farklı birim testi çerçeveleri kullanabilir. Test altındaki kod .NET için yazıldığında, hedef kodun dilinden bağımsız olarak, test projesi de .NET ' i hedefleyen herhangi bir dilde yazılabilir. Yerel C/C++ kod projeleri bir C++ birim testi çerçevesi kullanılarak test edilmiş olmalıdır.

## <a name="build-your-test-project"></a>Test projenizi derleme

Visual Studio çözümünüzde ayarlanmış bir test projeniz yoksa, önce bir test projesi oluşturmanız ve derlemeniz gerekir.

- [Birim testini kullanmaya başlama (.NET)](../test/getting-started-with-unit-testing.md)
- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

Visual Studio hem yönetilen hem de yerel kod için Microsoft birim testi çerçevelerini içerir. Ancak, test Gezgini, test Gezgini bağdaştırıcısı uygulayan herhangi bir birim test çerçevesini de çalıştırabilir. Üçüncü taraf birim testi çerçevelerini yükleme hakkında daha fazla bilgi için bkz. [üçüncü taraf birim testi çerçeveleri yükleme](../test/install-third-party-unit-test-frameworks.md)

## <a name="run-tests-in-test-explorer"></a>Testleri test Gezgini 'nde Çalıştır

Test projesi oluşturduğunuzda, testler test Gezgini 'nde görünür. test gezgini görünür değilse, Visual Studio menüsünde **Test** ' i seçin, **Windows**' i seçin ve ardından **Test gezgini** ' ni seçin (veya **Ctrl**  +  **E**, **T**' ye basın).

::: moniker range="vs-2017"
![Birim test Gezgini](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range="vs-2019"
![Test Gezgini](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Test Gezgini](../test/media/vs-2022/test-explorer-17-0.png)
::: moniker-end

::: moniker range="vs-2017"
Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, test Gezgini sonuçları **başarısız testler**, **başarılı** testler, **Atlanan** testler ve **çalıştırma** testleri için varsayılan gruplar halinde görüntüler. Test Gezgini 'nin testlerinizi gruplandırma yöntemini değiştirebilirsiniz.
::: moniker-end
::: moniker range=">=vs-2019"
testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, Test gezgini sonuçları **Project**, **ad alanı** ve **sınıf** için varsayılan gruplandırmada görüntüler. Test Gezgini 'nin testlerinizi gruplandırma şeklini değiştirebilirsiniz.
::: moniker-end

**Test Gezgini** araç çubuğundan testleri bulma, düzenleme ve çalıştırma işinin çoğunu yapabilirsiniz.

::: moniker range="vs-2017"
![Testleri test Gezgini araç çubuğundan Çalıştır](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range="vs-2019"
![Testleri test Gezgini araç çubuğundan Çalıştır](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end
::: moniker range=">=vs-2022"
:::image type="content" source="../test/media/vs-2022/test-explorer-toolbar-diagram-17-0.png" alt-text="Testleri test Gezgini araç çubuğundan Çalıştır":::
::: moniker-end

### <a name="run-tests"></a>Testleri çalıştırma

::: moniker range="vs-2017"
Çözümdeki tüm testleri, bir gruptaki tüm testleri veya seçtiğiniz bir test kümesini çalıştırabilirsiniz. Aşağıdakilerden birini yapın:

- Bir Çözümdeki tüm testleri çalıştırmak için **Tümünü Çalıştır** ' ı seçin (veya **CTRL** + **R**, **V** tuşlarına basın).

- Varsayılan bir gruptaki tüm testleri çalıştırmak için **Çalıştır** ' ı seçin ve ardından menüdeki grubu seçin.

- Çalıştırmak istediğiniz bireysel testleri seçin, seçili bir test için sağ tıklama menüsünü açın ve ardından **Seçili Testleri Çalıştır** ' ı seçin (veya **CTRL** + **R**, **T**' ye basın).

- Bireysel testlerin herhangi bir sırada çalıştırılmasını önleyen bir bağımlılığı yoksa, paralel test yürütme özelliğini ![Visual Studio test gezgini araç çubuğundaki paralel test yürütme geçiş düğmesi ekran görüntüsü. Bu düğme seçildiğinde, testler paralel olarak çalışır.](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğme. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.

**Test Gezgini** penceresinin en üstündeki **geçiş/başarısızlık çubuğu** , testler çalışırken hareketlendirilir. Test çalıştırmasının sonunda, herhangi bir test başarısız olursa tüm testler başarılı veya Red durumunda, **geçiş/başarısızlık çubuğu** yeşile dönüşür.
::: moniker-end
::: moniker range=">=vs-2019"
Çözümdeki tüm testleri, bir gruptaki tüm testleri veya seçtiğiniz bir test kümesini çalıştırabilirsiniz. Aşağıdakilerden birini yapın:

- Bir Çözümdeki tüm testleri çalıştırmak için **Tümünü Çalıştır** simgesini seçin (veya **CTRL** + **R**, **V** tuşlarına basın).

- Varsayılan bir gruptaki tüm testleri çalıştırmak için **Çalıştır** simgesini seçin ve sonra menüdeki grubu seçin.

- Çalıştırmak istediğiniz bireysel testleri seçin, seçili bir test için sağ tıklama menüsünü açın ve ardından **Seçili Testleri Çalıştır** ' ı seçin (veya **CTRL** + **R**, **T**' ye basın).

- Bireysel testlerin herhangi bir sırada çalıştırılmasını engelleyen bir bağımlılığı yoksa, araç çubuğunun ayarlar menüsünde paralel test yürütme ' yi açın. Bu, tüm testleri çalıştırmak için harcanan süreyi önemli ölçüde azaltabilir.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Her derlemeden sonra Testleri Çalıştır
::: moniker range="vs-2017"
|Düğme|Description|
|-|-|
|![Derlemeden sonra Çalıştır](../test/media/ute_runafterbuild_btn.png)|Her yerel derlemeden sonra birim testlerinizi çalıştırmak için standart menüdeki **Test** ' i seçin ve ardından **Test Gezgini** araç çubuğunda **derlemeden sonra Testleri Çalıştır** ' ı seçin.|

> [!NOTE]
> her derlemeden sonra birim testlerini çalıştırmak için Visual Studio 2017 Enterprise veya Visual Studio 2019 gerekir. Visual Studio 2019 ' de Community ve Professional ve Enterprise bulunur.
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
::: moniker range="vs-2019"
![Test yürütme ayrıntıları](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Test yürütme ayrıntıları](../test/media/vs-2022/test-explorer-details.png)
::: moniker-end

Test ayrıntıları bölmesi aşağıdaki bilgileri görüntüler:

- Test yönteminin kaynak dosya adı ve satır numarası.

- Testin durumu.

- Test yönteminin çalışması için geçen geçen süre.

Test başarısız olursa, Ayrıntılar bölmesi şunları da görüntüler:

- Test için birim test çerçevesi tarafından döndürülen ileti.

- Testin başarısız olduğu zamanda yığın izlemesi.

### <a name="view-the-source-code-of-a-test-method"></a>Test yönteminin kaynak kodunu görüntüleme

Visual Studio düzenleyicisinde bir test yönteminin kaynak kodunu göstermek için, testi seçin ve sağ tıklama menüsünde **testi aç** ' ı seçin (veya **F12** tuşuna basın).

## <a name="group-and-filter-the-test-list"></a>Test listesini gruplandırma ve filtreleme

Test Gezgini, testlerinizi önceden tanımlanmış kategoriler halinde gruplandırmanızı sağlar. Test Gezgini 'nde çalışan çoğu birim testi çerçevesi, testlerinizi gruplandırmak için kendi kategorilerinizi ve kategori/değer çiftlerini tanımlamanızı sağlar. Test özelliklerine karşılık dizeleri eşleştirerek, testlerin listesini de filtreleyebilirsiniz.

### <a name="group-tests-in-the-test-list"></a>Test listesindeki testleri gruplandırma

::: moniker range="vs-2017"
Testlerin düzenlenme şeklini değiştirmek için **Gruplandırma ölçütü** düğme ![ Test Gezgini grubu düğmesinin yanındaki aşağı oku seçin ](../test/media/ute_groupby_btn.png) ve yeni bir gruplandırma ölçütü seçin.

![Test Gezgini 'nde kategoriye göre grup testleri](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range="vs-2019"
Test Gezgini, testlerinizi bir hiyerarşiye gruplandırmanıza olanak tanır. varsayılan hiyerarşi gruplandırması **Project**, **ad alanı** ve daha sonra **sınıftır**. Testlerin düzenlenme şeklini değiştirmek için **grupla** düğmesine tıklayın ![ Test Explorer grubu düğmesini seçin ](../test/media/ute_groupby_btn.png) ve yeni bir gruplandırma ölçütü seçin.

![Test Gezgini 'nde kategoriye göre grup testleri](../test/media/vs-2019/test-explorer-groupby-162.png)

Hiyerarşi ve gruplama düzeylerini **tanımlayabilir ve sonra** tercih ettiğiniz sırada grupla seçeneklerini belirleyerek **sınıfa** göre gruplandırabilirsiniz.

![bir bölmede bir test hiyerarşisini gösteren ve diğer içindeki sınıf ve durum seçenekleri işaretli olan grup ölçütü menüsündeki Visual Studio test gezgini ekran görüntüsü.](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end
::: moniker range=">=vs-2022"
Test Gezgini, testlerinizi bir hiyerarşiye gruplandırmanıza olanak tanır. varsayılan hiyerarşi gruplandırması **Project**, **ad alanı** ve daha sonra **sınıftır**. Testlerin düzenlenme şeklini değiştirmek için **grupla** düğmesine tıklayın ![ Test Explorer grubu düğmesini seçin ](../test/media/ute_groupby_btn.png) ve yeni bir gruplandırma ölçütü seçin.

![Test Gezgini 'nde kategoriye göre grup testleri](../test/media/vs-2022/test-explorer-groupby-17-0.png)

Hiyerarşi ve gruplama düzeylerini **tanımlayabilir ve sonra** tercih ettiğiniz sırada grupla seçeneklerini belirleyerek **sınıfa** göre gruplandırabilirsiniz.

![bir bölmede bir test hiyerarşisini gösteren ve diğer içindeki sınıf ve durum seçenekleri işaretli olan grup ölçütü menüsündeki Visual Studio test gezgini ekran görüntüsü.](../test/media/vs-2022/test-explorer-groupby-state-17-0.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Test Gezgini grupları

::: moniker range="vs-2017"
|Grup|Açıklama|
|-|-----------------|
|**Süre**|Gruplar yürütme süresine göre test ediyor: **Hızlı,** **Orta** ve **Yavaş.**|
|**Sonuç**|Testleri yürütme sonuçlarına göre **gruplar: Başarısız Testler**, **Atlanan Testler**, Başarılı **Testler**.|
|**Özellik**|Gruplar, tanımladığınız kategori/değer çiftleri tarafından test edildi. Nitelik kategorilerini ve değerlerini belirtme söz dizimi birim testi çerçevesi tarafından tanımlanır.|
|**Project**|Grupların testini projelerin adına göre sınar.|
::: moniker-end
::: moniker range=">=vs-2019"
|Grup|Açıklama|
|-|-----------------|
|**Süre**|Testleri yürütme süresine göre gruplar: **Hızlı,** **Orta** ve **Yavaş.**|
|**Durum**|Testleri yürütme sonuçlarına göre gruplar: **Başarısız Testler,** **Atlanan Testler**, **Başarılı Testler**, **Çalıştırılamadı**|
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

**Bir çalma listesine testler eklemek için Test** Gezgini'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde Çalma Listesine Ekle'yi **ve** ardından testleri eklemek istediğiniz oynatma listesini seçin.

**Bir çalma listesi açmak** için, Visual Studio menüsünden **Test** Oynatma Listesi'ne tıklayın ve son kullanılan çalma listeleri listesinden birini seçin veya çalma listesinin adını ve konumunu belirtmek için Çalma Listesini Aç'ı >  seçin. 

Tek tek testlerin herhangi bir sırada çalıştırılamalarını engelleyen bağımlılıkları yoksa, ile paralel test yürütmeyi ![Test Gezgini araç çubuğundaki Paralel test yürütme iki durumlu Visual Studio düğmesinin ekran görüntüsü.](../test/media/ute_parallelicon-small.png) araç çubuğundaki iki durumlu düğmeyi seçin. Bu, tüm testleri çalıştırmak için gereken zamanı önemli ölçüde azaltabilirsiniz.
::: moniker-end
::: moniker range="vs-2019"
Grup olarak çalıştırmak veya görüntülemek istediğiniz testlerin listesini oluşturabilir ve kaydedebilirsiniz. Bir oynatma listesi seçerek, listede yer alan testler yeni bir Test Gezgini sekmesinde görüntülenir. Birden fazla oynatma listesine test ekleyebilirsiniz.

**Oynatma listesi oluşturmak için** Test Gezgini'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde Oynatma Listesine Ekle Yeni **Oynatma Listesi'ne**  >  **tıklayın.**

![Oynatma listesi oluşturma](../test/media/vs-2019/test-explorer-playlist-16-2.png)

Oynatma listesi yeni bir Test Gezgini sekmesinde açılır. Bu oynatma listesini bir kez kullanabilir ve sonra  atabilir veya oynatma listesi penceresinin araç çubuğundaki Kaydet düğmesine tıklayabilirsiniz ve ardından çalma listesini kaydetmek için bir ad ve konum seçin.

![Oynatma listesi ayrı test gezgini sekmesinde açılır](../test/media/vs-2019/test-explorer-playlist-tab-16-7.png)

**Oynatma listesi oluşturmak için** Test Gezgini'nde bir veya daha fazla test seçin. Sağ tıklayın ve Oynatma Listesine **Ekle Yeni oynatma listesi'ne**  >  **tıklayın.**

**Bir oynatma listesi açmak** için, araç çubuğundaki oynatma Visual Studio simgesini seçin ve menüden daha önce kaydedilmiş bir oynatma listesi dosyasını seçin.

**Oynatma listesini düzenlemek için** herhangi bir teste sağ tıklar ve menü seçeneklerini kullanarak oynatma listesine ekleyebilir veya oynatma listesinden kaldırabilirsiniz.

2019 Visual Studio 16.7 sürümünden başlayarak araç çubuğunda **düzenle** düğmesini seçebilirsiniz. Hangi testlerin dahil olduğunu ve oynatma listesine dahil edilen testleri gösteren testlerinin yanında onay kutuları görüntülenir. Grupları dilediğiniz şekilde düzenleyin.

![Oynatma Listesini Düzenle düğmesi](../test/media/vs-2019/test-explorer-playlist-edit-16-7.png)

Hiyerarşide üst grupların kutularını da işaretlerini veya işaretini kaldırabilirsiniz. Bu eylem, o gruptaki testler temel alınarak çalma listesini her zaman güncelleye bir dinamik çalma listesi oluşturur. Örneğin, bir sınıfın yanına bir onay işareti eklersiniz, bu sınıftan eklenen tüm testler bu çalma listesinin bir parçası olur. Bu sınıftan bir testi silersiniz, bu test oynatma listesinden kaldırılır. Araç çubuğundaki Kaydet düğmesiyle oynatma listesini kaydederek ve diskiniz üzerinde oluşturulan *.playlist* dosyasını açarak kurallar hakkında daha fazla bilgi edinebilirsiniz. Bu dosyada oynatma listesinin tüm kuralları ve tek tek testleri listele.

![Çalma listesi xml dosyası](../test/media/vs-2019/test-explorer-playlist-xml-file.png)

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

::: moniker range=">=vs-2022"
Grup olarak çalıştırmak veya görüntülemek istediğiniz testlerin listesini oluşturabilir ve kaydedebilirsiniz. Bir oynatma listesi seçerek, listede yer alan testler yeni bir Test Gezgini sekmesinde görüntülenir. Birden fazla oynatma listesine test ekleyebilirsiniz.

**Oynatma listesi oluşturmak için** Test Gezgini'nde bir veya daha fazla test seçin. Sağ tıklama menüsünde Oynatma Listesine Ekle Yeni **Oynatma Listesi'ne**  >  **tıklayın.**

![Oynatma listesi oluşturma](../test/media/vs-2022/test-explorer-playlist-17-0.png)

Oynatma listesi yeni bir Test Gezgini sekmesinde açılır. Bu oynatma listesini bir kez kullanabilir ve sonra  atabilir veya oynatma listesi penceresinin araç çubuğundaki Kaydet düğmesine tıklayabilirsiniz ve ardından çalma listesini kaydetmek için bir ad ve konum seçin.

![Oynatma listesi ayrı test gezgini sekmesinde açılır](../test/media/vs-2022/test-explorer-playlist-tab-17-0.png)

**Oynatma listesi oluşturmak için** Test Gezgini'nde bir veya daha fazla test seçin. Sağ tıklayın ve Oynatma Listesine **Ekle Yeni oynatma listesi'ne**  >  **tıklayın.**

**Bir oynatma listesi açmak** için, araç çubuğundaki oynatma Visual Studio simgesini seçin ve menüden daha önce kaydedilmiş bir oynatma listesi dosyasını seçin.

**Oynatma listesini düzenlemek için** herhangi bir teste sağ tıklar ve menü seçeneklerini kullanarak oynatma listesine ekleyebilir veya oynatma listesinden kaldırabilirsiniz.

2019 Visual Studio 16.7 sürümünden başlayarak araç çubuğunda **düzenle** düğmesini seçebilirsiniz. Hangi testlerin dahil olduğunu ve oynatma listesine dahil edilen testleri gösteren testlerinin yanında onay kutuları görüntülenir. Grupları dilediğiniz şekilde düzenleyin.

![Oynatma Listesini Düzenle düğmesi](../test/media/vs-2022/test-explorer-playlist-edit-17-0.png)

Hiyerarşide üst grupların kutularını da işaretlerini veya işaretini kaldırabilirsiniz. Bu eylem, o gruptaki testler temel alınarak çalma listesini her zaman güncelleye bir dinamik çalma listesi oluşturur. Örneğin, bir sınıfın yanına bir onay işareti eklersiniz, bu sınıftan eklenen tüm testler bu çalma listesinin bir parçası olur. Bu sınıftan bir testi silersiniz, bu test oynatma listesinden kaldırılır. Araç çubuğundaki Kaydet düğmesiyle oynatma listesini kaydederek ve diskiniz üzerinde oluşturulan *.playlist* dosyasını açarak kurallar hakkında daha fazla bilgi edinebilirsiniz. Bu dosyada oynatma listesinin tüm kuralları ve tek tek testleri listele.

![Çalma listesi xml dosyası](../test/media/vs-2022/test-explorer-playlist-xml-file.png)

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

::: moniker range="vs-2019"
### <a name="test-explorer-columns"></a>Test Gezgini sütunları

Gruplar [Ayrıca](#test-explorer-groups) Nitelik, Yığın İzleme, Hata İletisi ve Tam Ad ile birlikte Test Gezgini'nde sütun olarak da kullanılabilir. Çoğu sütun varsayılan olarak görünür değildir ve hangi sütunları gördüğünüzi ve hangi sırada görüntüle olduklarını özelleştirebilirsiniz.

![Sütunlar'ın Visual Studio ve Süre, Nitelikler ve Hata İletisi'nin seçili olduğu bir alt menüyü gösteren Test Gezgini'nin ekran görüntüsü.](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Test sütunlarını filtreleme, sıralama ve yeniden düzenleme

Sütunlar filtrelenmiş, sıralanmış ve yeniden düzenlenmiş olabilir.
* Belirli niteliklere filtrelemek için Nitelikler sütununu en üst köşesindeki filtre simgesine tıklayın.

  ![Sütun filtresi](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* Sütunların sıralamalarını değiştirmek için bir sütun başlığına tıklayın ve bunu sola veya sağa sürükleyin.

* Bir sütunu sıralamak için sütun başlığına tıklayın. Her sütun sıralanamaz. Shift tuşunu basılı tutarak ve ek bir sütun **başlığına** tıklayarak ikincil sütuna göre de sıraabilirsiniz.

  ![Sütun sıralama](../test/media/vs-2019/test-explorer-sort-column-16-2.png)
::: moniker-end
::: moniker range=">=vs-2022"
### <a name="test-explorer-columns"></a>Test Gezgini sütunları

Gruplar [Ayrıca](#test-explorer-groups) Nitelik, Yığın İzleme, Hata İletisi ve Tam Ad ile birlikte Test Gezgini'nde sütun olarak da kullanılabilir. Çoğu sütun varsayılan olarak görünür değildir ve hangi sütunları gördüğünüzi ve hangi sırada görüntüle olduklarını özelleştirebilirsiniz.

![Sütunlar'ın Visual Studio ve Süre, Nitelikler ve Hata İletisi'nin seçili olduğu bir alt menüyü gösteren Test Gezgini'nin ekran görüntüsü.](../test/media/vs-2022/test-explorer-columns-17-0.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Test sütunlarını filtreleme, sıralama ve yeniden düzenleme

Sütunlar filtrelenmiş, sıralanmış ve yeniden düzenlenmiş olabilir.
* Belirli niteliklere filtrelemek için Nitelikler sütununu en üst köşesindeki filtre simgesine tıklayın.

  ![Sütun filtresi](../test/media/vs-2022/test-explorer-filter-column-17-0.png)

* Sütunların sıralamalarını değiştirmek için bir sütun başlığına tıklayın ve bunu sola veya sağa sürükleyin.

* Bir sütunu sıralamak için sütun başlığına tıklayın. Her sütun sıralanamaz. Shift tuşunu basılı tutarak ve ek bir sütun **başlığına** tıklayarak ikincil sütuna göre de sıraabilirsiniz.

  ![Sütun sıralama](../test/media/vs-2022/test-explorer-sort-column-17-0.png)
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
::: moniker range="vs-2019"
![Test Gezgini'nde testleri filtreleme](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Test Gezgini'nde testleri filtreleme](../test/media/vs-2022/test-explorer-search-filter-17-0.png)
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
|**Çıkış**|Standart çıkışa (stdout) veya standart hataya (stderr) yazılan kullanıcı tanımlı hata iletilerini arar. Çıkış iletilerini belirtmek için söz dizimi birim testi çerçevesi tarafından tanımlanır.|
|**Sonuç**|Test Gezgini kategori adlarını eşleşmeler için arar: **Başarısız Testler,** **Atlanan Testler**, **Başarılı Testler.**|
::: moniker-end
::: moniker range=">=vs-2019"
|Niteleyici|Description|
|-|-----------------|
|**Durum**|Test Gezgini kategori adlarını eşleşmeler için arar: **Başarısız Testler,** **Atlanan Testler**, **Başarılı Testler.**|
|**Özellik**|Eşleşmeler için hem nitelik kategorisini hem de değeri arar. Nitelik kategorilerini ve değerlerini belirtme söz dizimi birim testi çerçevesi tarafından tanımlanır.|
|**Tam Ad**|Eşleşmeler için test ad alanlarının, sınıfların ve yöntemlerin tam adını arar.|
|**Project**|Test projesi adlarını eşleşmeler için arar.|
|**Hedef Çerçeve**|Test Gezgini kategori adlarını eşleşmeler için arar: **Başarısız Testler,** **Atlanan Testler**, **Başarılı Testler.**|
|**Ad Alanı**|Test ad alanlarında eşleşmeleri arar.|
|**Sınıf**|Test sınıfları adlarını eşleşmeler için arar.|
::: moniker-end

Filtre sonuçlarının bir alt kümesini dışlamak için aşağıdaki söz dizimlerini kullanın:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Örneğin, adlarına "PerfTest" de içeren testler dışında, adlarına `FullName:"MyClass" - FullName:"PerfTest"` "MyClass" içeren tüm testleri döndürür.

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

* Test Gezgini'ne sağ tıklayın ve Seçili testler **için Kod Kapsamı Çözümleme'yi seçin**

::: moniker-end

Kod **Kapsamı Sonuçları** penceresi satır, işlev, sınıf, ad alanı ve modül tarafından yapılan ürün kodu bloklarının yüzdesini görüntüler.

Daha fazla bilgi için [bkz. Test edilen koda ne kadar kod olduğunu belirlemek için kod kapsamı kullanma.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

## <a name="test-shortcuts"></a>Test kısayolları

Testler, testte kod düzenleyicisine sağ tıklar ve Testi çalıştır'ı seçerek veya test gezgininde varsayılan [Test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) Gezgini kısayollarını Visual Studio.  Kısayollardan bazıları bağlam tabanlıdır. Bu, imlecinizin kod [düzenleyicisinde bulunduğu yere](../test/debug-unit-tests-with-test-explorer.md) göre testleri çalıştıracakları veya hata ayıklayacakları anlamına gelir. İmleciniz bir test yönteminin içinde yer alırsa bu test yöntemi çalışır. İmleciniz sınıf düzeyinde ise, o sınıftaki tüm testler çalıştır. Bu, ad alanı düzeyi için de aynıdır.

|Sık Kullanılan Komutlar| Klavye Kısayolları|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**Ctrl** + **R**, **Ctrl** + **T**|
|TestExplorer.RunAllTestsInContext|**Ctrl** + **R,** **T**|
|TestExplorer.RunAllTests|**Ctrl** + **R,** **A**|
|TestExplorer.RepeatLastRun|**Ctrl** + **R,** **L**|

> [!NOTE]
> Testler yalnızca soyut sınıflarda tanımlandığı ve örneklanmamış olduğu için bir testi soyut sınıfta çalıştıraabilirsiniz. Soyut sınıflarda testleri çalıştırmak için soyut sınıftan türetilen bir sınıf oluşturun.

::: moniker range=">=vs-2019"
## <a name="test-audio-cue"></a>Test ses ipucu

Test Gezgini, bir test çalıştırması tamamlandığında ses çalabilirsiniz. İki ses var: Test çalıştırması başarılı oldu ve test çalıştırması başarılı oldu ve test çalıştırması en az bir başarısız testle tamamlandı. Bu sesleri varsayılan 11 ses Windows ayarlayabilirsiniz. Bu özellik, Visual Studio 2019 Güncelleştirme 16.9 Önizleme 3'te başlayarak kullanılabilir.

1. Varsayılan 11 Windows iletişim kutusunu açın.
2. Sesler **sekmesine** gidin.
3. Microsoft Visual Studio **bulun.** Önceden ayarlanmış **sesleri seçmek veya kendi ses** **dosyanıza** göz atmak için Test Çalıştırması Başarılı veya Test Çalıştırması Başarısız seslerini seçin.  
![Windows 10 iletişim kutusu](../test/media/default-windows-11-sound-dialog.png)

::: moniker-end
## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu birim testi](../test/unit-test-your-code.md)
- [Test Gezgini ile birim testlerinde hata ayıklama](../test/debug-unit-tests-with-test-explorer.md)
- [64 bitlik bir işlem olarak birim testi çalıştırma](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Test Gezgini Hakkında SSS](test-explorer-faq.md)
