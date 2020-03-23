---
title: Pencere düzenlerini özelleştirme
ms.date: 01/23/2017
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1963c76b67eaedea4cdf013739c112275ecffb2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596716"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Visual Studio'da pencere düzenlerini özelleştirme

Visual Studio'da, çeşitli geliştirme iş akışları için en iyi çalışan pencere düzenleri oluşturmak için pencerelerin konumunu, boyutunu ve davranışını özelleştirebilirsiniz. Düzeni özelleştirdiğinizde, IDE bunu hatırlar. Örneğin, **Solution Explorer'ın** yerleştirme konumunu değiştirir ve Visual Studio'yu kapatırsanız, Visual Studio'yu bir sonraki açtığınızda, başka bir bilgisayarda çalışıyor olsanız bile, **Çözüm Gezgini** aynı konuma sabitlenir.

Ayrıca, özel bir düzeni adlandırAbilir ve kaydedebilir ve ardından tek bir komutla düzenler arasında geçiş yapabilirsiniz. Örneğin, düzenleme için bir düzen ve hata ayıklama için bir düzen oluşturabilir ve **Pencere** > **Uygula Penceresi Düzeni** menüsü komutunu kullanarak bunlar arasında geçiş yapabilirsiniz.

## <a name="kinds-of-windows"></a>Pencere çeşitleri

### <a name="tool-and-document-windows"></a>Araç ve belge pencereleri

IDE iki temel pencere türleri, *araç pencereleri* ve *belge pencereleri*vardır. Araç pencereleri **Çözüm Gezgini,** **Sunucu Gezgini,** **Çıkış Penceresi,** **Hata Listesi,** tasarımcılar, hata ayıklama pencereleri ve benzeri içerir. Belge pencereleri kaynak kod dosyaları, rasgele metin dosyaları, config dosyaları ve benzeri içerir. Araç pencereleri yeniden boyutlandırılabilir ve başlık çubuğu tarafından sürüklenebilir. Belge pencereleri sekmeleri tarafından sürüklenebilir. Penceredeki diğer seçenekleri ayarlamak için sekmeye veya başlık çubuğuna sağ tıklayın.

**Pencere** menüsü, IDE'de pencereleri yerleştirme, yüzdürme ve gizleme seçeneklerini gösterir. Belirli bir pencere için ek seçenekleri görmek için pencere sekmesine veya başlık çubuğuna sağ tıklayın. Belirli araç pencerelerinin birden fazla örneğini aynı anda görüntüleyebilirsiniz. Örneğin, birden fazla web tarayıcısı penceresi görüntüleyebilir ve **Pencere** menüsünde **Yeni Pencere'yi** seçerek bazı araç pencerelerinin ek örneklerini oluşturabilirsiniz.

### <a name="preview-tab-document-windows"></a>Önizleme sekmesi (belge pencereleri)

**Önizleme** sekmesinde, dosyaları açmadan düzenleyicide görüntüleyebilirsiniz. **Dosyaları Solution Explorer'da**seçerek , dosyalara adım attığınızda hata ayıklama sırasında, **Tanıma Git**ile ve arama sonuçlarına göz attığınızda önizleyebilirsiniz. Önizleme dosyaları belge sekmesinin sağ tarafındaki bir sekmede iyi görünür. Dosyayı değiştirirseniz veya **Aç'ı**seçerseniz düzenleme için açılır.

### <a name="tab-groups"></a>Sekme grupları

Sekme grupları, IDE'de iki veya daha fazla açık belgeyle çalışırken sınırlı çalışma alanını yönetme yeteneğinizi genişletir. Birden çok belge penceresi ve araç penceresini dikey veya yatay sekme gruplarına dönüştürebilir ve belgeleri bir sekme grubundan diğerine karıştırabilirsiniz.

### <a name="split-windows"></a>Pencereleri bölme

Bir belgede aynı anda iki konumu görüntülemeniz veya değiştirmeniz gerektiğinde, pencereleri bölebilirsiniz. Belgenizi bağımsız olarak kaydırma kkaydırma iki bölüme bölmek için **Pencere** menüsünde **Böl'ü** tıklatın. Tek görünümü geri yüklemek için **Pencere** menüsünde **Bölünmüş'u Kaldır'ı** tıklatın.

### <a name="toolbars"></a>Araç Çubukları

Araç çubukları sürükleyerek veya **Özelleştir** iletişim kutusunu kullanarak düzenlenebilir. Araç çubuklarını nasıl konumlandırıp özelleştirin, nasıl [konumlandırılabilirsiniz: Menüleri ve araç çubuklarını özelleştirin.](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)

## <a name="arrange-and-dock-windows"></a>Pencereleri düzenleme ve yerleştirme

Belge penceresi veya araç *penceresi,* IDE pencere çerçevesi içinde bir konuma ve boyuta sahip olacak şekilde veya IDE'den bağımsız ayrı bir pencere olarak kayan bir belge penceresine sabitlenebilir. Takım pencereleri IDE çerçevesiiçinde herhangi bir yere sabitlenebilir; bazı araç pencereleri düzenleyici çerçevede sekmeli pencereler olarak sabitlenebilir. Belge pencereleri düzenleyici çerçevesi içinde sabitlenebilir ve sekme sırasına göre geçerli konumlarına sabitlenebilir. Birden çok pencereyi bir *saliçinde* veya IDE'nin dışında birlikte yüzdürmek için sabitleyebilirsiniz. Araç pencereleri de gizlenebilir veya en aza indirilebilir.

Pencereleri aşağıdaki şekillerde düzenleyebilirsiniz:

- Belge pencerelerini sekmenin soluna sabitleyin.

- Düzenleme çerçevesine sekme pencereleri yerleştirme.

- Araç pencerelerini IDE'deki bir çerçevenin kenarına sabitleyin.

- Belge veya araç pencerelerini IDE'nin üzerinde veya dışında yüzdürün.

- Takım pencerelerini IDE'nin kenarına gizleyin.

- Pencereleri farklı monitörlerde görüntüleyin.

- Pencere yerleşimini varsayılan düzene veya kaydedilmiş özel düzene sıfırla.

**Pencere** menüsündeki komutları sürükleyerek, komutları kullanarak veya düzenlenecek pencerenin başlık çubuğuna sağ tıklayarak araç ve belge pencerelerini düzenleyin.

### <a name="dock-windows"></a>Dock pencereleri

Bir araç penceresinin başlık çubuğunu veya belge penceresinin sekmesini tıklatıp sürüklediğinızda, bir kılavuz elması görüntülenir. Sürükleme işlemi sırasında, fare imleci elmastaki oklardan birinin üzerindeyken, fare düğmesini şimdi serbest bıraktığınızda pencerenin nereye kenetleneceğini gösteren gölgeli bir alan görüntülenir.

Takılabilir bir pencereyi yerine yapışmadan taşımak için, pencereyi sürüklerken **Ctrl** tuşuna basın.

Bir araç penceresini veya belge penceresini en son sabitlenmiş konumuna döndürmek için, pencerenin başlık çubuğunu veya sekmesini çift tıklatırken **Ctrl** tuşuna basın.

Aşağıdaki resimde, yalnızca düzenleme çerçevesi içinde sabitlenebilen belge pencereleri için kılavuz elması gösterilmektedir:

![Belge pencere kılavuzu elması](../ide/media/documentwindowguidediamonds.png)

Araç pencereleri IDE'deki bir çerçevenin bir tarafına veya düzenleme çerçevesi içinde bağlanabilir. Bir araç penceresini başka bir konuma sürüklediğinizde, pencereyi kolayca yeniden yerleştirmenize yardımcı olmak için kılavuz elması görüntülenir.

![Araç Pencere Kılavuzu Elmaslar](../ide/media/vs10guidediamond.png)

Aşağıdaki resimde **Çözüm Gezgini'nin** mavi gölgeli alan tarafından çizilmiş yeni bir konuma kenetlenmiş olduğu gösterilmektedir:

![Yerleştirme Çözüm Gezgini yeni bir konumda](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Araç pencerelerini kapatma ve otomatik gizleme

Başlık çubuğunun sağ üst kısmındaki **X'i** tıklatarak bir araç penceresini kapatabilirsiniz. Pencereyi yeniden açmak için klavye kısayolu veya menü komutunu kullanın. Araç pencereleri, farklı bir pencere kullandığınızda pencerenin yoldan çıkmasına neden olan *otomatik gizle*adlı bir özelliği destekler. Bir pencere otomatik olarak gizlendiğinde, adı IDE'nin kenarındaki bir sekmede görünür. Pencereyi yeniden kullanmak için, pencerenin görünüme geri kayması için sekmeye işaret edin.

![Otomatik gizleme](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Otomatik gizle'nin araç pencerelerinde tek tek veya sabitlenmiş gruplar olarak çalışıp çalışmadığını ayarlamak için, Otomatik Gizle düğmesini seçin veya temizleyin, yalnızca **Seçenekler** iletişim **kutusundaki etkin araç pencerelerini etkiler.** Daha fazla bilgi için [Genel, Çevre, Seçenekler iletişim kutusuna](../ide/reference/general-environment-options-dialog-box.md)bakın.

> [!NOTE]
> Otomatik gizle özelliği etkin olan araç pencereleri, pencere odaklandığında geçici olarak görünüme kayabilir. Pencereyi yeniden gizlemek için geçerli pencerenin dışında bir öğe seçin. Pencere odağı kaybettiğinde, görünümdışına kayar.

### <a name="specifying-a-second-monitor"></a>İkinci bir monitör belirtme

İkinci bir monitörünüz varsa ve işletim sisteminiz bunu destekliyorsa, hangi monitörün bir pencere yi görüntülediğinizi seçebilirsiniz. Hatta birden fazla pencereyi sallarda diğer *monitörlerde* gruplatabilirsiniz.

> [!TIP]
> **Çözüm Gezgini'nin** birden çok örneği oluşturabilir ve bunları başka bir monitöre taşıyabilirsiniz. Pencereye sağ tıklayın ve **Yeni Çözüm Gezgini Görünümü'ni**seçin. **Ctrl** tuşunu seçerken çift tıklayarak tüm pencereleri orijinal monitöre geri döndürebilirsiniz.

### <a name="reset-name-and-switch-between-window-layouts"></a>Pencere düzenleri arasında sıfırlama, ad ve geçiş

**Pencere Düzenini Sıfırla** komutunu kullanarak ide'yi ayarlar koleksiyonunuzun özgün pencere düzenine döndürebilirsiniz. Bu komutu çalıştırdığınızda, aşağıdaki eylemler oluşur:

- Tüm pencereler varsayılan konumlarına taşınır.

- Varsayılan pencere düzeninde kapalı olan pencereler kapatılır.

- Varsayılan pencere düzeninde açık olan pencereler açılır.

### <a name="create-and-save-custom-layouts"></a>Özel düzenler oluşturma ve kaydetme

Visual Studio, en fazla 10 özel pencere düzeni kaydetmenizi ve aralarında hızlı bir şekilde geçiş yapmanızı sağlar. Aşağıdaki adımlar, hem sabitlenmiş hem de kayan araç pencereleriyle birden çok monitörden yararlanan özel düzenlerin nasıl oluşturulup, kaydedilen, çağırılanın ve yönetilen işeyli düzenleri gösterir.

İlk olarak, her biri farklı bir optimal düzene sahip iki projesi olan bir test çözümü oluşturun.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Bir Eski UI projesi oluşturma ve düzeni özelleştirme

1. Yeni bir C# **WPF App** projesi oluşturun. Bu projede bir kullanıcı arabirimi geliştireceğinizi düşünün. Tasarımcı penceresi için alanı en üst düzeye çıkarmak ve diğer araç pencerelerini yoldan çıkarmak istiyorsunuz.

2. Birden çok monitörünüz varsa, **Çözüm Gezgini** penceresini ve **Özellikler** penceresini ikinci monitörünüze doğru çekin. Tek bir monitör sisteminde, tasarımcı hariç tüm pencereleri kapatmayı deneyin.

3. **Araç Kutusu** penceresini görüntülemek için **Ctrl**+**Alt**+**X** tuşuna basın. Pencere sabitlenmişse, onu konumlandırmak istediğiniz bir yerde yüzecek şekilde sürükleyin.

4. Visual Studio'u hata ayıklama moduna sokmak için **F5** tuşuna basın. **Otomatik Lerin**konumunu, **Arama Yığınını**ve **Çıkış** hata ayıklama pencerelerini istediğiniz şekilde ayarlayın. Oluşturmak üzere olduğunuz düzen hem düzenleme modu na hem de hata ayıklama moduna uygulanır.

5. Hem hata ayıklama modunda hem de düzenleme modundaki düzenleriniz istediğiniz gibi olduğunda, **Pencere** > **Yit'i Kaydet**Düzeni'ni seçin. Bu düzene "Tasarımcı" deyin.

     Yeni düzeninizin **ctrl**+**Alt**+**1...0'ın**ayrılmış listesinden bir sonraki klavye kısayolu atandığını unutmayın.

#### <a name="create-a-database-project-and-layout"></a>Veritabanı projesi ve düzeni oluşturma

1. Çözüme yeni bir **SQL Server Veritabanı** projesi ekleyin.

2. **Çözüm Gezgini'ndeki** yeni projeye sağ tıklayın ve **Nesne Gezgini'nde Görünüm'i**seçin. Bu, veritabanınızdaki tablolara, görünümlere ve diğer nesnelere erişmenizi sağlayan **SQL Server Object Explorer** penceresini görüntüler. Bu pencereyi yüzdürebilir ya da sabitte bırakabilirsiniz. Diğer araç pencerelerini istediğiniz şekilde ayarlayın. Ek gerçekçilik için gerçek bir veritabanı ekleyebilirsiniz, ancak bu izlenme için gerekli değildir.

3. Düzeniniz istediğiniz gibi olduğunda, ana menüden **Pencere** > **Kaydet Pencere Düzeni'ni**seçin. Bu düzene "DB Project" deyin. (Bu proje için hata ayıklama modu düzeniyle uğraşmayız.)

#### <a name="switch-between-the-layouts"></a>Düzenler arasında geçiş

Düzenler arasında geçiş yapmak için klavye kısayollarını kullanın veya ana menüden **Pencere** > **Düzeni Uygula'yı**seçin.

![Pencere düzeni menüsünü uygulama](../ide/media/vs2015_applywindowlayout.png)

UI düzenini uyguladıktan sonra, düzenin hem düzenleme modunda hem de hata ayıklama modunda nasıl korunduğuna dikkat edin.

İş yerinde çoklu monitör kurulumunuz ve evde tek bir monitör dizüstü bilgisayarınız varsa, her makine için optimize edilmiş düzenler oluşturabilirsiniz.

> [!NOTE]
> Tek monitörlü bir sisteme çoklu monitör düzeni uygularsanız, ikinci monitöre yerleştirdiğiniz kayan pencereler artık Visual Studio penceresinin arkasına gizlenir. **Alt + Sekme**tuşuna basarak bu pencereleri öne getirebilirsiniz. Daha sonra Visual Studio'yu birden çok monitörle açarsanız, düzeni yeniden uygulayarak pencereleri belirtilen konumlara geri yükleyebilirsiniz.

#### <a name="manage-and-roam-your-layouts"></a>Düzenlerinizi yönetme ve dolaşımda

**Pencere** > **Yönet Pencere Düzenleri'ni**seçerek özel düzeninizi kaldırabilir, yeniden adlandırabilir veya yeniden sıralayabilirsiniz. Bir düzeni taşırsanız, anahtar bağlama listedeki yeni konumu yansıtacak şekilde otomatik olarak ayarlanır. Bağlamalar başka türlü değiştirilemez ve böylece aynı anda en fazla 10 düzen depolayabilirsiniz.

![Pencere düzenlerini yönetme](../ide/media/managewindowlayouts.png)

Hangi klavye kısayolu nun hangi düzene atandığını kendinize hatırlatmak için **Pencere** > **Düzeni Uygula'yı**seçin.

Bu düzenler, Visual Studio sürümleri arasında ve ayrıca ayrı makinelerdeki Karışım örnekleri arasında ve herhangi bir Express sürümünden başka bir Express kuruluşuna otomatik olarak dolaşır. Ancak, düzenler Visual Studio, Blend ve Express'te gezinmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapilir: IDE'de hareket et](../ide/how-to-move-around-in-the-visual-studio-ide.md)
