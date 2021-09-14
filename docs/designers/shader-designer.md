---
title: Gölgelendirici Tasarımcısı
description: gölgelendiriciler olarak bilinen özel görsel etkileri oluşturmak, değiştirmek ve dışarı aktarmak için Visual Studio gölgelendirici tasarımcısı ile nasıl çalışacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/21/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 02b59924a2b2020d6c5855f5e91f41615601a19d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725869"
---
# <a name="shader-designer"></a>Gölgelendirici Tasarımcısı

bu belgede, *gölgelendiriciler* olarak bilinen özel görsel etkileri oluşturmak, değiştirmek ve dışarı aktarmak için Visual Studio **gölgelendirici tasarımcısı** ile nasıl çalışılacağı açıklanmaktadır.

Üst düzey gölgelendirici dili (HLSL) programlamayı bilmiyor olsanız bile, oyununuz veya uygulamanız için özel görsel etkiler oluşturmak üzere **gölgelendirici tasarımcısını** kullanabilirsiniz. **Gölgelendirici tasarımcısında** gölgelendirici oluşturmak için onu bir grafik olarak yerleştirirsiniz. Yani, verileri ve işlemleri temsil eden tasarım yüzeyi *düğümlerine* ekler ve sonra işlemlerin verileri nasıl işleyeceğini tanımlamak için bunlar arasında bağlantı yaparsınız. Her bir işlem düğümünde, bu noktaya kadar olan efektin bir önizlemesi sağlanır, böylece sonucu görselleştirebilirsiniz. Veriler, gölgelendirici çıkışını temsil eden son bir düğüme doğru düğümler aracılığıyla akar.

## <a name="supported-formats"></a>Desteklenen biçimler

**Gölgelendirici Tasarımcısı** Bu gölgelendirici biçimlerini destekler:

|Biçim Adı|Dosya Uzantısı|Desteklenen Işlemler (görüntüleme, düzenleme, dışarı aktarma)|
|-----------------| - | - |
|yönlendirilmiş Graph gölgelendirici dili|*. dgsl*|Görüntüleme, düzenleme|
|HLSL gölgelendiricisi (kaynak kodu)|*. HLSL*|Dışarı Aktarma|
|HLSL gölgelendiricisi (bytecode)|*. cso*|Dışarı Aktarma|
|C++ üstbilgisi (HLSL bytecode dizisi)|*. h*|Dışarı Aktarma|

## <a name="get-started"></a>başlarken

bu bölümde, Visual Studio C++ projenize bir dgsl gölgelendiricisi ekleme ve kullanmaya başlamanıza yardımcı olacak temel bilgiler sağlanmaktadır.

> [!NOTE]
> Gölgelendirici grafikleri (. dgsl dosyaları) gibi grafik öğelerinin otomatik derleme tümleştirmesi yalnızca C++ projeleri için desteklenir.

### <a name="to-add-a-dgsl-shader-to-your-project"></a>Projenize bir DGSL gölgelendiricisi eklemek için

1. grafiklerle çalışmanız gereken Visual Studio bileşenin yüklü olduğundan emin olun. Bileşen, **görüntü ve 3B model düzenleyicileri** olarak adlandırılır.

   yüklemek için **araçlar**  >  menüsünü ve menü çubuğundan araçlar **al** ' ı seçerek Visual Studio Yükleyicisi açın ve ardından **ayrı bileşenler** sekmesini seçin. **oyunlar ve grafikler** kategorisi altındaki **görüntü ve 3b model düzenleyicileri** bileşenini seçin ve ardından **değiştir**' i seçin.

   ![Görüntü ve 3B model düzenleyicileri bileşeni](media/image-3d-model-editors-component.png)

2. **Çözüm Gezgini**' de, gölgelendiriciyi eklemek istediğiniz C++ projesinin kısayol menüsünü açın ve   >  **Yeni öğe** Ekle ' yi seçin.

3. **yeni öğe ekle** iletişim kutusunda, **yüklü** altında **grafikler**' i seçin ve ardından **görsel gölgelendirici Graph (. dgsl)** öğesini seçin.

   > [!NOTE]
   > **Yeni öğe Ekle** Iletişim kutusunda **grafik** kategorisini görmüyorsanız ve **resim ve 3B model düzenleyicileri** bileşeni yüklüyse, grafik öğeleri proje türü için desteklenmez.

4. Gölgelendirici dosyasının **adını** ve oluşturulmasını istediğiniz **konumu** belirtin.

5. **Ekle** düğmesini seçin.

### <a name="the-default-shader"></a>Varsayılan gölgelendirici

Her bir DGSL gölgelendiricisi oluşturduğunuzda, **son renk** düğümüne bağlanmış yalnızca bir **nokta rengi** düğümüne sahip olan minimal bir gölgelendirici olarak başlar. Bu gölgelendirici tamamlanmış ve işlevsel olsa da, çok fazla değildir. Bu nedenle, çalışma Gölgelendirici oluşturmanın ilk adımı genellikle **nokta rengi** düğümünü silmek veya diğer düğümlere yer açmak Için **son renk** düğümü bağlantısını keser.

## <a name="work-with-the-shader-designer"></a>Gölgelendirici Tasarımcısı ile çalışma

Aşağıdaki bölümlerde, özel gölgelendiriciler ile çalışmak için Gölgelendirici Tasarımcısının nasıl kullanılacağı açıklanır.

### <a name="shader-designer-toolbars"></a>Gölgelendirici Tasarımcısı araç çubukları

Gölgelendirici Tasarımcısı araç çubukları, DGSL gölgelendirici grafikleriyle çalışmanıza yardımcı olan komutlar içerir.

gölgelendirici tasarımcısının durumunu etkileyen komutlar, ana Visual Studio penceresindeki **gölgelendirici tasarımcı modu** araç çubuğunda bulunur. Tasarım araçları ve komutları, gölgelendirici Tasarımcısı tasarım yüzeyinde **Gölgelendirici Tasarımcısı** araç çubuğunda bulunur.

**Gölgelendirici tasarımcı modu** araç çubuğu şöyledir:

![Gölgelendirici Tasarımcısı kalıcı araç çubuğu.](../designers/media/digit-dsd-modal-toolbar.png)

Bu tabloda, **gölgelendirici tasarımcı modu** araç çubuğunda soldan sağa göründükleri sırada listelenen öğeler açıklanmaktadır:

|Araç Çubuğu Öğesi|Description|
|------------------|-----------------|
|**Seç**|Grafikteki düğümlerle ve kenarlarla etkileşimi sunar. Bu modda düğümleri seçip taşıyabilir ya da silebilirsiniz ve kenarları oluşturabilir veya bunları kesebilirsiniz.|
|**Kaydır**|Bir gölgelendirici grafiğinin pencere çerçevesine göre taşınmasını sağlar. Kaydırmak için tasarım yüzeyinde bir nokta seçin ve taşıyın.<br /><br /> **Seçim** modunda, **Dikey Çevir** modunu geçici olarak etkinleştirmek için **CTRL** tuşuna basılı tutabilirsiniz.|
|**Zoom**|Pencere çerçevesine göre daha fazla veya daha az gölgelendirici grafik ayrıntısı görüntülenmesini sağlar. **Yakınlaştırma** modu ' nda tasarım yüzeyinde bir nokta seçin ve yakınlaştırmak için sağa veya aşağı taşıyın ya da uzaklaştırmak için sola veya yukarı kaydırın.<br /><br /> **Seçme** modunda, fare tekerleğini kullanarak yakınlaştırmak veya uzaklaştırmak için **CTRL** tuşuna basılı tutabilirsiniz.|
|**Sığacak kadar Yakınlaştır**|Pencere çerçevesindeki tam gölgelendirici grafiğini görüntüler.|
|**Gerçek zamanlı Işleme modu**|gerçek zamanlı işleme etkinleştirildiğinde, kullanıcı eylemi gerçekleştirilmediğinde bile tasarım yüzeyini yeniden çizer Visual Studio. Bu mod, zamanla değişen gölgelendiriciler ile çalıştığınızda kullanışlıdır.|
|**Sphere ile Önizleme**|Etkinleştirildiğinde, gölgelendiricinin önizlemesi için bir Sphere modeli kullanılır. Tek seferde yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Küp ile Önizleme**|Etkinleştirildiğinde, gölgelendirici önizlemesi için bir küpün modeli kullanılır. Tek seferde yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Silindir ile Önizleme**|Etkinleştirildiğinde, gölgelendiriciyi önizlemek için bir silindir modeli kullanılır. Tek seferde yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Koni ile Önizleme**|Etkinleştirildiğinde, gölgelendiriciyi önizlemek için koni modeli kullanılır. Tek seferde yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Ekiple Önizleme**|Etkinleştirildiğinde, gölgelendiriciyi önizlemek için bir ekip modeli kullanılır. Tek seferde yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Düzlemle Önizleme**|Etkinleştirildiğinde, gölgelendiriciyi önizlemek için düzlemin bir modeli kullanılır. Tek seferde yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Araç Kutusu**|Ayrıca **araç kutusunu** gösterir veya gizler.|
|**Özellikler**|Alternatif olarak, **Özellikler** penceresini gösterir veya gizler.|
|**Gelişmiş**|Gelişmiş komutları ve seçenekleri içerir.<br /><br /> **Dışarı aktar**: bir gölgelendiricinin birkaç biçimde dışa aktarılmasını mümkün.<br /><br /> **Farklı ver**: gölgelendiriciyi HLSL kaynak kodu veya derlenen gölgelendirici bayt olarak dışa aktarır. Gölgelendiricilerin nasıl dışarı aktarılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md).<br /><br /> **Grafik altyapıları**: tasarım yüzeyini göstermek için kullanılan oluşturucunun seçilmesini sağlar.<br /><br /> **D3d11 Ile işle**: Gölgelendirici Tasarımcısı tasarım yüzeyini Işlemek için Direct3D 11 kullanır.<br /><br /> **D3D11WARP ile işle**: gölgelendirici tasarımcısı tasarım yüzeyini işlemek için Direct3D 11 Windows gelişmiş tarama platformu (WARP) kullanır.<br /><br /> **Görünüm:** Gölgelendirici Tasarımcısı hakkında ek bilgi seçimini sağlar.<br /><br /> **Çerçeve Hızı:** Etkinleştirildiğinde, tasarım yüzeyinin sağ üst köşesinde geçerli kare oranını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır. Bu seçenek, Gerçek Zamanlı İşleme **Modu seçeneğini etkinleştirenler için** kullanışlıdır.|

> [!TIP]
> Son komutu yeniden **çalıştırmak** için Gelişmiş düğmesini seçebilirsiniz.

### <a name="work-with-nodes-and-connections"></a>Düğümler ve bağlantılarla çalışma

Düğümleri **eklemek,** kaldırmak, yeniden konumlandırmak, bağlamak ve yapılandırmak için Seçim modunu kullanın. Bu temel işlemleri şu şekilde gerçekleştirin:

#### <a name="to-perform-basic-operations-in-select-mode"></a>Seçim modunda temel işlemleri gerçekleştirmek için

- Aşağıdaki adımları uygulayın:

  - Grafiye bir düğüm eklemek için, Araç Kutusundan düğümü **seçin** ve tasarım yüzeyine taşıyın.

  - Bir düğümü grafikten kaldırmak için seçin ve Sil'e **basın.**

  - Bir düğümü yeniden konumlandırmak için düğümü seçin ve yeni bir konuma taşının.

  - İki düğümü bağlamak için, bir düğümün çıkış terminali diğer düğümün giriş terminaline hareket ettirin. Yalnızca uyumlu türlere sahip terminaller bağlanabilir. Terminaller arasındaki bir satır, bağlantıyı gösterir.

  - Bağlantıyı kaldırmak için, bağlı terminallerden birinin kısayol menüsünde Bağlantıları **Kesme'yi seçin.**

  - Bir düğümün özelliklerini yapılandırmak için düğümü seçin ve özellikler **penceresinde** özellikler için yeni değerler belirtin.

### <a name="preview-shaders"></a>Önizleme gölgelendiricileri

Bir gölgelendiricinin uygulamanıza nasıl görüneceklerini anlamanıza yardımcı olmak için, etkinizin önizlemesini yapılandırabilirsiniz. Uygulamanıza yakınlık sağlamak için işlenecek çeşitli şekillerden birini seçebilir, dokuları ve diğer malzeme parametrelerini yapılandırabilirsiniz, zaman tabanlı etkilerin animasyonunu etkinleştirebilirsiniz ve önizlemeyi farklı açılardan inceebilirsiniz.

#### <a name="shapes"></a>Şekiller

Gölgelendirici Tasarımcısı gölgelendiricinizi önizlemek için kullanabileceğiniz altı şekil (bir küre, küp, silindir, külah, bir çaydanlık ve bir düzlem) içerir. Gölgelendiriciye bağlı olarak bazı şekiller daha iyi bir önizlemeye sahip olabilir.

Önizleme şeklini seçmek için Gölgelendirici **Tasarımcısı** Modları araç çubuğunda istediğiniz şekli seçin.

#### <a name="textures-and-material-parameters"></a>Dokular ve malzeme parametreleri

Birçok gölgelendirici, uygulamanıza her tür nesne için benzersiz bir görünüm oluşturmak için dokulara ve malzeme özelliklerine güvenmektedir. Gölgelendiricinizin uygulamanıza nasıl bir görünümde olduğunu görmek için, önizlemeyi işlemek için kullanılan dokuları ve malzeme özelliklerini uygulamanıza ek olarak kullanabileceğiniz dokular ve parametrelerle eş hale gelecek şekilde ayarlayın.

Doku kaydına farklı bir doku bağlamak veya diğer malzeme parametrelerini değiştirmek için:

1. Seç **modunda** tasarım yüzeyinin boş bir alanı seçin. Bu, Özellikler **penceresinin** genel gölgelendirici özelliklerini görüntülemesine neden olur.

2. Özellikler **penceresinde,** değiştirmek istediğiniz doku ve parametre özellikleri için yeni değerler belirtin.

Aşağıdaki tabloda değiştirerek değiştirerek gölgelendirici parametrelerine yer ve ardından ve ardından 2018'e kadar olan tüm gölgelendirici parametreleri ve daha sonra aşağıdaki tabloda değişiklik yapabilirsiniz:

|Parametre|Özellikler|
|---------------|----------------|
|**Doku 1**  -  **Doku 8**|**Erişim:**                             **Özelliğin** Model Düzenleyicisi'nde ayarlanmış olmasına izin vermek için Genel; aksi takdirde, **Özel**.<br /><br /> **Dosya adı:** Bu doku kaydıyla ilişkili doku dosyasının tam yolu.|
|**Malzeme Ortamı**|**Erişim:**                             **Özelliğin** Model Düzenleyicisi'nde ayarlanmış olmasına izin vermek için Genel; aksi takdirde, **Özel**.<br /><br /> **Değer:** Dolaylı veya ortam - aydınlatma nedeniyle geçerli pikselin dağınık rengi.|
|**Malzeme Yayma**|**Erişim:** **Özelliğin** Model Düzenleyicisi'nde ayarlanmış olmasına izin vermek için Genel; aksi takdirde, **Özel**.<br /><br /> **Değer:** Geçerli pikselin doğrudan aydınlatmayı nasıl yaymalarını açıklayan bir renk.|
|**Malzeme Emissive**|**Erişim:**                              **Özelliğin** Model Düzenleyicisi'nde ayarlanmış olmasına izin vermek için Genel; aksi takdirde, **Özel**.<br /><br /> **Değer:** Otomatik olarak sağlanan aydınlatma nedeniyle geçerli pikselin renk katkısı.|
|**Malzeme Özellikleri**|**Erişim:**                              **Özelliğin** Model Düzenleyicisi'nde ayarlanmış olmasına izin vermek için Genel; aksi takdirde, **Özel**.<br /><br /> **Değer:** Geçerli pikselin doğrudan aydınlatmayı nasıl yansıtdığını açıklayan bir renk.|
|**Malzeme Specular Gücü**|**Erişim:**                             **Özelliğin** Model Düzenleyicisi'nde ayarlanmış olmasına izin vermek için Genel; aksi takdirde, **Özel**.<br /><br /> **Değer:** Geçerli pikselde belirli vurguların yoğunluğunu tanımlayan üs.|

#### <a name="time-based-effects"></a>Zaman tabanlı etkiler

Bazı gölgelendiriciler, etkiye animasyonu olan zaman tabanlı bir bileşene sahiptir. Etkinin nasıl göründüğünü göstermek için önizlemenin saniye başına birkaç kez güncelleştirilmiş olması gerekir. Varsayılan olarak önizleme yalnızca gölgelendirici değiştirdiğinde güncelleştirilir; Bu davranışı, zaman tabanlı etkileri görüntüley olanaklı olacak şekilde değiştirmek için gerçek zamanlı işlemeyi etkinleştirmeniz gerekir.

Gerçek zamanlı işlemeyi etkinleştirmek için Gölgelendirici Tasarımcısı araç çubuğunda Gerçek Zamanlı **İşleme'yi seçin.**

#### <a name="examine-the-effect"></a>Etkiyi inceleme

Birçok gölgelendirici, görüntüleme açısı veya yönlü aydınlatma gibi değişkenlerden etkilenir. Bu değişkenler değiştiklerinde etkinin nasıl yanıt verme şeklini incelemek için önizleme şeklini serbestçe döndürebilir ve gölgelendiricinin nasıl davrandığını gözlemleyebilirsiniz.

Şekli döndürmek için Alt tuşuna **basın** ve basılı tutun, ardından tasarım yüzeyinde herhangi bir nokta seçin ve hareket ettirin.

### <a name="export-shaders"></a>Gölgelendiricileri dışarı aktarma

Uygulamanıza gölgelendiriciyi kullanamadan önce DirectX'in anlayacaktır.

Gölgelendiricileri HLSL kaynak kodu olarak veya derlenmiş gölgelendirici bytecode olarak dışarı aktarabilirsiniz. HLSL kaynak kodu, *.hlsl* dosya adı uzantısına sahip bir metin dosyasına dışarı aktarıldı. Gölgelendirici bytecode, *.cso* dosya adı uzantısına sahip bir ham ikili dosyaya veya gölgelendirici bytecode'unu bir diziye kodlayan bir C++ üst bilgisi (*.h*) dosyasına aktarabilirsiniz.

Gölgelendiricileri dışarı aktarma hakkında daha fazla bilgi için [bkz. Nasıl: Gölgelendiriciyi dışarı aktarma.](../designers/how-to-export-a-shader.md)

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

|Komut|Klavye kısayolları|
|-------------| - |
|Seçim **moduna** geçme|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **Q**<br /><br /> **S**|
|Yakınlaştırma **moduna** geçme|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **Z**<br /><br /> **Z**|
|Pan **moduna** geçme|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **P**<br /><br /> **K**|
|Tümünü seç|**Ctrl tuşunu basılı tutarak** + **A**|
|Geçerli seçimi sil|**Silme**|
|Geçerli seçimi iptal et|**Kaçış** (**Esc**)|
|Yakınlaştır|**Ctrl tuşunu basılı tutarak** + **Fare tekerleği ileri**<br /><br /> Artı İşareti ( **+** )|
|Uzaklaştır|**Ctrl tuşunu basılı tutarak** + **Fare tekerleği geriye doğru**<br /><br /> Eksi İşareti ( **-** )|
|Tasarım yüzeyini yukarı kaydır|**Fare tekerleği geriye doğru**<br /><br /> **PageDown**|
|Tasarım yüzeyini aşağı kaydır|**Fare tekerleği ileriye doğru**<br /><br /> **PageUp**|
|Tasarım yüzeyini sola kaydır|**Shift ile kaydırma** + **Fare tekerleği geriye doğru**<br /><br /> **Fare tekerleği sol**<br /><br /> **SHIFT** + **Pageaşağı**|
|Tasarım yüzeyini sağa kaydır|**SHIFT** + **Fare tekerleği ileri**<br /><br /> **Fare tekerleği sağ**<br /><br /> **SHIFT** + **PageUp**|
|Klavye odağını başka bir düğüme taşı|**Ok** tuşları|
|Klavye odağının bulunduğu düğümü seçin (düğümü seçim grubuna ekler)|**SHIFT** + **Boşluk çubuğu**|
|Klavye odağına sahip olan düğüm seçimini değiştirme|**CTRL** + **Boşluk çubuğu**|
|Geçerli seçimi değiştirin (hiçbir düğüm seçilmezse, klavye odağına sahip düğümü seçin)|**Boşluk çubuğu**|
|Geçerli seçimi yukarı taşı|**SHIFT** + **Yukarı ok**|
|Geçerli seçimi aşağı taşı|**SHIFT** + **Aşağı ok**|
|Geçerli seçimi sola taşı|**SHIFT** + **Sol ok**|
|Geçerli seçimi sağa taşı|**SHIFT** + **Sağ ok**.|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Oyunlar ve uygulamalar için 3B varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|dokular ve görüntüler, 3b modeller ve gölgelendirici efektleri ile çalışmak için kullanabileceğiniz Visual Studio araçlarına genel bir bakış sağlar.|
|[Görüntü Düzenleyicisi](../designers/image-editor.md)|dokularla ve görüntülerle çalışmak için Visual Studio görüntü düzenleyicisi ' nin nasıl kullanılacağını açıklar.|
|[Model Düzenleyicisi](../designers/model-editor.md)|3b modellerle çalışmak için Visual Studio Model düzenleyicisi ' nin nasıl kullanılacağını açıklar.|
