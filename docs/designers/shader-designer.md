---
title: Gölgelendirici Tasarımcısı
description: Gölgelendirici olarak bilinen özel görsel Visual Studio oluşturmak, değiştirmek ve dışarı aktarmak için Visual Studio Gölgelendirici Tasarımcısı ile nasıl çalışabilirsiniz?
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073662"
---
# <a name="shader-designer"></a>Gölgelendirici Tasarımcısı

Bu belgede gölgelendirici olarak bilinen özel  görsel Visual Studio oluşturmak, değiştirmek ve dışarı aktarmak için Visual Studio Gölgelendirici Tasarımcısı ile nasıl *çalışabilirsiniz?*

Üst düzey **gölgelendirici dili** (HLSL) programlaması bilmiyorsanız bile, oyun veya uygulamanıza özel görsel efektler oluşturmak için Gölgelendirici Tasarımcısı'nın kullanabilirsiniz. Gölgelendirici Tasarımcısı'nda **bir gölgelendirici oluşturmak** için bunu grafik olarak ortaya koyabilirsiniz. Başka bir ifadeyle, verileri  ve işlemleri temsil eden tasarım yüzeyi düğümlerine eklersiniz ve ardından işlemlerin verileri nasıl işleyeni tanımlamak için bunlar arasında bağlantılar kurmanız gerekir. Her işlem düğümünde, o noktaya kadar olan etkinin önizlemesi sağlanır, böylece sonucu görselleştiresiniz. Veri, gölgelendiricinin çıkışını temsil eden son düğüme doğru düğümler arasında akar.

## <a name="supported-formats"></a>Desteklenen biçimler

Gölgelendirici **Tasarımcısı şu** gölgelendirici biçimlerini destekler:

|Biçim Adı|Dosya Uzantısı|Desteklenen İşlemler (Görüntüleme, Düzenleme, Dışarı Aktarma)|
|-----------------| - | - |
|Yönlendirildi Graph Gölgelendirici Dili|*.dgsl*|Görüntüle, Düzenle|
|HLSL Gölgelendiricisi (kaynak kodu)|*.hlsl*|Dışarı Aktarma|
|HLSL Gölgelendiricisi (bytecode)|*.cso*|Dışarı Aktarma|
|C++ üst bilgisi (HLSL bytecode dizisi)|*H*|Dışarı Aktarma|

## <a name="get-started"></a>başlarken

Bu bölümde, Visual Studio C++ projenize DGSL gölgelendiricisi ekleme ve başlamanıza yardımcı olacak temel bilgiler açıklandı.

> [!NOTE]
> Gölgelendirici grafikleri (.dgsl dosyaları) gibi grafik öğelerinin otomatik derleme tümleştirmesi yalnızca C++ projeleri için de kullanılabilir.

### <a name="to-add-a-dgsl-shader-to-your-project"></a>Projenize bir DGSL gölgelendiricisi eklemek için

1. Grafiklerle çalışma Visual Studio gereken gerekli bileşene sahip olduğundan emin olmak. Bileşenin adı **Görüntü ve 3D model düzenleyicileri'dir.**

   Yüklemek için, Visual Studio Yükleyicisi çubuğundan Araçlar Araçları ve Özellikleri Al'ı seçerek Visual Studio Yükleyicisi'yi açın ve ardından Bağımsız bileşenler sekmesini seçin. Oyunlar ve Grafikler kategorisi altında Görüntü ve 3D model düzenleyicileri bileşenini seçin ve ardından  >   Değiştir'i **seçin.**   

   ![Görüntü ve 3D model düzenleyicileri bileşeni](media/image-3d-model-editors-component.png)

2. Bu **Çözüm Gezgini,** gölgelendiriciyi eklemek istediğiniz C++ projesinin kısayol menüsünü açın ve ardından Yeni Öğe **Ekle'yi**  >  **seçin.**

3. Yeni Öğe Ekle **iletişim kutusundaki** Yüklü altında Grafikler'i ve ardından Visual Shader Graph  **(.dgsl) öğesini seçin.**

   > [!NOTE]
   > Yeni Öğe Ekle iletişim  kutusunda Grafik  kategorisini görmüyorsanız ve Görüntü ve **3D model** düzenleyicileri bileşeni yüklüyse, proje türünüz için grafik öğeleri desteklenmiyordur.

4. Gölgelendirici  dosyasının Adını ve **oluşturulacak** konumu belirtin.

5. **Ekle** düğmesini seçin.

### <a name="the-default-shader"></a>Varsayılan gölgelendirici

Her DGSL gölgelendiricisi olduğunuzda, Yalnızca Son Renk düğümüne  bağlı bir Nokta Rengi düğümüne sahip olan minimal bir gölgelendirici **olarak** başlar. Bu gölgelendirici eksiksiz ve işlevsel olsa da çok fazla bir şey yapmaz. Bu nedenle, çalışma gölgelendiricisi oluşturmanın ilk adımı genellikle **Nokta** Rengi düğümünü silmek veya diğer düğümlere yer sağlamak için **Son** Renk düğümüyle bağlantısını kesmektir.

## <a name="work-with-the-shader-designer"></a>Gölgelendirici Tasarımcısı ile çalışma

Aşağıdaki bölümlerde, özel gölgelendiricilerle çalışmak için Gölgelendirici Tasarımcısı'nın nasıl kullanımı açıklanmaktadır.

### <a name="shader-designer-toolbars"></a>Gölgelendirici Tasarımcısı araç çubukları

Gölgelendirici Tasarımcısı araç çubukları, DGSL gölgelendirici grafikleriyle çalışmanıza yardımcı olan komutlar içerir.

Gölgelendirici Tasarımcısı'nın durumunu etkileyen komutlar,  ana gölgelendirici penceresindeki Gölgelendirici Tasarımcısı Modu araç Visual Studio bulunur. Tasarım araçları ve komutlar Gölgelendirici **Tasarımcısı tasarım yüzeyinde** gölgelendirici Tasarımcısı araç çubuğunda bulunur.

Gölgelendirici Tasarımcısı Modu **araç çubuğu şu şekildedir:**

![Gölgelendirici Tasarımcısı kalıcı araç çubuğu.](../designers/media/digit-dsd-modal-toolbar.png)

Bu tabloda Gölgelendirici Tasarımcısı  Modu araç çubuğundaki öğeler, soldan sağa doğru görünme sırasına göre listelenmiştir:

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Seç**|Grafikte düğümler ve kenarlarla etkileşime olanak sağlar. Bu modda düğümleri seçerek taşıma veya silme, kenarlar kurma veya kesme gibi seçeneklere sahip olursunuz.|
|**Kaydır**|Bir gölgelendirici grafiğinin pencere çerçevesine göre hareketini sağlar. Kaydırmak için tasarım yüzeyinde bir nokta seçin ve bu noktanın etrafında hareket ettirin.<br /><br /> Seçim **modunda,** Pan modunu geçici olarak etkinleştirmek için **Ctrl tuşuna** **basabilirsiniz.**|
|**Zoom**|Pencere çerçevesine göre daha fazla veya daha az gölgelendirici grafı ayrıntısı görüntülenmeye olanak sağlar. Yakınlaştırma **modunda** tasarım yüzeyinde bir nokta seçin ve ardından yakınlaştırmak için sağa veya aşağı hareket ettirin ya da uzaklaştırın ya da sola ya da yukarıya gelin.<br /><br /> Seç **modunda,** fare tekerleğini kullanarak yakınlaştırmak veya uzaklaştırmak için **Ctrl** tuşuna basıp basılı tutabilirsiniz.|
|**Sığdırmak için Yakınlaştır**|Pencere çerçevesinde tam gölgelendirici grafiğini görüntüler.|
|**Gerçek Zamanlı İşleme Modu**|Gerçek zamanlı işleme etkinleştirildiğinde, Visual Studio eylemi gerçekleştirilmese bile tasarım yüzeyini yeniden çizin. Bu mod, zamanla değişen gölgelendiriciler ile çalıştığınızda kullanışlıdır.|
|**Sphere ile önizleme**|Etkinleştirildiğinde, gölgelendiricinin önizlemesini görmek için bir küre modeli kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Küp ile önizleme**|Etkinleştirildiğinde, gölgelendiricinin önizlemesini görmek için bir küp modeli kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Silindir ile Önizleme**|Etkinleştirildiğinde, gölgelendiricinin önizlemesini görmek için bir silindir modeli kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Külah ile önizleme**|Etkinleştirildiğinde gölgelendiricinin önizlemesini görmek için bir külah modeli kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Çaydanlık ile önizleme**|Etkinleştirildiğinde, gölgelendiricinin önizlemesini görmek için bir çaydanlık modeli kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Düzlem ile önizleme**|Etkinleştirildiğinde gölgelendiricinin önizlemesini görmek için bir düzlem modeli kullanılır. Aynı anda yalnızca bir önizleme şekli etkinleştirilebilir.|
|**Araç Kutusu**|Alternatif olarak Araç Kutusunu gösterir **veya gizler.**|
|**Özellikler**|Alternatif olarak Özellikler penceresini gösterir veya **gizler.**|
|**Gelişmiş**|Gelişmiş komutları ve seçenekleri içerir.<br /><br /> **Dışarı** aktar: Bir gölgelendiricinin çeşitli biçimlerde dışarı aktarılabilir.<br /><br /> **Farklı Dışarı** Aktar: Gölgelendiriciyi HLSL kaynak kodu olarak veya derlenmiş gölgelendirici bytecode olarak dışarı aktarın. Gölgelendiricileri dışarı aktarma hakkında daha fazla bilgi için [bkz. Nasıl: Gölgelendiriciyi dışarı aktarma.](../designers/how-to-export-a-shader.md)<br /><br /> **Grafik Altyapıları:** Tasarım yüzeyini görüntülemek için kullanılan işleyicinin seçimini sağlar.<br /><br /> **D3D11 ile işleme:** Gölgelendirici Tasarımcısı tasarım yüzeyini işlemek için Direct3D 11 kullanır.<br /><br /> **D3D11WARP** ile işleme: Gölgelendirici Tasarımcısı tasarım yüzeyini işlemek için Direct3D 11 Windows Gelişmiş Tarama Platformu'na (RENDER) sahiptir.<br /><br /> **Görünüm:** Gölgelendirici Tasarımcısı hakkında ek bilgi seçimini sağlar.<br /><br /> **Çerçeve Hızı:** Etkinleştirildiğinde, tasarım yüzeyinin sağ üst köşesinde geçerli kare oranını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır. Bu seçenek, Gerçek Zamanlı İşleme **Modu seçeneğini etkinleştirenler için** kullanışlıdır.|

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

Birçok gölgelendirici, uygulamanıza her tür nesne için benzersiz bir görünüm oluşturmak için dokulara ve malzeme özelliklerine güvenmektedir. Gölgelendiricinizin uygulamanıza nasıl bir şey göreceğini görmek için, önizlemeyi işlemek için kullanılan dokuları ve malzeme özelliklerini uygulamanıza ek olarak kullanabileceğiniz dokular ve parametrelerle eş hale gelecek şekilde ayarlayın.

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

Birçok gölgelendirici, açıyı veya yönlü aydınlatmayı görüntüleme gibi değişkenlerden etkilenir. Bu değişkenler değiştiklerinde etkinin nasıl yanıt verme şeklini incelemek için önizleme şeklini serbestçe döndürebilir ve gölgelendiricinin nasıl davrandığını gözlemleyebilirsiniz.

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
|Kaydırma **moduna** geçme|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **P**<br /><br /> **K**|
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
