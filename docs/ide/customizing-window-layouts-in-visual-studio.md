---
title: Pencere düzenlerini özelleştirme
description: Çeşitli geliştirme iş akışları için en iyi şekilde çalışan düzenler oluşturmak için Windows'un sergilemektedir özelliklerini özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: conceptual
f1_keywords:
- vs.windows
- vs.environment
helpviewer_keywords:
- windows [Visual Studio], managing
- custom window configurations
- layout [Visual Studio], window management
- document windows [Visual Studio]
- interface modes
- AutoHide windows
- MDI, window interface modes
- multiple monitors
- Tabbed Document mode
- debug mode
- custom layouts
ms.assetid: 7517ff13-76de-4ecf-9c1b-eb9b7ff4d718
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be11db364d0505833e722d3db308b41a18ccbb9d
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308135"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Visual Studio'da pencere düzenlerini özelleştirme

Bu Visual Studio, çeşitli geliştirme iş akışları için en iyi şekilde çalışan pencere düzenleri oluşturmak için pencerelerin konumunu, boyutunu ve davranışını özelleştirebilirsiniz. Düzeni özelleştirin, IDE bunu anımsar. Örneğin, **Çözüm Gezgini'nin** yerleştirme konumunu değiştirir ve sonra Visual Studio'ı kapatırsanız, Visual Studio'ı bir sonraki açsanız, başka bir bilgisayarda çalışıyorsanız bile, **Çözüm Gezgini** aynı konuma yer açılır.

Ayrıca özel bir düzeni adlandırarak kaydedebilir ve ardından tek bir komutla düzenler arasında geçiş de sabilirsiniz. Örneğin, düzenlemek için bir düzen ve hata ayıklama için bir düzen oluşturabilir ve Pencere Düzeni Uygula menü komutunu kullanarak bu düzen  >  **arasında geçiş** yapabilirsiniz.

## <a name="tool-and-document-windows"></a>Araç ve belge pencereleri

IDE'nin iki temel pencere türü vardır: *araç pencereleri* ve *belge pencereleri.* Araç pencereleri **Çözüm Gezgini**, **Sunucu Gezgini**, **Çıkış Penceresi**, Hata Listesi, tasarımcılar, hata ayıklayıcı pencereleri ve daha pek çok şey içerir. Belge pencereleri kaynak kod dosyaları, rastgele metin dosyaları, yapılandırma dosyaları ve daha pek çok şey içerir. Araç pencereleri başlık çubuğu tarafından yeniden boyutlandırılabilir ve sürüklenebilirsiniz. Belge pencereleri sekmeleri tarafından sürüklenebilirsiniz. Pencerede diğer seçenekleri ayarlamak için sekmeye veya başlık çubuğuna sağ tıklayın.

Pencere **menüsünde** IDE'de pencereleri yerleştirme, kayan ve gizleme seçenekleri gösterilir. İlgili pencereye yönelik ek seçenekleri görmek için bir pencere sekmesine veya başlık çubuğuna sağ tıklayın. Belirli araç pencerelerinin birden fazla örneğini aynı anda görüntüebilirsiniz. Örneğin, birden fazla web tarayıcısı penceresi görüntüleyebilirsiniz ve Pencere menüsünde Yeni Pencere'yi seçerek bazı araç **pencerelerinin ek** **örneklerini oluşturabilirsiniz.**

### <a name="split-windows"></a>Bölme pencereleri

Bir belgede aynı anda iki konumu görüntülemeniz veya düzenlemeniz gerekirken pencereleri bölebilirsiniz. Belgenizi bağımsız olarak kaydıran iki bölüme  bölmek için Pencere menüsünde **Böl'e** tıklayın. Tek **görünümü geri yüklemek** için Pencere **menüsünde** Bölmeyi Kaldır'a tıklayın.

### <a name="tabs"></a>Sekmeler

Düzeninizi birkaç farklı şekilde düzenlemek için sekmeleri kullanabilirsiniz. Örneğin, dosyayı açmadan bir dosyanın önizlemesini düzenleyicide görüntüebilirsiniz, sekmelerinizi gruplayabilirsiniz ve daha fazlasını yapın.

#### <a name="preview-tab-document-windows"></a>Önizleme sekmesi (belge pencereleri)

Önizleme **sekmesinde** dosyaları açmadan düzenleyicide görüntüleyebilirsiniz. Dosyaları önizlemek için önizlemeyi **seçerek Çözüm Gezgini,** dosyalara adımlarken hata ayıklama sırasında Tanıma Git ile ve bir aramanın sonuçlarına göz atarak. Önizleme dosyaları, belge sekmesinin sağ tarafındaki bir sekmede görünür. Dosyada değişiklik yaptıysanız veya Aç'ı seçerseniz dosya düzenlemek için **açılır.**

::: moniker range=">=vs-2019"

#### <a name="vertical-document-tabs"></a>Dikey belge sekmeleri

**[Sürüm 16.4'te](/visualstudio/releases/2019/release-notes-v16.4/)** yeni eklendi: Visual Studio 2019 sürüm 16.4 sürümünde en önemli özellik isteklerinden [birini,](https://developercommunity.visualstudio.com/idea/467369/vertical-group-tab.html)dikey belge sekmelerini ekledik. Artık belge sekmelerinizi düzenleyicinizin sol veya sağ tarafındaki dikey listede yönetebilirsiniz.

Dikey belge sekmelerini aşağıdaki yollarla uygulayabilirsiniz:

- Menü   >  **çubuğundan Araçlar**  >  **Seçenekler** Ortam  >  **Sekmeleri ve Windows'u** seçin. Ardından, Sekme **düzeni ayarla denetiminde,** açılan **listeden Üst,** **Sol** **veya** Sağ'ı seçin.

- Bir sekmeye sağ tıklayın, Sekme Düzenini **Ayarla'yı ve** ardından Sol veya **Sağ'ı** **seçin.** (Sekmeleri varsayılan konumlarına geri dönmek için **Üst'i seçin.)**

    :::image type="content" source="./media/vs-2019/vertical-tabs.gif" alt-text="Dikey belge sekmelerini uygulamalı olarak gösteren animasyon":::

::: moniker-end

#### <a name="tab-groups"></a>Sekme grupları

Sekme grupları, IDE'de iki veya daha fazla açık belgeyle çalışırken sınırlı çalışma alanını yönetme becerinizi genişletmektedir. Birden çok belge penceresini ve araç pencerelerini dikey veya yatay sekme grupları halinde düzenleyebilir ve belgeleri bir sekme grubundan diğerine karıştırabilirsiniz.

### <a name="toolbars"></a>Araç Çubukları

Araç çubuklarını istediğiniz yere sürükleyerek veya Özelleştir iletişim kutusunu **kullanarak ayarlayabilirsiniz.** Araç çubuklarını konumlandırma ve özelleştirme hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Menüleri ve araç çubuklarını özelleştirme.](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)

## <a name="arrange-and-dock-windows"></a>Pencereleri düzenleme ve yerleştirme

IDE pencere çerçevesi içinde bir *konuma ve* boyuta sahip olması için bir belge penceresi veya araç penceresi yerleştirebilirsiniz. Ayrıca, IDE'nin dışında ayrı bir kayan pencere olarak da konumlandırabilirsiniz.

Bir araç penceresini IDE çerçevesinin herhangi bir yerine yerleştirebilirsiniz. Ayrıca, bazı araç pencerelerini düzenleyici çerçevesinde sekmeli pencereler olarak yerleştirebilirsiniz. Ayrıca, belge pencerelerini düzenleyici çerçevesinde sabitleyebilirsiniz ve bunları sekme sırasına göre geçerli konumlarına sabitleyebilirsiniz.

IDE'nin üzerinde veya dışında bir rafta birlikte *kayan* birden çok pencere de yerleştirebilir. Araç pencereleri gizli veya simge durumuna küçültülmüş de olabilir.

Pencereleri aşağıdaki yollarla ayarlayabilirsiniz:

- Belge pencerelerini sekmenin sol tarafından sabitleyebilirsiniz.

- Düzenleme çerçevesine sekmeyle yerleştirme pencereleri.

- Araç pencerelerini IDE'de bir çerçevenin kenarına yerleştirme.

- IDE üzerinde veya dışında kayan belge veya araç pencereleri.

- IDE'nin kenarı boyunca araç pencerelerini gizle.

- Pencereleri farklı monitörlerde görüntüleme.

- Pencere yerleştirmeyi varsayılan düzene veya kaydedilmiş bir özel düzene sıfırlayın.

Araç ve belge pencerelerini düzenlemek için imlecinizi bir pencerenin başlık çubuğuna yerleştirip istediğiniz yere sürükleyebilirsiniz. Alternatif olarak, bağlam menüsünü kullanmak için pencerenin başlık çubuğuna sağ tıklayabilirsiniz veya Pencere menüsündeki komutları **kullanabilirsiniz.**

### <a name="dock-windows"></a>Pencereleri yerleştirme

Bir araç penceresinin başlık çubuğuna veya belge penceresinin sekmesine tıklar ve sürüklerken kılavuz baklavası görüntülenir. Sürükleme işlemi sırasında, fare imleci baklavanın oklarından birinin üzerine geldiğinde, fare düğmesini şimdi serbest bıraktığınızda pencerenin nereye yerleştir olacağını gösteren gölgeli bir alan görüntülenir.

Yerleştirilebilir bir pencereyi yerine yaslamadan taşımak için, pencereyi **sürüklerken Ctrl** tuşuna basın.

Bir araç penceresini veya belge penceresini en son yerleştirilen konuma geri dönmek için, pencerenin başlık çubuğuna veya sekmesine çift tıklarken **Ctrl** tuşuna basın.

Aşağıdaki çizimde, belge pencereleri için kılavuz baklavası gösterilmiştir ve bu yalnızca düzenleme çerçevesine yerleştirilene kadardır:

![Belge penceresi kılavuzu baklava](../ide/media/documentwindowguidediamonds.png)

Araç pencereleri, IDE'de veya düzenleme çerçevesi içinde bir çerçevenin bir tarafına sabit olabilir. Bir araç penceresini başka bir konuma sürükleyerek pencereyi kolayca yeniden çıkarmanıza yardımcı olacak bir kılavuz baklavası görüntülenir.

![Araç Penceresi Kılavuzu Elmasları](../ide/media/vs10guidediamond.png)

Aşağıdaki **çizimde Çözüm Gezgini** gölgeli alan tarafından sınırlan yeni bir konuma yerleştirildikleri gösterilmiştir:

![Yeni Çözüm Gezgini yerleştirme](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Araç pencerelerini kapatma ve otomatik gizleme

Başlık çubuğunun sağ üst köşesindeki **X** tarak bir araç penceresini kapatabilirsiniz. Pencereyi yeniden açmak için klavye kısayolunu veya menü komutunu kullanın. Araç pencereleri, otomatik gizleme *adlı bir özelliği* destekler ve bu da farklı bir pencereyi kullanırsanız pencerenin aradan kaymasına neden olur. Bir pencere otomatik olarak gösterilirse, adı IDE'nin sonundaki bir sekmede görünür. Pencereyi yeniden kullanmak için sekmenin üzerine gelin, böylece pencere tekrar görünüme kayar.

![Otomatik gizle](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Otomatik gizlemenin araç pencerelerinde tek tek mi yoksa yerleştirilen  gruplar olarak mı olduğunu ayarlamak için Otomatik Gizle düğmesinin etkin araç pencerelerini yalnızca Seçenekler iletişim kutusunda etkileyeceğini seçin **veya** temizleyin. Daha fazla bilgi için [bkz. Genel, Ortam, Seçenekler iletişim kutusu.](../ide/reference/general-environment-options-dialog-box.md)

> [!NOTE]
> Otomatik gizlemenin etkin olduğu araç pencereleri, pencere odakta olduğunda geçici olarak görünüme kayar. Pencereyi yeniden gizlemek için geçerli pencerenin dışında bir öğe seçin. Pencere odağı kaybettiği zaman tekrar görünümden çıkar.

### <a name="use-a-second-monitor"></a>İkinci bir izleyici kullanma

İkinci bir izleyiciniz varsa ve işletim sisteminiz bunu destekliyorsa, hangi izleyicinin bir pencere görüntüleyeni seçebilirsiniz. Hatta birden çok pencereyi diğer monitörlerde *sallar içinde* birlikte gruplayabilirsiniz.

> [!TIP]
> Birden çok örnek oluşturabilir Çözüm Gezgini **başka** bir izleyiciye taşıma. Pencereye sağ tıklayın ve Yeni **Görünüm'Çözüm Gezgini seçin.** **Ctrl** tuşunu seçerken çift tıklayarak tüm pencereleri özgün monitöre geri dönabilirsiniz.

### <a name="reset-name-and-switch-between-window-layouts"></a>Pencere düzenlerini sıfırlama, adı ve değiştirme

Pencere Düzenini Sıfırla komutunu kullanarak IDE'i ayarlar koleksiyonunuz için özgün pencere **düzenine geri dönebilirsiniz.** Bu komutu çalıştırarak aşağıdaki eylemler gerçekleşir:

- Tüm pencereler varsayılan konumlarına taşınır.

- Varsayılan pencere düzeninde kapatılan Pencereler kapatılır.

- Varsayılan pencere düzeninde açık olan Windows açılır.

### <a name="create-and-save-custom-layouts"></a>Özel düzenler oluşturma ve kaydetme

Visual Studio 10 adede kadar özel pencere düzeni kaydetmenizi ve bu düzenleri hızlıca değiştirmenizi sağlar. Aşağıdaki adımlar, hem yuvalı hem de kayan araç pencereleriyle birden çok izleyiciden yararlanan özel düzenleri oluşturma, kaydetme, çağırma ve yönetmeyi gösterir.

İlk olarak, her biri farklı bir en iyi düzende olan iki projesi olan bir test çözümü oluşturun.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Ui projesi oluşturma ve düzeni özelleştirme

::: moniker range="vs-2017"

1. Yeni bir C# **WPF Uygulaması projesi** oluşturun. Bu projede bir kullanıcı arabirimi geliştirdiğini düşünün. Tasarımcı penceresi için alanı en üst düzeye çıkarmak ve diğer araç pencerelerini yolundan çıkarmak istediğiniz.

::: moniker-end

::: moniker range=">=vs-2019"

1. Yeni bir C# **WPF Uygulaması projesi** oluşturun. Bu projede bir kullanıcı arabirimi geliştirdiğini düşünün. Tasarımcı penceresi için alanı en üst düzeye çıkarmak ve diğer araç pencerelerini yolundan çıkarmak istediğiniz.

::: moniker-end

2. Birden çok izleyiciniz varsa, Çözüm Gezgini **penceresini** ve **Özellikler penceresini** ikinci izleyicinize çekin. Tek bir izleyici sisteminde tasarımcı dışındaki tüm pencereleri kapatmayı deneyin.

3. Araç Kutusu penceresini görüntülemek için **Ctrl** + **Alt** + **X** **tuşlarına** basın. Pencere yerleştirildi ise, konumlandırmak istediğiniz bir yere kayar şekilde sürükleyin.

4. Hata ayıklama moduna Visual Studio **F5'e** basın. Otomatikler, Çağrı **Yığını** ve **Çıkış** hata ayıklama **pencerelerinin** konumunu istediğiniz şekilde ayarlayın. Oluşturmak istediğiniz düzen hem düzenleme moduna hem de hata ayıklama moduna uygulanır.

5. Düzenleri hem hata ayıklama modunda hem de düzenleme modunda istediğiniz gibi olduğunda, Pencere Düzeni'ne **Pencere**  >  **Kaydet'i seçin.** Bu düzeni "Tasarımcı" olarak arayın.

     Yeni düzeninize, ayrılmış Ctrl Alt **1...0** listesinden bir sonraki klavye +  + **kısayolu atanmıştır.**

#### <a name="create-a-database-project-and-layout"></a>Veritabanı projesi ve düzeni oluşturma

1. Çözüme **yeni SQL Server Veritabanı** projesi ekleyin.

2. içinde yeni projeye sağ tıklayın ve **Çözüm Gezgini'de** **görüntüle'yi Nesne Gezgini.** Bu, **veritabanı SQL Server Nesne Gezgini** tablolara, görünümlere ve diğer nesnelere erişmenize olanak sağlayan genel görünüm penceresini görüntüler. Bu pencereyi kayan bir şekilde ya da yerleştirildi olarak bırakın. Diğer araç pencerelerini istediğiniz şekilde ayarlayın. Daha fazla gerçekçilik için gerçek bir veritabanı eklemeniz gerekir, ancak bu izlenecek yol için gerekli değildir.

3. Düzeniniz istediğiniz gibi olduğunda, ana menüden Pencere Kaydet Pencere  >  **Düzeni'ne tıklayın.** Bu düzeni "DB Projesi" olarak arayın. (Bu proje için hata ayıklama modu düzeninden rahatsız olmayacaksınız.)

#### <a name="switch-between-the-layouts"></a>Düzenler arasında geçiş

Düzenler arasında geçiş yapmak için klavye kısayollarını kullanın veya ana menüden Pencere Pencere **Düzeni**  >  **Uygula'ya tıklayın.**

![Pencere düzenini uygula menüsü](../ide/media/vs2015_applywindowlayout.png)

Ui düzenini uygulamadan sonra, düzenin hem düzenleme modunda hem de hata ayıklama modunda nasıl korunacaklarına dikkat edin.

İş yerinde çoklu monitör kurulumunuz ve evde tek bir monitör dizüstü bilgisayarınız varsa, her makine için iyileştirilmiş düzenler oluşturabilirsiniz.

> [!NOTE]
> Tek monitörlü bir sisteme çok monitörlü bir düzen uygulayacaksanız, ikinci monitöre yerleştiren kayan pencereler artık tek monitörlü Visual Studio gizlenir. Alt + Tab tuşlarına basarak bu pencereleri **öne getirebilirsiniz.** Daha sonra birden Visual Studio izleyici ile pencereyi açarsanız, düzeni yeniden uygulayarak pencereleri belirtilen konumlara geri yükleyebilirsiniz.

#### <a name="manage-and-roam-your-layouts"></a>Düzenlerinizi yönetme ve dolaştırma

Windows Pencere Düzenlerini Yönet'i seçerek özel düzeninizi kaldırabilir,  >  **yeniden adlandırabilirsiniz veya yeniden sıraabilirsiniz.** Bir düzeni taşısanız, anahtar bağlaması otomatik olarak listede yeni konumu yansıtacak şekilde ayarlanır. Bağlamalar başka şekilde değiştirilemez ve bu nedenle aynı anda en fazla 10 düzen depolarsınız.

![Pencere düzenlerini yönetme](../ide/media/managewindowlayouts.png)

Hangi klavye kısayolunu hangi düzene atandığı kendinize anımsatacak şekilde Pencere **Düzeni**  >  **Uygula'yı seçin.**

Bu düzenler otomatik olarak farklı Visual Studio ve ayrı makinelerde Blend örnekleri arasında ve herhangi bir Express yayından diğer Express kuruluşlarına dolar. Ancak düzenler Visual Studio, Blend ve Express üzerinde dolanmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl olur: IDE'de hareket etme](../ide/how-to-move-around-in-the-visual-studio-ide.md)
