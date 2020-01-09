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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596716"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Visual Studio 'da pencere düzenlerini özelleştirme

Visual Studio 'da, Windows 'un konumunu, boyutunu ve davranışını çeşitli geliştirme iş akışları için en iyi şekilde çalışan pencere düzenleri oluşturacak şekilde özelleştirebilirsiniz. Düzen'nı özelleştirdiğinizde, IDE hatırlar. Örneğin, **Çözüm Gezgini** yerleştirme konumunu değiştirir ve ardından Visual Studio 'yu kapatırsanız, başka bir bilgisayarda çalışıyor olsanız bile, Visual Studio 'yu bir sonraki açışınızda **Çözüm Gezgini** aynı konuma yerleştirilmeyecektir.

Ayrıca, özel bir düzen yazıp kaydedebilir ve sonra tek bir komutla birlikte mizanpajlar arasında geçiş yapabilirsiniz. Örneğin, düzenleme için bir düzen ve hata ayıklama için bir düzen oluşturabilir ve pencere **düzeni Düzenle** menü komutunu > **pencereyi** kullanarak bunlar arasında geçiş yapabilirsiniz.

## <a name="kinds-of-windows"></a>Windows türleri

### <a name="tool-and-document-windows"></a>Araç ve belge pencereleri

İki temel pencere türleri, IDE olan *araç pencerelerini* ve *belge windows*. Araç pencereleri **Çözüm Gezgini**, **Sunucu Gezgini**, **Çıkış penceresi**, **hata listesi**, tasarımcılar, hata ayıklayıcı pencereleri vb. içerir. Belge pencereleri, kaynak kodu dosyaları, rastgele metin dosyaları, yapılandırma dosyaları vb. içerir. Araç pencereleri yeniden boyutlandırıldı ve bunların başlık çubuğundaki sürüklediğiniz. Belge pencereleri sekmesine göre sürüklenebilir. penceredeki diğer seçenekleri ayarlamak için sekmeye veya başlık çubuğuna sağ tıklayın.

**Penceresi** kayan ve IDE'de pencereleri gizleme takma seçenekleri menüsü gösterir. Belirli bir pencere için ek seçenekleri görmek üzere bir penceresi sekme veya başlık çubuğunun sağ tıklayın. Aynı anda birden fazla örneğini belirli araç pencereleri görüntüleyebilirsiniz. Örneğin, birden fazla web tarayıcısı penceresi görüntüleyebilir ve bazı araç pencerelerinin ek örneklerini seçerek oluşturabilirsiniz **yeni pencere** üzerinde **penceresi** menüsü.

### <a name="preview-tab-document-windows"></a>Önizleme sekmesini (belge windows)

**Önizleme** sekmesinde, dosyaları açmadan düzenleyicide görüntüleyebilirsiniz. Dosyalara tıkladığınızda hata ayıklama sırasında ve bir aramanın sonuçlarına göz **atarken, dosyaları** **Çözüm Gezgini**seçerek önizleyebilirsiniz, bu dosyaları görüntüleyebilirsiniz. Önizleme dosyalar bir sekmede iyi belge sekmesini sağ tarafında görünür. Dosyayı değiştirirseniz veya **Aç**seçeneğini belirlerseniz dosya düzenlenmek üzere açılır.

### <a name="tab-groups"></a>Sekme grupları

Sekme grupları, IDE 'de iki veya daha fazla açık belge ile çalışırken sınırlı çalışma alanını yönetme yeteneğinizi genişletmenizi sağlar. Birden çok belge Windows ve araç pencerelerini dikey veya yatay sekme grupları halinde düzenleyebilir ve belgeleri bir sekme grubundan diğerine karıştırabilirsiniz.

### <a name="split-windows"></a>Pencereleri Böl

Bir belgede aynı anda iki konuma görüntüleyemez veya varsa, windows bölebilirsiniz. Belgenizi iki bağımsız olarak kaydırma bölümlere ayırmak için tıklayın **bölünmüş** üzerinde **penceresi** menüsü. Tıklayın **Bölmeyi Kaldır** üzerinde **penceresi** tek bir görünüm geri yüklemek için menü.

### <a name="toolbars"></a>Araç Çubukları

Araç çubukları düzenlenmiş sürükleyerek ya da kullanarak **Özelleştir** iletişim kutusu. Araç çubuklarını konumlandırma ve özelleştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: özelleştirme menüleri ve araç çubukları](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arrange-and-dock-windows"></a>Pencereleri yerleştirme ve yerleştirme

Bir belge penceresi veya araç penceresi *yerleştirilebilir*, böylece IDE pencere çerçevesinde bir konum ve boyut, ya da IDE 'den bağımsız ayrı bir pencere olarak taşınabilir. Araç pencerelerini IDE çerçevesinin içinde her yerden yerleştirilmiş olabilir; Bazı araç pencerelerinin Düzenleyicisi çerçevesindeki sekmeli pencerelerin olarak sabitlenebilir. Belge pencereleri Düzenleyicisi çerçevesinde sabitlenebilir ve geçerli konumlarına sekme sırasını sabitlenebilir. Birden çok pencereleri, IDE 'nin üzerinde veya dışında bir şekilde bir araya *getirin* . Araç pencerelerini de gizli veya simge.

Aşağıdaki yollarla windows düzenleyebilirsiniz:

- Belge pencerelerini sekme soluna iyice sabitleyin.

- Düzenleme çerçevesindeki için sekmesinde dock windows.

- Araç Pencereleri IDE içinde bir çerçevenin kenarına yerleştir.

- Belge veya aracı windows üzerinde veya IDE dışında yüzdürün.

- Araç pencerelerini IDE kenarında gizleyin.

- Windows, farklı monitörlerde görüntüleyin.

- Pencere yerleşimini varsayılan düzene veya kaydedilen özel bir düzen sıfırlayın.

Araç ve belge pencerelerini sürükleyerek, **pencere** menüsündeki komutları kullanarak veya düzenlemek üzere pencerenin başlık çubuğuna sağ tıklayarak düzenleyin.

### <a name="dock-windows"></a>Pencereleri yerleştir

' A tıklayın ve bir araç penceresinin başlık çubuğunda veya belge penceresi için sekmesinde sürükleyin, kılavuz elmas görünür. Fare imleci üzerine elmas okları olduğunda sürükleme işlemi sırasında artık fare düğmesini serbest bırakırsanız penceresi nereye yerleştirilir gösteren gölgeli bir alanı görünür.

Bir yerleştirilebilir penceresini yerinde yaslama olmadan taşımak için, pencereyi sürüklerken **CTRL** tuşuna basın.

Bir araç penceresini veya belge penceresini en son yerleştirilen konumuna döndürmek için, pencerenin başlık çubuğunu veya sekmesini çift tıklatırken **CTRL** tuşuna basın.

Aşağıdaki çizimde, yalnızca düzenleme çerçevesinde yuvalanabilir belge windows için kılavuz elmas gösterir:

![Belge penceresi Kılavuzu elmas](../ide/media/documentwindowguidediamonds.png)

Araç Pencereleri IDE içinde veya düzenleme çerçevesindeki içinde bir çerçevenin bir tarafına sabitlenebilir. Bir araç penceresini, pencereyi kolayca yeniden yerleştirmenize yardımcı olması için başka bir konuma sürüklediğinizde kılavuz elmas görünür.

![Araç penceresi Kılavuzu elleri](../ide/media/vs10guidediamond.png)

Aşağıdaki çizimde, mavi gölgeli alanla ilgili yeni bir konuma yerleştirilmiş **Çözüm Gezgini** gösterilmektedir:

![Yeni bir konumda Çözüm Gezgini sabitleme](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Araç pencerelerini kapat ve otomatik gizle

Başlık çubuğunun sağ üst köşesindeki **X** simgesine tıklayarak bir araç penceresini kapatabilirsiniz. Pencereyi yeniden açmak için, klavye kısayolunu veya menü komutunu kullanın. Araç pencereleri, *Otomatik Gizle*adlı bir özelliği destekler ve bu, farklı bir pencere kullandığınızda pencerenin bu şekilde kaydırılmasına neden olur. Bir pencere gizli olduğunda, adı IDE 'nin kenarındaki bir sekmede görünür. Pencereyi tekrar kullanmak için sekmenin görünüme geri yönlendirebilmesi için sekmesinde gidin.

![Otomatik Gizle](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Otomatik gizleme 'nin araç pencereleri için tek tek veya sabitlenmiş gruplar halinde çalışıp çalışmadığını belirlemek için otomatik gizleme düğmesini seçin veya temizleyin **seçeneği yalnızca seçenekler** iletişim kutusunda **etkin araç pencerelerini etkiler** . Daha fazla bilgi için bkz. [Genel, ortam, Seçenekler iletişim kutusu](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Otomatik gizleme özelliği etkin olan araç pencereleri, pencere odaklanıldığında geçici olarak görünüme kayarak çıkabilir. Pencereyi yeniden gizlemek için geçerli pencere dışında bir öğe seçin. Pencere odağı kaybettiğinde, görünümden çıkar.

### <a name="specifying-a-second-monitor"></a>İkinci bir izleyici belirtme

İkinci bir monitörünüz varsa ve işletim sisteminizin destekliyorsa, hangi monitörün pencere görüntüleyeceğini seçebilirsiniz. Diğer izleyicilerinde, *Rafts* içinde birden çok pencere de gruplandırabilirsiniz.

> [!TIP]
> Birden çok örneğini oluşturduğunuz **Çözüm Gezgini** ve başka bir monitöre taşıyabilirsiniz. Pencereye sağ tıklatın ve seçin **Yeni Çözüm Gezgini görünümü**. **CTRL** tuşunu seçerken, tüm pencereleri geri ' ye çift tıklayarak özgün monitöre döndürebilirsiniz.

### <a name="reset-name-and-switch-between-window-layouts"></a>Sıfırlama, adı ve pencere düzenlerini arasında geçiş yapma

Kullanarak ayarlar koleksiyonunuz için özgün pencere düzenini IDE döndürebilir **pencere düzenini Sıfırla** komutu. Bu komutu çalıştırdığınızda, aşağıdaki eylemler gerçekleşir:

- Tüm pencereler varsayılan konumlarına taşınır.

- Varsayılan pencere düzeninde kapatılan Windows kapatılır.

- Varsayılan pencere düzeninde Windows açılır.

### <a name="create-and-save-custom-layouts"></a>Oluşturun ve özel düzenler kaydedin

Visual Studio, 10 ' a kadar özel pencere düzenini kaydetmenizi ve aralarında hızlıca geçiş yapmanızı sağlar. Aşağıdaki adımlarda, oluşturma, kaydetme, çağırma ve her iki yerleşik ve kayan araç pencereleri ile birden çok monitör yararlanan özel düzenler yönetmek gösterilmektedir.

İlk olarak, iki proje içeren bir test çözümü her biri farklı bir en iyi düzen oluşturun.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Bir kullanıcı Arabirimi projesi oluşturun ve düzeni özelleştirme

1. Yeni C# bir **WPF uygulaması** projesi oluşturun. Bu projede, bir kullanıcı arabirimi geliştirdiğinizi düşünelim. Tasarımcı penceresinin alanını en üst düzeye çıkarmak ve diğer araç pencerelerini bu şekilde taşımak istiyorsunuz.

2. Birden çok monitörü varsa, çekme **Çözüm Gezgini** penceresi ve **özellikleri** pencere üzerinde ikinci bir monitörünüz. Tek bir izleme sistemine, Tasarımcı dışındaki tüm windows kapatmayı deneyin.

3. **Araç kutusu** penceresini göstermek için **Ctrl**+**alt**+**X** tuşlarına basın. Pencere yerleştirilmişse, yerleştirmek istediğiniz yere kayabilecek şekilde sürükleyin.

4. Visual Studio 'Yu hata ayıklama moduna almak için **F5** tuşuna basın. **Oto**, **çağrı yığınının**ve **Çıkış** hata ayıklama pencerelerinin konumunu istediğiniz şekilde ayarlayın. Oluşturmakta olduğunuz düzen hem düzenleme modu hem de hata ayıklama modu için geçerlidir.

5. Hem hata ayıklama modu hem de düzenleme modundaki mizanpajlarınız istediğiniz gibi **olduğunda pencere düzeni > pencere** **düzenini kaydet**' i seçin. Bu düzeni "tasarımcı" olarak çağırın.

     Yeni mizanpajınızı, **Ctrl**+**alt**+**1... 0**' ın ayrılmış listesinden sonraki klavye kısayoluna atandığını unutmayın.

#### <a name="create-a-database-project-and-layout"></a>Bir veritabanı projesi oluşturup düzeni

1. Yeni bir **SQL Server veritabanı** çözüme bir proje.

2. **Çözüm Gezgini** yeni projeye sağ tıklayın ve **Nesne Gezgini Görünüm**' ü seçin. Bu görüntüler **SQL Server Nesne Gezgini** access tabloları, görünümleri ve veritabanınızdaki diğer nesnelerin sağlayan bir pencere. Bu pencere float veya yerleşik bırakın. Diğer araç pencereleri, istediğiniz şekilde ayarlayın. Ek realronizme için gerçek bir veritabanı ekleyebilirsiniz, ancak bu izlenecek yol için gerekli değildir.

3. Mizanpajınızı istediğiniz **şekilde tercih ettiğinizde** , ana menüden pencere > pencere **yerleşimini kaydet**' i seçin. Bu düzeni "DB Project" olarak çağırın. (Bu proje için bir hata ayıklama modu düzeniyle ilgili değildir.)

#### <a name="switch-between-the-layouts"></a>Düzeni arasında geçiş yapın

Düzenler arasında geçiş yapmak için klavye kısayollarını kullanın veya ana menüden pencere **düzenini uygula** > **pencere** düzeni ' ni seçin.

![Pencere Düzen menüsünü Uygula](../ide/media/vs2015_applywindowlayout.png)

UI düzenini uyguladıktan sonra hem de düzenleme modunda hata ayıklama modunda düzenini nasıl korunur unutmayın.

Çoklu monitör Kurulum ve tek bir izleyici dizüstü evde varsa, her makine için iyileştirilmiş düzenleri oluşturabilirsiniz.

> [!NOTE]
> Tek izlemeli bir sisteme çok monitörlü bir düzen uygularsanız, ikinci monitöre yerleştirdiğiniz kayan pencereler artık Visual Studio penceresinin arkasında gizlenir. **Alt + Tab**tuşlarına basarak bu pencereleri öne çıkarabilirsiniz. Daha sonra Visual Studio 'Yu birden çok izleyiciyle açarsanız, düzeni yeniden uygulayarak pencereleri belirtilen konumlarına geri yükleyebilirsiniz.

#### <a name="manage-and-roam-your-layouts"></a>Yönetme ve katmanlarınızı Dolaşımda

Pencere **düzenlerini yönet** > **pencere** ' yi seçerek özel düzeninizi kaldırabilir, yeniden adlandırabilir veya yeniden sıralayabilirsiniz. Bir düzen taşırsanız, tuş bağlama listesinde yeni konumunu gösterecek şekilde otomatik olarak ayarlanır. Değiştirilen bağlamaları aksi olamaz ve bu nedenle aynı anda en fazla 10 düzenleri depolayabilirsiniz.

![Pencere düzenlerini Yönet](../ide/media/managewindowlayouts.png)

Kendinize hangi klavye kısayolunun atandığını hatırlatmak için, pencere **düzeni uygula** > **pencere** öğesini seçin.

Bu düzenleri otomatik olarak Visual Studio sürümleri arasında ve Blend örnekleri ayrı makinelerde ve tüm Express sürümleri için herhangi bir Express kuruluş arasında dolaşıma girer. Ancak, düzenleri Visual Studio, Blend ve Express Dolaşımda değil.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: IDE 'de gezinme](../ide/how-to-move-around-in-the-visual-studio-ide.md)
