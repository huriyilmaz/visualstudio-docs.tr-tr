---
title: Gölgelendirici Tasarımcısı
ms.date: 09/21/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85ce7b0f270f0da8728b17610a683dcc17d06189
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589935"
---
# <a name="shader-designer"></a>Gölgelendirici Tasarımcısı

Bu belge, *gölgeli*olarak bilinen özel görsel efektler oluşturmak, değiştirmek ve dışa aktarmak için Visual Studio **Shader Tasarımcısı** ile nasıl çalışılabildiğini açıklar.

Üst düzey gölgeli dili (HLSL) programlama bilmiyorsanız bile oyununuz veya uygulamanız için özel görsel efektler oluşturmak için **Shader Designer'ı** kullanabilirsiniz. **Shader Designer**bir gölgeli oluşturmak için, bir grafik olarak ortaya koydu. Diğer bir tarihte, verileri ve işlemleri temsil eden tasarım yüzey *düğümlerini* ekler ve işlemlerin verileri nasıl işleyeceğini tanımlamak için aralarında bağlantılar kurarsınız. Her işlem düğümünde, sonucunu görselleştirebilmeniz için o noktaya kadar olan efektin bir önizlemesi sağlanır. Veri, gölgeleyicinin çıktısını temsil eden son düğüme doğru düğümler üzerinden akar.

## <a name="supported-formats"></a>Desteklenen biçimler

**Shader Designer** bu gölgelendirme biçimlerini destekler:

|Biçim Adı|Dosya Uzantısı|Desteklenen İşlemler (Görünüm, Edit, Dışa Aktarma)|
|-----------------| - | - |
|Yönetmen GrafSi Shader Dili|*.dgsl*|Görüntüle, Edit|
|HLSL Shader (kaynak kodu)|*.hlsl*|Dışarı Aktarma|
|HLSL Shader (bayt kodu)|*.cso*|Dışarı Aktarma|
|C++ üstbilgi (HLSL bytecode dizisi)|*H*|Dışarı Aktarma|

## <a name="get-started"></a>Kullanmaya başlayın

Bu bölümde Visual Studio C++ projenize nasıl DGSL shader ekleyeceğiniz açıklanmaktadır ve başlamanıza yardımcı olacak temel bilgiler verilmektedir.

> [!NOTE]
> Shader graphs (.dgsl files) gibi grafik öğelerinin otomatik yapı tümleştirmesi yalnızca C++ projeleri için desteklenir.

### <a name="to-add-a-dgsl-shader-to-your-project"></a>Projenize DGSL shader eklemek için

1. Grafiklerle çalışmanız için gerekli Visual Studio bileşeninin yüklü olduğundan emin olun. Bileşenin adı **Image ve 3D model editörleri.**

   Yüklemek için, **Araçlar** > **Araçlar Al Araçları ve Özellikleri** menü çubuğundan seçerek Visual Studio Installer'ı açın ve ardından Bireysel **bileşenler** sekmesini seçin. Oyunlar **ve Grafikler** kategorisi altında Resim ve **3D model düzenleyicileri** bileşenini seçin ve sonra **Değiştir'i**seçin.

   ![Resim ve 3B model editörleri bileşeni](media/image-3d-model-editors-component.png)

2. **Çözüm Gezgini'nde,** gölgeleyicieklemek istediğiniz C++ projesinin kısayol menüsünü açın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.

3. Yüklü , **Grafik**seçin ve **Installed**sonra **Visual Shader Graph (.dgsl)** seçin Yeni **Öğe** ekle iletişim kutusunda.

   > [!NOTE]
   > **Yeni Öğe Ekle** iletişim kutusunda **Grafik** kategorisini görmüyorsanız ve Resim **ve 3B model düzenleyicileri** bileşeni yüklüyse, grafik öğeleri proje türünüz için desteklenmez.

4. Gölgeli dosyanın **Adını** ve oluşturulmasını istediğiniz **Konumu** belirtin.

5. **Ekle** düğmesini seçin.

### <a name="the-default-shader"></a>Varsayılan gölgeleyici

Bir DGSL gölgeleyici oluşturmak her zaman, **son renk** düğümüne bağlı sadece bir **Nokta Renk** düğümü olan en az gölgeli olarak başlar. Bu gölgeli tam ve işlevsel olmasına rağmen, çok yapmaz. Bu nedenle, çalışan bir gölgelendirme oluşturmanın ilk adımı genellikle **Nokta Rengi** düğümünü silmek veya diğer düğümlere yer açmak için **Son Renk** düğümünden kesmektir.

## <a name="work-with-the-shader-designer"></a>Shader Tasarımcısı ile Çalışma

Aşağıdaki bölümlerde, özel gölgelilerle çalışmak için Shader Tasarımcısı'nın nasıl kullanılacağı açıklanmıştır.

### <a name="shader-designer-toolbars"></a>Shader Designer araç çubukları

Shader Designer araç çubukları, DGSL gölgeli grafiklerle çalışmanıza yardımcı olan komutlar içerir.

Gölgeli Tasarımcısı'nın durumunu etkileyen komutlar, ana Visual Studio penceresindeki **Shader Designer Mode** araç çubuğunda bulunur. Tasarım araçları ve komutları Shader Designer tasarım yüzeyindeki **Shader Designer** araç çubuğunda bulunur.

İşte **Shader Designer Mode** araç çubuğu:

![Shader Designer modal araç çubuğu.](../designers/media/digit-dsd-modal-toolbar.png)

Bu tablo, Soldan sağa göründükleri sırada listelenen **Gölgeli Tasarımcı Modu** araç çubuğundaki öğeleri açıklar:

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Seç**|Grafikteki düğümler ve kenarlarla etkileşimi sağlar. Bu modda, düğümleri seçebilir ve taşıyabilir veya silebilir, kenarlar kurabilir veya kırabilirsiniz.|
|**Pan**|Pencere çerçevesine göre gölgeli grafiğin hareketini sağlar. Kaydırmak için, tasarım yüzeyinde bir nokta seçin ve hareket ettirin.<br /><br /> **Select** modunda, **Kaydırma** modunu geçici olarak etkinleştirmek için **Ctrl** tuşuna basıp basılı tutabilirsiniz.|
|**Zoom**|Pencere çerçevesine göre az çok gölgeli grafik ayrıntısının görüntülenmesini sağlar. **Yakınlaştırma** modunda, tasarım yüzeyinde bir nokta seçin ve yakınlaştırmak için sağa veya aşağı veya uzaklaştırmak için sağa veya aşağı taşıyın.<br /><br /> **Select** modunda, fare tekerleğini kullanarak yakınlaştırmak veya uzaklaştırmak için **Ctrl** tuşuna basıp basılı tutabilirsiniz.|
|**Sığdırmak için Yakınlaştırma**|Pencere çerçevesinde tam gölgeli grafiği görüntüler.|
|**Gerçek Zamanlı Görüntüleme Modu**|Gerçek zamanlı görüntüleme etkinleştirildiğinde, Visual Studio hiçbir kullanıcı eylemi gerçekleştirilmese bile tasarım yüzeyini yeniden çizer. Bu mod, zamanla değişen gölgelendiriciler ile çalıştığınızda kullanışlıdır.|
|**Küre ile önizleme**|Etkinleştirildiğinde, gölgeyi önizlemek için bir küre modeli kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Küple önizleme**|Etkinleştirildiğinde, gölgeyi önizlemek için bir küp modeli kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Silindir ile Önizleme**|Etkinleştirildiğinde, gölgeyi önizlemek için bir silindir modeli kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Koni ile önizleme**|Etkinleştirildiğinde, gölgeyi önizlemek için bir koni modeli kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Çaydanlıkla önizleme**|Etkinleştirildiğinde, gölgeyi önizlemek için bir çaydanlık modeli kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Düzlemle önizleme**|Etkinleştirildiğinde, gölgeyi önizlemek için bir düzlem modeli kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Araç Kutusu**|Araç **Kutusunu**dönüşümlü olarak gösterir veya gizler.|
|**Özellikler**|Alternatif olarak **Özellikler** penceresini gösterir veya gizler.|
|**Gelişmiş**|Gelişmiş komutları ve seçenekleri içerir.<br /><br /> **Dışa Aktarma**: Bir gölgeleyicinin çeşitli biçimlerde dışa aktarılmasını sağlar.<br /><br /> **As Dışa Aktarma**: Shader'ı HLSL kaynak kodu veya derlenmiş shader bytecode olarak dışa aktar. Gölgelilerin nasıl dışa aktarılabildiğini hakkında daha fazla bilgi için [bkz.](../designers/how-to-export-a-shader.md)<br /><br /> **Grafik Motorları**: Tasarım yüzeyini görüntülemek için kullanılan işleyicinin seçimini sağlar.<br /><br /> **D3D11 ile İşlen**: Shader Designer tasarım yüzeyini işlemek için Direct3D 11 kullanır.<br /><br /> **D3D11WARP ile işleme**: Shader Designer tasarım yüzeyini işlemek için Direct3D 11 Windows Advanced Rasterization Platform (WARP) kullanır.<br /><br /> **Görünüm**: Shader Designer hakkında ek bilgilerin seçilmesini sağlar.<br /><br /> **Kare Hızı**: Etkinleştirildiğinde, tasarım yüzeyinin sağ üst köşesindeki geçerli kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır. Bu seçenek, **Gerçek Zamanlı Görüntüleme Modu** seçeneğini etkinleştirdiğinizde yararlıdır.|

> [!TIP]
> Son komutu yeniden çalıştırmak için **Gelişmiş** düğmesini seçebilirsiniz.

### <a name="work-with-nodes-and-connections"></a>Düğümler ve bağlantılarla çalışma

Düğümleri eklemek, kaldırmak, yeniden konumlandırmak, bağlamak ve yapılandırmak için **Select** modunu kullanın. Bu temel işlemleri şu şekilde gerçekleştirebilirsiniz:

#### <a name="to-perform-basic-operations-in-select-mode"></a>Temel işlemleri Select modunda gerçekleştirmek için

- Bunu yapmak için:

  - Grafiğe düğüm eklemek için, **araç kutusunda** seçin ve ardından tasarım yüzeyine taşıyın.

  - Bir düğümü grafikten kaldırmak için seçip **Sil**tuşuna basın.

  - Düğümü yeniden konumlandırmak için düğümü seçin ve sonra yeni bir konuma taşıyın.

  - İki düğümü bağlamak için, bir düğümün çıkış terminalini diğer düğümün giriş terminaline taşıyın. Yalnızca uyumlu türleri olan terminaller bağlanabilir. Terminaller arasındaki bir çizgi bağlantıyı gösterir.

  - Bağlantıyı kaldırmak için, bağlı terminallerden birinin kısayol menüsünde **Bağlantıları Ara'yı**seçin.

  - Düğümün özelliklerini yapılandırmak için düğümü seçin ve ardından **Özellikler** penceresinde özellikler için yeni değerler belirtin.

### <a name="preview-shaders"></a>Önizleme gölgeleyicileri

Uygulamanızda bir gölgenin nasıl görüneceğini anlamanıza yardımcı olmak için efektinizin nasıl önizden izleneceğini yapılandırabilirsiniz. Uygulamanızı yaklaşık olarak işlemek, dokuları ve diğer malzeme parametrelerini yapılandırmak, zaman tabanlı efektlerin animasyonunu etkinleştirmek ve önizlemeyi farklı açılardan incelemek için çeşitli şekillerden birini seçebilirsiniz.

#### <a name="shapes"></a>Şekiller

Shader Designer altı şekil içerir- bir küre, bir küp, bir silindir, koni, bir çaydanlık, ve bir düzlem- gölgeli önizleme kullanabilirsiniz. Gölgeli bağlı olarak, bazı şekiller daha iyi bir önizleme verebilir.

Bir önizleme şekli seçmek için, **Shader Designer Modes** araç çubuğunda istediğiniz şekli seçin.

#### <a name="textures-and-material-parameters"></a>Dokular ve malzeme parametreleri

Birçok gölgeli, uygulamanızdaki her tür nesne için benzersiz bir görünüm oluşturmak için dokulara ve malzeme özelliklerine güvenir. Gölgeleyicinizin uygulamanızda nasıl görüneceğini görmek için, önizlemeyi oluşturmada kullanılan dokuları ve malzeme özelliklerini uygulamanızda kullanabileceğiniz dokular ve parametrelerle eşleşecek şekilde ayarlayabilirsiniz.

Farklı bir dokuyu doku kaydına bağlamak veya diğer malzeme parametrelerini değiştirmek için:

1. **Seç** modunda, tasarım yüzeyinin boş bir alanını seçin. Bu, **Özellikler** penceresinin genel gölgeli özelliklerini görüntülemesine neden olur.

2. **Özellikler** penceresinde, değiştirmek istediğiniz doku ve parametre özellikleri için yeni değerler belirtin.

Aşağıdaki tabloda değiştirebileceğiniz gölgeli parametreler gösterilmektedir:

|Parametre|Özellikler|
|---------------|----------------|
|**Doku 1** - **Doku 8**|**Erişim**: Özelliğin Model Düzenleyicisi'nden ayarlanabilmesi için **herkese açık** olması; aksi takdirde, **Özel**.<br /><br /> **Dosya adı**: Bu doku kaydıyla ilişkili doku dosyasının tam yolu.|
|**Malzeme Ortam**|**Erişim**: Özelliğin Model Düzenleyicisi'nden ayarlanabilmesi için **herkese açık** olması; aksi takdirde, **Özel**.<br /><br /> **Değer**: Dolaylı veya ortam - aydınlatma nedeniyle geçerli pikselin dağınık rengi.|
|**Malzeme Diffüz**|**Erişim**: Özelliğin Model Düzenleyicisi'nden ayarlanabilmesi için **herkese açık** olması; aksi takdirde, **Özel**.<br /><br /> **Değer**: Geçerli pikselin doğrudan aydınlatmayı nasıl yaydığını açıklayan renk.|
|**Malzeme Elçisi**|**Erişim**: Özelliğin Model Düzenleyicisi'nden ayarlanabilmesi için **herkese açık** olması; aksi takdirde, **Özel**.<br /><br /> **Değer**: Kendi kendine sağlanan aydınlatma nedeniyle geçerli pikselin renk katkısı.|
|**Malzeme Aynalı**|**Erişim**: Özelliğin Model Düzenleyicisi'nden ayarlanabilmesi için **herkese açık** olması; aksi takdirde, **Özel**.<br /><br /> **Değer**: Geçerli pikselin doğrudan aydınlatmayı nasıl yansıttığını açıklayan renk.|
|**Malzeme Specular Güç**|**Erişim**: Özelliğin Model Düzenleyicisi'nden ayarlanabilmesi için **herkese açık** olması; aksi takdirde, **Özel**.<br /><br /> **Değer**: Geçerli pikseldeki aynasal vurguların yoğunluğunu tanımlayan üs.|

#### <a name="time-based-effects"></a>Zamana dayalı efektler

Bazı gölgeleyicilerin efekti canlandıran zaman tabanlı bir bileşeni vardır. Efektin eylemde nasıl göründüğünü göstermek için önizlemenin saniyede birkaç kez güncellenmesi gerekir. Varsayılan olarak, önizleme yalnızca gölgeli değiştirildiğinde güncelleştirilir; zaman tabanlı efektleri görüntüleyebilmeniz için bu davranışı değiştirmek için gerçek zamanlı görüntülemeyi etkinleştirmeniz gerekir.

Gerçek zamanlı görüntülemeyi etkinleştirmek için, Shader Designer araç çubuğunda **Gerçek Zamanlı Görüntüleme'yi**seçin.

#### <a name="examine-the-effect"></a>Efekti inceleyin

Birçok gölgeli görüntüleme açısı veya yön aydınlatması gibi değişkenlerden etkilenir. Bu değişkenler değiştikçe efektin nasıl tepki verdiğini incelemek için önizleme şeklini serbestçe döndürebilir ve gölgeleyicinin nasıl tepki verdiğini gözlemleyebilirsiniz.

Şekli döndürmek için **Alt tuşuna**basın ve basılı tutun ve ardından tasarım yüzeyindeki herhangi bir noktayı seçin ve hareket ettirin.

### <a name="export-shaders"></a>Dışa aktarma shaders

Uygulamanızda bir gölgeli kullanabilmek için önce, uygulamayı DirectX'in anladığı bir biçimde dışa aktarmanız gerekir.

Shaders'ı HLSL kaynak kodu veya derlenmiş shader bytecode olarak dışa aktarabilirsiniz. HLSL kaynak *kodu,.hlsl* dosya adı uzantısı olan bir metin dosyasına dışa aktarılır. Shader bytecode, *.cso* dosya adı uzantısı olan ham bir ikili dosyaya veya gölgeli bayt kodunu bir diziye kodlayan bir C++ üstbilgisine (*.h*) dosyaya dışa aktarılabilir.

Gölgelilerin nasıl dışa aktarılabildiğini hakkında daha fazla bilgi için [bkz.](../designers/how-to-export-a-shader.md)

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

|Komut|Klavye kısayolları|
|-------------| - |
|**Select** moduna geç|**Ctrl**+**G**, **Ctrl**+**Q**<br /><br /> **S**|
|**Yakınlaştırma** moduna geçme|**Ctrl**+**G**, **Ctrl**+**Z**<br /><br /> **Z**|
|**Pan** moduna geçme|**Ctrl**+**G**, **Ctrl**+**P**<br /><br /> **Kahraman**|
|Tümünü seç|**Ctrl**+**A**|
|Geçerli seçimi sil|**Sil**|
|Geçerli seçimi iptal et|**Kaçış** (**Esc**)|
|Yakınlaştır|**Ctrl**+**Mouse tekerleği ileri**<br /><br /> Artı İşaret**+**( )|
|Uzaklaştır|**Ctrl**+**Fare tekerleği geriye**<br /><br /> Eksi İşareti (**-**)|
|Tasarım yüzeyini yukarı kaydırma|**Fare tekerleği geriye doğru**<br /><br /> **PageDown**|
|Tasarım yüzeyini aşağı kaydırma|**Fare tekerleği ileriye doğru**<br /><br /> **PageUp**|
|Tasarım yüzeyini sola kaydırma|**Shift**+**Mouse tekerleği geriye**<br /><br /> **Fare tekerleği sol**<br /><br /> **PageDown'ı Kaydır**+**PageDown**|
|Tasarım yüzeyini sağa kaydırma|**Shift**+**Mouse tekerleği ileri**<br /><br /> **Fare tekerleği sağ**<br /><br /> **Shift**+**PageUp**|
|Klavye odağıbaşka bir düğüme taşıma|**Ok** tuşları|
|Klavye odağı olan düğümü seçin (düğümü seçim grubuna ekler)|**Shift**+**Spacebar**|
|Klavye odağı olan düğümün seçimini geçiş|**Ctrl**+**Boşluk Çubuğu**|
|Geçerli seçimi geçişe kaydırma (düğüm yoksa, klavye odağı olan düğümü seçin)|**Boşluk çubuğu**|
|Geçerli seçimi yukarı taşıma|**Shift**+**Oku Yukarı Kaydır**|
|Geçerli seçimi aşağı taşıma|**Shift**+**Aşağı Ok** Kaydırma|
|Geçerli seçimi sola taşıma|**Shift**+**Sol Ok**|
|Geçerli seçimi sağa taşıma|**Shift**+**Sağ Ok**.|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Oyunlar ve uygulamalar için 3B varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Dokular ve görüntüler, 3B modeller ve gölgeefektleri ile çalışmak için kullanabileceğiniz Visual Studio araçlarına genel bir bakış sağlar.|
|[Görüntü Düzenleyici](../designers/image-editor.md)|Dokular ve görüntülerle çalışmak için Visual Studio Image Editor'un nasıl kullanılacağını açıklar.|
|[Model Düzenleyicisi](../designers/model-editor.md)|Visual Studio Model Editor'un 3B modellerle çalışmak için nasıl kullanılacağını açıklar.|
