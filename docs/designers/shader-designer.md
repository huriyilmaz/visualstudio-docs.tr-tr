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
ms.openlocfilehash: b3532444945b02f145262d099e41fe69d99b6926ef9aa64c4d780978463de7f3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435145"
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
|**Gelişmiş**|Gelişmiş komutları ve seçenekleri içerir.<br /><br /> **Dışarı** Aktar: Gölgelendiricinin çeşitli biçimlerde dışarı aktarılabilir.<br /><br /> **Farklı Dışarı** Aktar: Gölgelendiriciyi HLSL kaynak kodu olarak veya derlenmiş gölgelendirici bytecode olarak dışarı aktarın. Gölgelendiricileri dışarı aktarma hakkında daha fazla bilgi için [bkz. Nasıl: Gölgelendiriciyi dışarı aktarma.](../designers/how-to-export-a-shader.md)<br /><br /> **Grafik Altyapıları:** Tasarım yüzeyini görüntülemek için kullanılan işleyicinin seçimini sağlar.<br /><br /> **D3D11 ile işleme:** Gölgelendirici Tasarımcısı tasarım yüzeyini işlemek için Direct3D 11 kullanır.<br /><br /> **D3D11WARP** ile işleme: Gölgelendirici Tasarımcısı tasarım yüzeyini işlemek için Direct3D 11 Windows Gelişmiş Tarama Platformu'na (RENDER) sahiptir.<br /><br /> **Görünüm**: Gölgelendirici Tasarımcısı hakkında ek bilgi seçimini sunar.<br /><br /> **Kare hızı**: etkinleştirildiğinde, tasarım yüzeyinin sağ üst köşesindeki geçerli kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır. Bu seçenek, **gerçek zamanlı Işleme modu** seçeneğini etkinleştirdiğinizde yararlıdır.|

> [!TIP]
> Son komutu yeniden çalıştırmak için **Gelişmiş** düğmesini seçebilirsiniz.

### <a name="work-with-nodes-and-connections"></a>Düğümler ve bağlantılarla çalışma

Düğümleri eklemek, kaldırmak, yeniden konumlandırmak, bağlamak ve yapılandırmak için **seçim** modunu kullanın. Bu temel işlemleri gerçekleştirmek için aşağıdaki adımları izleyin:

#### <a name="to-perform-basic-operations-in-select-mode"></a>Seçme modunda temel işlemleri gerçekleştirmek için

- Aşağıdaki adımları uygulayın:

  - Grafiğe bir düğüm eklemek için **araç kutusunda** seçin ve tasarım yüzeyine taşıyın.

  - Grafikten bir düğüm kaldırmak için, seçin ve ardından **Delete** tuşuna basın.

  - Bir düğümü yeniden konumlandırmak için seçin ve sonra yeni bir konuma taşıyın.

  - İki düğüm bağlamak için bir düğümün çıkış terminalini diğer düğümün giriş terminaline taşıyın. Yalnızca uyumlu türleri olan terminaller bağlanabilir. Terminallerde bir çizgi bağlantıyı gösterir.

  - Bir bağlantıyı kaldırmak için, bağlı terminallerin her biri için kısayol menüsünde **Bağlantıları Kes**' i seçin.

  - Bir düğümün özelliklerini yapılandırmak için düğümü seçin ve ardından **Özellikler** penceresinde özellikler için yeni değerler belirtin.

### <a name="preview-shaders"></a>Gölgelendiriciler önizlemesi

Uygulamanızda bir gölgelendiricinin nasıl görüneceğini anlamanıza yardımcı olmak için, etkinizi nasıl önizlenbileceğinizi yapılandırabilirsiniz. Uygulamanızı yaklaşık olarak oluşturmak, dokular ve diğer malzeme parametrelerini yapılandırmak, zaman tabanlı efektlerin animasyonunu etkinleştirmek ve farklı açılardan önizlemeyi incelemek için çeşitli şekillerden birini seçebilirsiniz.

#### <a name="shapes"></a>Şekiller

Gölgelendirici Tasarımcısı, Gölgelendiricinizi önizlemek için kullanabileceğiniz altı şekil (bir Sphere, bir küp, silindir, koni, bir ekip ve bir düzlem) içerir. Gölgelendiriciye bağlı olarak, belirli şekiller size daha iyi bir önizleme sağlayabilir.

Bir önizleme şekli seçmek için, **gölgelendirici tasarımcı modları** araç çubuğunda istediğiniz şekli seçin.

#### <a name="textures-and-material-parameters"></a>Dokular ve malzeme parametreleri

Birçok gölgelendiriciler, uygulamanızdaki her bir nesne türü için benzersiz bir görünüm oluşturmak üzere dokuların ve malzeme özelliklerine güvenir. Gölgelendiricinizi uygulamanızda nasıl görüneceğine bakmak için, Önizleme oluşturmak üzere kullanılan dokuları ve malzeme özelliklerini uygulamanızda kullanabileceğiniz dokularla ve parametrelerle eşleşecek şekilde ayarlayabilirsiniz.

Farklı dokuyu bir doku kaydına bağlamak veya diğer malzeme parametrelerini değiştirmek için:

1. **Seç** modunda tasarım yüzeyinde boş bir alan seçin. Bu, **Özellikler** penceresinin Genel gölgelendirici özelliklerini görüntülemesine neden olur.

2. **Özellikler** penceresinde, değiştirmek istediğiniz doku ve parametre özellikleri için yeni değerler belirtin.

Aşağıdaki tabloda, değiştirebileceğiniz Gölgelendirici parametreleri gösterilmektedir:

|Parametre|Özellikler|
|---------------|----------------|
|**Doku 1**  -  **Doku 8**|**Erişim**: özelliğin model düzenleyicisinden ayarlaneklenmesine izin vermek için                             **genel** ' e gidin; Aksi takdirde, **özel**.<br /><br /> **Dosya adı**: Bu doku kaydı ile ilişkili doku dosyasının tam yolu.|
|**Malzeme çevresel**|**Erişim**: özelliğin model düzenleyicisinden ayarlaneklenmesine izin vermek için                             **genel** ' e gidin; Aksi takdirde, **özel**.<br /><br /> **Değer**: dolaylı veya çevresel aydınlatma nedeniyle geçerli pikselin dağıtma rengi.|
|**Malzeme dağıtma**|**Erişim**: özelliğin model düzenleyicisinden ayarlaneklenmesine izin vermek için **genel** ' e gidin; Aksi takdirde, **özel**.<br /><br /> **Değer**: geçerli pikselin nasıl doğrudan aydınlatma kullandığını açıklayan bir renk.|
|**Malzeme yanıltıcı**|**Erişim**: özelliğin model düzenleyicisinden ayarlaneklenmesine izin vermek için                              **genel** ' e gidin; Aksi takdirde, **özel**.<br /><br /> **Değer**: kendi kendine sunulan aydınlatma nedeniyle geçerli pikselin renk katkısı.|
|**Malzeme yansımalı**|**Erişim**: özelliğin model düzenleyicisinden ayarlaneklenmesine izin vermek için                              **genel** ' e gidin; Aksi takdirde, **özel**.<br /><br /> **Değer**: geçerli pikselin doğrudan aydınlatmayı nasıl yansıttığını açıklayan bir renk.|
|**Malzeme yansımalı güç**|**Erişim**: özelliğin model düzenleyicisinden ayarlaneklenmesine izin vermek için                             **genel** ' e gidin; Aksi takdirde, **özel**.<br /><br /> **Değer**: geçerli pikselde Yansımalı vurguların yoğunluğunu tanımlayan üs.|

#### <a name="time-based-effects"></a>Zamana dayalı etkiler

Bazı gölgelendiriciler, etkiyi canlandıra zaman tabanlı bir bileşene sahiptir. Efektin işlem içinde nasıl göründüğünü göstermek için, önizlemenin saniyede birkaç kez güncellenmesi gerekir. Varsayılan olarak, Önizleme yalnızca gölgelendirici değiştirildiğinde güncelleştirilir; zamana dayalı etkileri görüntüleyebilmeniz için bu davranışı değiştirmek için gerçek zamanlı işlemeyi etkinleştirmeniz gerekir.

Gerçek zamanlı işlemeyi etkinleştirmek için, gölgelendirici Tasarımcısı araç çubuğunda **gerçek zamanlı işleme**' yı seçin.

#### <a name="examine-the-effect"></a>Etkiyi inceleyin

Birçok gölgelendiriciler, açı veya yönlü aydınlatmayı görüntüleme gibi değişkenlerden etkilenir. Bu değişkenler değiştiğinde efektin nasıl yanıt verdiğini incelemek için önizleme şeklini serbestçe döndürebilir ve gölgelendiricisinin nasıl davranacağını gözlemleyebilirsiniz.

Şekli döndürmek için **alt** tuşuna basın ve basılı tutun ve tasarım yüzeyinde herhangi bir noktayı seçin ve taşıyın.

### <a name="export-shaders"></a>Gölgelendiricileri dışarı aktar

Uygulamanızda bir gölgelendirici kullanabilmeniz için, bunu DirectX 'in anladığı bir biçimde dışarı aktarmanız gerekir.

Gölgelendiricileri HLSL kaynak kodu olarak veya derlenen gölgelendirici bayt olarak dışarı aktarabilirsiniz. HLSL kaynak kodu, *. HLSL* dosya adı uzantısına sahip bir metin dosyasına aktarılmıştır. Gölgelendirici bytecode 'u *. cso* dosya adı uzantısına sahip bir ham ikili dosyaya ya da gölgelendirici bayt kodunu bir diziye kodlayan bir C++ üst bilgi (*. h*) dosyasına aktarılabilir.

Gölgelendiricilerin nasıl dışarı aktarılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md).

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

|Komut|Klavye kısayolları|
|-------------| - |
|**Seçme** moduna geçiş yap|**CTRL** + **G**, **CTRL** + **s**<br /><br /> **S**|
|**Yakınlaştırma** moduna geç|**CTRL** + **G**, **CTRL** + **Z**<br /><br /> **Kadar**|
|**Pan** moduna geç|**CTRL** + **G**, **CTRL** + **P**<br /><br /> **K**|
|Tümünü seç|**CTRL** + **Bir**|
|Geçerli seçimi sil|**Silme**|
|Geçerli seçimi iptal et|**Escape** (**ESC**)|
|Yakınlaştır|**CTRL** + **Fare tekerleği ileri**<br /><br /> Artı Işareti ( **+** )|
|Uzaklaştır|**CTRL** + **Fare tekerleği geriye doğru**<br /><br /> Eksi Işareti ( **-** )|
|Tasarım yüzeyini yukarı kaydır|**Fare tekerleği geriye doğru**<br /><br /> **PageDown**|
|Tasarım yüzeyini aşağı kaydır|**Fare tekerleği ileriye doğru**<br /><br /> **PageUp**|
|Tasarım yüzeyini sola kaydır|**SHIFT** + **Fare tekerleği geriye doğru**<br /><br /> **Fare tekerleği sol**<br /><br /> **Shift ile kaydırma** + **PageDown**|
|Tasarım yüzeyini sağa kaydır|**Shift ile kaydırma** + **Fare tekerleği ileri**<br /><br /> **Fare tekerleği sağ**<br /><br /> **Shift ile kaydırma** + **PageUp**|
|Klavye odağını başka bir düğüme taşıma|Ok  tuşları|
|Klavye odağı olan düğümü seçin (düğümü seçim grubuna ekler)|**Shift ile kaydırma** + **Ara Çubuğu**|
|Klavye odağı olan düğümün seçimini iki durumlu olarak değiştir|**Ctrl tuşunu basılı tutarak** + **Ara Çubuğu**|
|Geçerli seçimi değiştir (düğüm seçilmemişse klavye odağı olan düğümü seçin)|**Boşluk çubuğu**|
|Geçerli seçimi yukarı taşıma|**Shift ile kaydırma** + **Yukarı Ok**|
|Geçerli seçimi aşağı taşıma|**Shift ile kaydırma** + **Aşağı Ok**|
|Geçerli seçimi sola taşıma|**Shift ile kaydırma** + **Sol Ok**|
|Geçerli seçimi sağa taşıma|**Shift ile kaydırma** + **Sağ Ok.**|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Oyunlar ve uygulamalar için 3D varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Dokular, görüntüler, 3B modeller ve gölgelendirici etkileriyle çalışmak için kullanabileceğiniz Visual Studio araçlarına genel bir bakış sağlar.|
|[Görüntü Düzenleyicisi](../designers/image-editor.md)|Dokular ve görüntülerle çalışmak Visual Studio Görüntü Düzenleyicisi'nin nasıl kullanılabını açıklar.|
|[Model Düzenleyicisi](../designers/model-editor.md)|3D modellerle çalışmak Visual Studio Model Düzenleyicisi'nin nasıl kullanılası açıklandı.|
