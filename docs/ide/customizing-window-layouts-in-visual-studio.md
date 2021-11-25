---
title: Pencere düzenlerini özelleştirme
description: Çeşitli geliştirme iş akışları için en iyi şekilde çalışan düzenler oluşturmak için Windows'un sergilemektedir özelliklerini özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/24/2021
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 636f80024d87a07aa78723e9905ddaca21e5702d
ms.sourcegitcommit: 5af130d3ff64b71d415819e42f4f2efb2ae36a6a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "133117541"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Visual Studio'da pencere düzenlerini özelleştirme

Bu Visual Studio, çeşitli geliştirme iş akışları için en iyi şekilde çalışan pencere düzenleri oluşturmak için pencerelerin konumunu, boyutunu ve davranışını özelleştirebilirsiniz. Düzeni özelleştirin, IDE bunu anımsar. Örneğin, **Çözüm Gezgini'nin** yerleştirme konumunu değiştirir ve sonra Visual Studio'ı kapatırsanız, Visual Studio'ı bir sonraki açsanız, başka bir bilgisayarda çalışıyorsanız **bile,** Çözüm Gezgini aynı konuma yer açılır.

Ayrıca özel bir düzeni adlandırarak kaydedebilir ve ardından tek bir komutla düzenler arasında geçiş de sabilirsiniz. Örneğin, düzenlemek için bir düzen ve hata ayıklama için bir düzen oluşturabilir ve Pencere Düzeni Uygula menü komutunu kullanarak bu düzen  >  **arasında geçiş** yapabilirsiniz.

## <a name="tool-and-document-windows"></a>Araç ve belge pencereleri

IDE'nin iki temel pencere türü vardır: *araç pencereleri* ve *belge pencereleri.* Araç pencereleri **Çözüm Gezgini,** **Sunucu Gezgini**, **Çıkış Penceresi** **,** Hata Listesi, tasarımcılar, hata ayıklayıcı pencereleri ve daha pek çok şey içerir. Belge pencereleri kaynak kod dosyaları, rastgele metin dosyaları, yapılandırma dosyaları ve daha pek çok şey içerir. Araç pencereleri başlık çubuğuyla yeniden boyutlandırılabilir ve sürüklenebilirsiniz. Belge pencereleri sekmeleri tarafından sürüklenebilirsiniz. Pencerede diğer seçenekleri ayarlamak için sekmeye veya başlık çubuğuna sağ tıklayın.

Pencere **menüsünde** IDE'de pencereleri yerleştirme, kayan ve gizleme seçenekleri gösterilir. İlgili pencereye yönelik ek seçenekleri görmek için bir pencere sekmesine veya başlık çubuğuna sağ tıklayın. Belirli araç pencerelerinin birden fazla örneğini aynı anda görüntüebilirsiniz. Örneğin, birden fazla web tarayıcısı penceresi görüntüleyebilirsiniz ve Pencere menüsünde Yeni Pencere'yi seçerek bazı araç **pencerelerinin ek** **örneklerini oluşturabilirsiniz.**

### <a name="split-windows"></a>Bölme pencereleri

Bir belgede aynı anda iki konumu görüntülemeniz veya düzenlemeniz gerekirken pencereleri bölebilirsiniz. Belgenizi bağımsız olarak kaydıran iki bölüme  bölmek için Pencere menüsünde **Böl'e** tıklayın. Tek **görünümü geri yüklemek** için Pencere **menüsünde** Bölmeyi Kaldır'a tıklayın.

### <a name="tabs"></a>Sekmeler

Düzeninizi birkaç farklı şekilde düzenlemek için sekmeleri kullanabilirsiniz. Örneğin, dosyayı açmadan bir dosyanın önizlemesini düzenleyicide görüntüebilirsiniz, sekmelerinizi gruplayabilirsiniz ve daha fazlasını yapın.

#### <a name="preview-tab-document-windows"></a>Önizleme sekmesi (belge pencereleri)

Önizleme **sekmesinde** dosyaları açmadan düzenleyicide görüntüleyebilirsiniz. Dosyaları önizlemek için önizlemeyi **seçerek Çözüm Gezgini,** dosyalara adımlarken hata ayıklama sırasında Tanıma Git ile ve bir aramanın sonuçlarına göz atarak. Önizleme dosyaları, belge sekmesinin sağ tarafındaki bir sekmede görünür. Dosyayı değiştirir veya Aç'ı seçerseniz dosya düzenlemek için **açılır.**

::: moniker range=">=vs-2019"

#### <a name="vertical-document-tabs"></a>Dikey belge sekmeleri

**[2019 Visual Studio 16.4](/visualstudio/releases/2019/release-notes-v16.4/)** ve sonraki sürümlerde yeni eklendi: En önemli özellik isteklerinden birini, dikey [belge sekmelerini ekledik.](https://developercommunity.visualstudio.com/idea/467369/vertical-group-tab.html) Artık belge sekmelerinizi düzenleyicinizin sol veya sağ tarafındaki dikey listede yönetebilirsiniz.

Dikey belge sekmelerini aşağıdaki yollarla uygulayabilirsiniz:

- Araçlar **Seçenekler**  >  **Ortam**  >  **Sekmeleri'Windows**  >   çubuğundan sekmeleri seçin. Ardından, Sekme **düzeni ayarla denetiminde,** açılan **listeden Üst,** **Sol** **veya** Sağ'ı seçin.

- Bir sekmeye sağ tıklayın, Sekme Düzenini **Ayarla'yı ve** ardından Sol veya **Sağ'ı** **seçin.** (Sekmeleri varsayılan konumlarına geri dönmek için **Üst'i seçin.)**

    :::image type="content" source="./media/vs-2019/vertical-tabs.gif" alt-text="Dikey belge sekmelerini uygulamalı olarak gösteren animasyon":::

::: moniker-end

::: moniker range="vs-2022"

#### <a name="color-document-tabs"></a>Belge sekmelerini renklendirme

**[2022 Visual Studio 17.0](/visualstudio/releases/2022/release-notes)** ve sonraki sürümlerde yeni eklendi: Başka bir en önemli özellik isteği [ekledik, belge sekmelerini renklendirme.](https://devblogs.microsoft.com/visualstudio/personalize-docs/) Artık Düzenleyici'de hem dikey hem de yatay görünümlerde sekmeleri renklendirebilirsiniz.

Aşağıdaki ekran görüntüsünde, dikey görünümde renk sekmelerinin bir örneği görüntülenir:

:::image type="content" source="media/vs-2022/color-tabs-vertical.png" alt-text="Dikey görünümde renk sekmelerinin ekran görüntüsü.":::

Aşağıdaki ekran görüntüsünde, yatay görünümde renk sekmelerinin bir örneği görüntülenir:

:::image type="content" source="media/vs-2022/color-tabs-horizontal.png" alt-text="Yatay görünümde renk sekmelerinin ekran görüntüsü.":::

Renk sekmelerini kullanmak  için Araçlar Seçenekler Ortam Sekmeleri'ne gidin Windows ve ardından belge sekmelerini >  >  > projeye **göre renklendirme'yi seçin.**

::: moniker-end

#### <a name="tab-groups"></a>Sekme grupları

Sekme grupları, IDE'de iki veya daha fazla açık belgeyle çalışırken sınırlı çalışma alanını yönetme becerinizi genişletmektedir. Birden çok belge penceresini ve araç pencerelerini dikey veya yatay sekme grupları halinde düzenleyebilir ve belgeleri bir sekme grubundan diğerine karıştırabilirsiniz.

### <a name="toolbars"></a>Araç Çubukları

Araç çubuklarını istediğiniz yere sürükleyerek veya Özelleştir iletişim kutusunu **kullanarak ayarlayabilirsiniz.** Araç çubuklarını konumlandırma ve özelleştirme hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Menüleri ve araç çubuklarını özelleştirme.](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)

## <a name="arrange-and-dock-windows"></a>Pencereleri düzenleme ve yerleştirme

IDE pencere çerçevesi içinde bir *konuma ve* boyuta sahip olması için bir belge penceresi veya araç penceresi yerleştirebilirsiniz. Ayrıca, IDE'nin dışında ayrı bir kayan pencere olarak da konumlandırabilirsiniz.

Bir araç penceresini IDE çerçevesinin herhangi bir yerine yerleştirebilirsiniz. Ayrıca, bazı araç pencerelerini düzenleyici çerçevesinde sekmeli pencereler olarak yerleştirebilirsiniz. Ayrıca, belge pencerelerini düzenleyici çerçevesinde sabitleyebilirsiniz ve bunları sekme sırasına göre geçerli konumlarına sabitleyebilirsiniz.

IDE'nin üzerinde veya dışında bir *rafta* birlikte kayan birden çok pencere de yerleştirebilir. Araç pencereleri gizli veya simge durumuna küçültülmüş de olabilir.

Pencereleri aşağıdaki yollarla ayarlayabilirsiniz:

- Belge pencerelerini sekmenin sol tarafından sabitleyebilirsiniz.

- Pencereleri düzenleme çerçevesine sekmeyle yerleştirme.

- Araç pencerelerini IDE'de bir çerçevenin kenarına yerleştirme.

- IDE üzerinde veya dışında kayan belge veya araç pencereleri.

- IDE'nin kenarı boyunca araç pencerelerini gizle.

- Pencereleri farklı monitörlerde görüntüleme.

- Pencere yerleşimini varsayılan düzene veya kaydedilmiş bir özel düzene sıfırlayın.

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

![Çözüm Gezgini yeni bir konuma yerleştirme](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Araç pencerelerini kapatma ve otomatik gizleme

Başlık çubuğunun sağ üst köşesindeki **X** tarak bir araç penceresini kapatabilirsiniz. Pencereyi yeniden açmak için klavye kısayolunu veya menü komutunu kullanın. Araç pencereleri, otomatik gizleme *adlı bir özelliği* destekler ve bu da farklı bir pencereyi kullanırsanız pencerenin aradan kaymasına neden olur. Bir pencere otomatik olarak gösterilirse, adı IDE'nin sonundaki bir sekmede görünür. Pencereyi yeniden kullanmak için sekmenin üzerine gelin; böylece pencere tekrar görünüme kayar.

![Otomatik gizle](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Otomatik gizlemenin araç pencerelerinde tek tek mi yoksa yerleştirilen  gruplar olarak mı olduğunu ayarlamak için Otomatik Gizle düğmesinin etkin araç pencerelerini yalnızca Seçenekler iletişim kutusunda etkileyeceğini seçin **veya** temizleyin. Daha fazla bilgi için [bkz. Genel, Ortam, Seçenekler iletişim kutusu.](../ide/reference/general-environment-options-dialog-box.md)

> [!NOTE]
> Otomatik gizlemenin etkin olduğu araç pencereleri, pencere odakta olduğunda geçici olarak görünüme kayar. Pencereyi yeniden gizlemek için geçerli pencerenin dışında bir öğe seçin. Pencere odağı kaybettiği zaman tekrar görünümden çıkar.

### <a name="use-a-second-monitor"></a>İkinci bir izleyici kullanma

İkinci bir izleyiciniz varsa ve işletim sisteminiz bunu destekliyorsa, hangi izleyicinin bir pencere görüntüleyeni seçebilirsiniz. Hatta birden çok pencereyi diğer monitörlerde *sallar içinde* birlikte gruplayabilirsiniz.

> [!TIP]
> Birden çok örnek oluşturabilir Çözüm Gezgini **başka** bir izleyiciye taşıma. Pencereye sağ tıklayın ve Yeni **Görünüm'Çözüm Gezgini seçin.** **CTRL** tuşunu seçerken, tüm pencereleri geri ' ye çift tıklayarak özgün monitöre döndürebilirsiniz.

### <a name="reset-name-and-switch-between-window-layouts"></a>Pencere düzenleri arasında sıfırlama, adlandırma ve geçiş yapma

**Pencere mizanpajını Sıfırla** komutunu kullanarak, ayarlar KOLEKSIYONUNUZ için IDE 'yi özgün pencere düzenine döndürebilirsiniz. Bu komutu çalıştırdığınızda, aşağıdaki eylemler gerçekleşir:

- Tüm pencereler varsayılan konumlarına taşınır.

- varsayılan pencere düzeninde kapatılan Windows kapalıdır.

- varsayılan pencere düzeninde açık olan Windows açılır.

### <a name="create-and-save-custom-layouts"></a>Özel düzenler oluşturma ve kaydetme

Visual Studio, en fazla 10 özel pencere düzenini kaydetmenizi ve aralarında hızlıca geçiş yapmanızı sağlar. Aşağıdaki adımlarda, yerleşik ve kayan araç pencereleri ile birden çok izleyiciden faydalanan özel düzenleri oluşturma, kaydetme, çağırma ve yönetme işlemleri gösterilmektedir.

İlk olarak, her biri ayrı bir en uygun düzene sahip iki projesi olan bir test çözümü oluşturun.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>UI projesi oluşturma ve düzeni özelleştirme

::: moniker range="vs-2017"

1. Yeni bir C# **WPF uygulaması** projesi oluşturun. bu projede, bir kullanıcı arabirimi geliştirirsiniz Imagine. Tasarımcı penceresinin alanını en üst düzeye çıkarmak ve diğer araç pencerelerini bu şekilde taşımak istiyorsunuz.

::: moniker-end

::: moniker range=">=vs-2019"

1. Yeni bir C# **WPF uygulaması** projesi oluşturun. bu projede, bir kullanıcı arabirimi geliştirirsiniz Imagine. Tasarımcı penceresinin alanını en üst düzeye çıkarmak ve diğer araç pencerelerini bu şekilde taşımak istiyorsunuz.

::: moniker-end

2. Birden çok monitörünüz varsa, **Çözüm Gezgini** penceresini ve **Özellikler** penceresini ikinci monitörünüze çekin. Tek bir izleme sisteminde, tasarımcı hariç tüm pencereleri kapatmayı deneyin.

3.  +  + **Araç kutusu** penceresini göstermek için Ctrl alt **X** tuşlarına basın. Pencere yerleştirilmişse, yerleştirmek istediğiniz yere kayabilecek şekilde sürükleyin.

4. Visual Studio hata ayıklama moduna koymak için **F5** tuşuna basın. **Oto**, **çağrı yığınının** ve **Çıkış** hata ayıklama pencerelerinin konumunu istediğiniz şekilde ayarlayın. Oluşturmakta olduğunuz düzen hem düzenleme modu hem de hata ayıklama modu için geçerlidir.

5. Hem hata ayıklama modu hem de düzenleme modundaki mizanpajlarınız istediğiniz gibi **olduğunda pencere**  >  **pencere düzenini kaydet**' i seçin. Bu düzeni "tasarımcı" olarak çağırın.

     Yeni mizanpajınızı **CTRL** + **alt** + **1... 0**' ın ayrılmış listesinden sonraki klavye kısayoluna atandığını unutmayın.

#### <a name="create-a-database-project-and-layout"></a>Veritabanı projesi ve düzeni oluşturma

1. çözüme yeni bir **SQL Server veritabanı** projesi ekleyin.

2. **Çözüm Gezgini** yeni projeye sağ tıklayın ve **Nesne Gezgini Görünüm**' ü seçin. bu, veritabanınızdaki tablolara, görünümlere ve diğer nesnelere erişmenizi sağlayan **SQL Server Nesne Gezgini** penceresini görüntüler. Bu pencereyi kayabilir ya da yuvalanmış bırakabilirsiniz. Diğer araç pencerelerini istediğiniz şekilde ayarlayın. Ek realronizme için gerçek bir veritabanı ekleyebilirsiniz, ancak bu izlenecek yol için gerekli değildir.

3. Mizanpajınızı istediğiniz şekilde tercih ettiğinizde, ana menüden **pencere**  >  **pencere yerleşimini kaydet**' i seçin. Bu düzeni "DB Project" olarak çağırın. (Bu proje için bir hata ayıklama modu düzeniyle ilgili değildir.)

#### <a name="switch-between-the-layouts"></a>Düzenler arasında geçiş yapma

Düzenler arasında geçiş yapmak için klavye kısayollarını kullanın veya ana menüden **pencere**  >  **pencere düzeni uygula**' yı seçin.

![Pencere Düzen menüsünü Uygula](../ide/media/vs2015_applywindowlayout.png)

Kullanıcı arabirimi düzeni uygulandıktan sonra, düzenin hem düzenleme modunda hem de hata ayıklama modunda nasıl korundığına göz önünde bulabilirsiniz.

Evde çok sayıda izleme kurulumuna sahipseniz ve tek bir izleme dizüstü bilgisayarı evinizde, her makine için optimize edilmiş düzenler oluşturabilirsiniz.

> [!NOTE]
> tek izlemeli bir sisteme çok monitörlü bir düzen uygularsanız, ikinci monitöre yerleştirdiğiniz kayan pencereler artık Visual Studio penceresinin arkasında gizlenir. **Alt + Tab** tuşlarına basarak bu pencereleri öne çıkarabilirsiniz. daha sonra birden çok izleyiciyle Visual Studio açarsanız, düzeni yeniden uygulayarak pencereleri belirtilen konumlarına geri yükleyebilirsiniz.

#### <a name="manage-and-roam-your-layouts"></a>Düzenlerinizi yönetme ve dolaşımda

**Pencere**  >  **düzenlerini Yönet**' i seçerek özel düzeninizi kaldırabilir, yeniden adlandırabilir veya yeniden sıralayabilirsiniz. Bir düzeni taşırsanız, anahtar bağlama otomatik olarak listedeki yeni konumu yansıtacak şekilde ayarlanır. Bağlamalar başka bir zamanda değiştirilemez ve bu nedenle, aynı anda en fazla 10 düzen saklayabilirsiniz.

![Pencere düzenlerini Yönet](../ide/media/managewindowlayouts.png)

Kendinize hangi klavye kısayolunun atandığını hatırlatmak **için pencere**  >  **pencere düzeni uygula**' yı seçin.

bu düzenler Visual Studio sürümleri arasında ve ayrıca ayrı makinelerde Blend örnekleri arasında ve tüm express sürümlerinden başka bir express kuruluşuna otomatik olarak dolaşımda yapılır. ancak, düzenler Visual Studio, Blend ve Express arasında dolaşımda değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: IDE 'de gezinme](../ide/how-to-move-around-in-the-visual-studio-ide.md)
