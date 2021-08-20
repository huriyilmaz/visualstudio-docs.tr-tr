---
title: Görüntü Düzenleyici
description: DirectX uygulama geliştirmesinde Visual Studio ve görüntü kaynaklarını görüntülemek ve değiştirmek için Görüntü Düzenleyicisi ile nasıl çalışabilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 08/10/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 47bcc37f0fe000066f8e2585098601b71e606a12
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133555"
---
# <a name="image-editor"></a>Görüntü düzenleyicisi

Bu makalede doku ve görüntü kaynaklarını görüntülemek  ve değiştirmek Visual Studio Görüntü Düzenleyicisi ile nasıl çalışabilirsiniz?

Görüntü **Düzenleyicisi'ni kullanarak** DirectX uygulama geliştirmesinde kullanılan zengin doku ve görüntü biçimleriyle çalışabilirsiniz. Buna popüler görüntü dosyası biçimleri ve renk kodlamaları desteği, alfa kanalları ve MIP eşlemesi gibi özellikler ve DirectX tarafından desteklenen yüksek oranda sıkıştırılmış, donanım hızlandırmalı doku biçimleri dahildir.

## <a name="supported-formats"></a>Desteklenen biçimler

Görüntü **Düzenleyicisi aşağıdaki** görüntü biçimlerini destekler:

|Biçim adı|Dosya Adı Uzantısı|
|-----------------| - |
|Taşınabilir Ağ Grafikleri|*.png*|
|JPEG|*.jpg*, *.jpeg*, *.jpe*, *.jfif*|
|Doğrudan Çizim Yüzeyi|*.dds*|
|Grafik Değişim Biçimi|*.gif*|
|Bitmap|*.bmp*, *.dib*|
|Etiketli Görüntü Dosyası Biçimi|*.tif*, *.tiff*|
|TGA (Targa)|*.tga*|

## <a name="get-started"></a>başlarken

Bu bölümde, Visual Studio projenize görüntü ekleme ve gereksinimleriniz için yapılandırma açıkmaktadır.

### <a name="add-an-image-to-your-project"></a>Projenize görüntü ekleme

1. Bu **Çözüm Gezgini,** görüntüyü eklemek istediğiniz projenin kısayol menüsünü açın ve ardından Yeni Öğe **Ekle'yi**  >  **seçin.**

2. Yeni Öğe **Ekle iletişim** kutusundaki Yüklü altında  **Grafikler'i** ve ardından görüntü için uygun bir dosya biçimi seçin.

   > [!NOTE]
   > Yeni Öğe Ekle iletişim kutusunda **Grafik** kategorisini görmüyorsanız Görüntü ve **3D model** düzenleyicileri bileşenini yüklemeniz gerekir.  İletişim kutusunu kapatın ve menü **çubuğundan** Araçlar Araçları ve Özellikleri  >   Al'ı seçerek Visual Studio Yükleyicisi.  Bağımsız **bileşenler sekmesini** ve ardından Oyunlar ve Grafikler kategorisi altındaki Görüntü ve **3D model** **düzenleyicileri bileşenini** seçin. **Değiştir'i seçin.**
   >
   > ![Görüntü ve 3D model düzenleyicileri bileşeni](media/image-3d-model-editors-component.png)

   Gereksinimlerinize göre bir dosya biçimi seçme hakkında bilgi için [bkz. Görüntü biçimini seçme.](#choose-the-image-format)

3. Görüntü **dosyasının** Adını ve **oluşturulacak** konumu belirtin.

4. **Ekle** düğmesini seçin.

### <a name="choose-the-image-format"></a>Görüntü biçimini seçin

Görüntüyü nasıl kullanmayı planlasanız, belirli dosya biçimleri diğerlerine göre daha uygun olabilir. Örneğin, bazı biçimler, saydamlık veya belirli bir renk biçimi gibi ihtiyacınız olan bir özelliği desteklemeyebilirsiniz. Bazı biçimler, planladnız görüntü içeriği türü için uygun sıkıştırma sağlamayabilirsiniz.

Aşağıdaki bilgiler, İhtiyaçlarınızı karşılayacak bir görüntü biçimi seçmenize yardımcı olabilir:

**Bit Eşlem Görüntüsü (.bmp)**

Bit eşlem görüntüsü biçimi. 24 bit rengi destekleyen sıkıştırılmamış bir görüntü biçimi. Bit eşlem biçimi saydamlığı desteklemez.

**GIF Görüntüsü (.gif)**

Grafik Değişim Biçimi (GIF) görüntü biçimi. En fazla 256 rengi destekleyen LZW sıkıştırılmış kayıpsız görüntü biçimi. Önemli miktarda renk ayrıntısı olan fotoğraflar ve görüntüler için uygun değildir, ancak yüksek düzeyde renk tutarlılığı olan düşük renkli görüntüler için iyi sıkıştırma oranları sağlar.

**JPG Görüntüsü (.jpg)**

Joint Photographic Experts Group (JPEG) görüntü biçimi. Yüksek oranda sıkıştırılmış, kayıplı bir görüntü biçimi, 24 bit rengi destekler ve yüksek düzeyde renk tutarlılığı olan görüntülerin genel amaçlı sıkıştırması için uygundur.

**PNG Görüntüsü (.png)**

Taşınabilir Ağ Grafikleri (PNG) görüntü biçimi. 24 bit renk ve alfa saydamlığı destekleyen orta düzeyde sıkıştırılmış kayıpsız görüntü biçimi. Hem doğal hem de yapay görüntüler için uygundur, ancak JPG veya GIF gibi kayıplı biçimler kadar iyi sıkıştırma oranları sağlamaz.

**TIFF Görüntüsü (.tif)**

Etiketli Görüntü Dosyası Biçimi (TIFF veya TIF) görüntü biçimi. Çeşitli sıkıştırma düzenlerini destekleyen esnek bir görüntü biçimi.

**DDS Dokusu (.dds)**

DirectDraw Surface (DDS) doku biçimi. 24 bit renk ve alfa saydamlığı destekleyen, yüksek oranda sıkıştırılmış, kayıplı doku biçimi. Sıkıştırma oranları 8:1'e kadar yüksek olabilir. Grafik donanımlarında sıkıştırılmış olan S3 Doku sıkıştırmasını temel alan bir sistemdir.

**TGA Görüntüsü (.tga)**

Truevision Grafik Bağdaştırıcısı (TGA) görüntü biçimi (Targa olarak da bilinir). Hem renk eşlenmiş (renk paleti) hem de 24 bit'e kadar renk ve alfa saydamlığı içeren doğrudan renk görüntülerini destekleyen, RLE ile sıkıştırılmış kayıpsız görüntü biçimi. Önemli miktarda renk ayrıntısı olan fotoğraflar ve görüntüler için uygun değildir, ancak aynı renklerin uzun sürelerine sahip görüntüler için iyi sıkıştırma oranları sağlar.

### <a name="configure-the-image"></a>Görüntüyü yapılandırma

Oluşturduğunuz görüntüyle çalışmaya başlamadan önce varsayılan yapılandırmasını değiştirebilirsiniz. Örneğin, boyutlarını veya kullandığı renk biçimini değiştirebilirsiniz. Bu özellikleri ve görüntünün diğer özelliklerini yapılandırma hakkında bilgi için bkz. [Görüntü özellikleri.](#image-properties)

> [!NOTE]
> Çalışmanızı kaydetmeden önce, belirli bir renk biçimi **kullanmak** için Renk Biçimi özelliğini ayarlamayı unutmayın. Dosya biçimi sıkıştırmayı destekliyorsa, dosyayı ilk kez kaydedecek veya Farklı Kaydet'i seçtiğiniz zaman sıkıştırma ayarlarını **yapabilirsiniz.**

## <a name="work-with-the-image-editor"></a>Görüntü Düzenleyicisi ile çalışma

Bu bölümde, dokuları ve görüntüleri **değiştirmek için** Görüntü Düzenleyicisi'nin nasıl kullanımı açıklanacak.

Görüntü Düzenleyicisi'nin durumunu etkileyen **komutlar,** gelişmiş komutlarla birlikte Görüntü **Düzenleyicisi Modu** araç çubuğunda bulunur. Araç çubuğu, Görüntü Düzenleyicisi tasarım yüzeyinin en üst **kenarı üzerinde** bulunur. Çizim araçları, Görüntü Düzenleyicisi tasarım **yüzeyinin** en sol kenarı boyunca Görüntü Düzenleyicisi **araç çubuğunda** bulunur.

### <a name="image-editor-mode-toolbar"></a>Görüntü Düzenleyicisi Modu araç çubuğu

![Visual Studio'de Görüntü Düzenleyicisi modu araç Visual Studio](../designers/media/digit-tre-modal-toolbar.png)

Aşağıdaki tabloda, Görüntü Düzenleyicisi  Modu araç çubuğundaki öğeler, soldan sağa doğru görünme sırasına göre listelenmiştir:

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Seç**|Görüntünün dikdörtgen bir bölgesi seçimine olanak sağlar. Bir bölgeyi seçdikten sonra kesebilir, kopyalayıp, hareket ettirebilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Düzensiz Seçim**|Görüntünün düzensiz bir bölgesi seçimine olanak sağlar. Bir bölgeyi seçdikten sonra kesebilir, kopyalayıp, hareket ettirebilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Wand Selection**|Bir görüntünün benzer renkli bir bölgenin seçimini sağlar. Tolerans *(diğer* bir ifadeyle, benzer olarak kabul edildikleri bitişik renkler arasındaki en büyük fark) daha küçük veya daha geniş bir benzer renk aralığı içerecek şekilde yalıtıldığında. Bir bölgeyi seçdikten sonra kesebilir, kopyalayıp, hareket ettirebilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Kaydır**|Görüntünün pencere çerçevesine göre hareketini sağlar. Pan **modunda,** görüntüde bir nokta seçin ve ardından bu noktayı hareket ettirin.<br /><br /> Ctrl tuşuna basarak **ve** basılı tutarak Pan modunu geçici **olarak etkinleştirebilirsiniz.**|
|**Zoom**|Pencere çerçevesine göre daha fazla veya daha az görüntü ayrıntısı görüntüsünü sağlar. Yakınlaştırma **modunda,** görüntüde bir nokta seçin ve sonra yakınlaştırmak için görüntüyü sağa veya aşağı hareket ettirin ya da uzaklaştırın ya da sola ya da yukarıya hareket ettirin.<br /><br /> Fare tekerleğini kullanırken **Ctrl** tuşunu basılı tutarak veya artı işaretine ( ) veya eksi işaretine ( ) basarak yakınlaştırabilir **+** veya **-** uzaklaştırabilirsiniz.|
|**Gerçek Boyuta Yakınlaştırma**|Görüntünün pikselleri ile ekranın pikselleri arasında 1:1 ilişkisi kullanarak görüntüyü görüntüler.|
|**Sığdırmak için Yakınlaştır**|Pencere çerçevesinde tam görüntüyü görüntüler.|
|**Genişliğe Yakınlaştırma**|Pencere çerçevesinde görüntünün tam genişliğini görüntüler.|
|**Kılavuz**|Piksel sınırlarını gösteren kılavuzu etkinleştirme veya devre dışı bırakma. Siz görüntüyü yakınlaştırana kadar kılavuz görüne görünebilir.|
|**Sonraki MIP Düzeyini Görüntüle**|Bir MIP eşleme zincirinde bir sonraki büyük MIP düzeyini etkinleştirir. Etkin MIP düzeyi tasarım yüzeyinde görüntülenir. Bu öğe yalnızca MIP düzeylerine sahip dokular için kullanılabilir.|
|**Önceki MIP Düzeyini Görüntüle**|Bir MIP eşleme zincirinde bir sonraki küçük MIP düzeyini etkinleştirir. Etkin MIP düzeyi tasarım yüzeyinde görüntülenir. Bu öğe yalnızca MIP düzeylerine sahip dokular için kullanılabilir.|
|**Kırmızı Kanal**<br /><br /> **Yeşil Kanal**<br /><br /> **Mavi Kanal**<br /><br /> **Alfa Kanalı**|Belirli bir renk kanalını etkinleştirme veya devre dışı bırakma. **Not:**  Renk kanallarını sistematik olarak etkinleştirerek veya devre dışı bırakarak, bunlardan biri veya daha fazlası ile ilgili sorunları yalıtabilirsiniz. Örneğin, yanlış alfa saydamlığını tanımlayabilirsiniz.|
|**Arka Plan**|Görüntünün saydam bölümleri aracılığıyla arka plan görüntüsünü etkinleştirme veya devre dışı bırakma. Bu seçeneklerden birini seçerek arka plan nasıl görüntülenmiyor yapılandırabilirsiniz:<br /><br /> **Dama**<br /> Arka planı denetleyici düzeni olarak görüntülemek için belirtilen arka plan rengiyle birlikte yeşil renk kullanır. Bu seçeneği, görüntünün saydam bölümlerini daha belirgin hale etmeye yardımcı olmak için kullanabilirsiniz.<br /><br /> Beyaz Arka Plan<br /> Arka planı görüntülemek için beyaz rengi kullanır.<br /><br /> Siyah Arka Plan<br /> Arka planı görüntülemek için siyah rengi kullanır.<br /><br /> Arka Plana Animasyon Animasyonu<br /> Denetleyici panosu desenini yavaş kaydırıyor. Bu seçeneği, görüntünün saydam bölümlerini daha belirgin hale etmeye yardımcı olmak için kullanabilirsiniz.|
|**Özellikler**|Alternatif olarak Özellikler penceresini açar **veya** kapatır.|
|**Gelişmiş**|Ek komutlar ve seçenekler içerir.<br /><br /> **Filtreler**<br /><br /> Çeşitli yaygın görüntü filtreleri sağlar: **Siyah ve Beyaz**, **Gölge,** **Parlak**, **Darken,** **Kenar Algılama**, **Emboss,** **Renkleri** Ters **Çevir,** **Sepya Rengi**, ve **Devam Et.**<br /><br /> **Grafik Altyapıları**<br /><br /> **D3D11 ile işleme**<br /> Görüntü Düzenleyicisi tasarım yüzeyini işlemek  için Direct3D 11 kullanır.<br /><br /> **D3D11WARP ile işleme**<br /> Görüntü Düzenleyicisi tasarım yüzeyini işlemek Windows Gelişmiş Tarama Platformu 'Windows Direct3D 11'i kullanır. <br /><br /> **Araçlar**<br /><br /> **Yatay Çevirme**<br /> Görüntüyü yatay ekseninin veya x ekseninin etrafında yer değiştirme.<br /><br /> **Dikey Çevirme**<br /> Görüntüyü dikey ekseninin veya y ekseninin çevresini dolar.<br /><br /> **Mips Oluşturma**<br /> Bir görüntü için MIP düzeyleri üretir. MIP düzeyleri zaten varsa, en büyük MIP düzeyinden yeniden oluşturulur. Daha küçük MIP düzeylerinde yapılan tüm değişiklikler kaybolur. Oluşturulan MIP düzeylerini kaydetmek için *.dds* biçimini kullanarak görüntüyü kaydetmeniz gerekir.<br /><br /> **Görünüm**<br /><br /> **Kare Hızı**<br /> Etkinleştirildiğinde, çerçeve oranını tasarım yüzeyinin sağ üst köşesinde görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır. **İpucu:** Son komutu yeniden **çalıştırmak** için Gelişmiş düğmesini seçebilirsiniz.|

### <a name="image-editor-toolbar"></a>Görüntü Düzenleyicisi araç çubuğu

![Görüntü Düzenleyicisi araç çubuğu](../designers/media/digit-tre-toolbar.png)

Aşağıdaki tabloda, Görüntü Düzenleyicisi  araç çubuğundaki öğeler yukarıdan aşağıya doğru görünme sırasına göre listelenmiştir:

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Kalem**|Diğer adlı bir vuruş çizmek için etkin renk seçimini kullanır. Özellikler penceresinde darbenin rengini ve kalınlığını **ayarlayabilirsiniz.**|
|**Fırça**|Diğer addan koruma vuruşu çizmek için etkin renk seçimini kullanır. Özellikler penceresinde darbenin rengini ve kalınlığını **ayarlayabilirsiniz.**|
|**Airbrush**|Etkin renk seçimini kullanarak görüntüyle bir araya gelir ve zaman işlevi olarak daha doygun hale gelir. Özellikler penceresinde darbenin rengini ve kalınlığını **ayarlayabilirsiniz.**|
|**Damlalık**|Etkin renk seçimini seçili pikselin rengine ayarlar.|
|**Doldur**|Görüntünün bir bölgeyi doldurmak için etkin renk seçimini kullanır. Etkilenen bölge, dolgu uygulandığı piksel olarak tanımlanır ve bu bölgeye aynı renge ve aynı renge sahip piksellerle bağlanan her piksel ile birlikte tanımlanır. Dolgu etkin bir seçim içinde uygulanırsa etkilenen bölge seçimle kısıtlanmış durumdadır.<br /><br /> Varsayılan olarak, etkin renk seçimi görüntünün etkilenen bölgesiyle alfa bileşenine göre karıştırıldı. Etkin renk seçimini kullanarak etkilenen bölgenin üzerine yazmak için dolgu aracını kullanarak **Shift** tuşuna basın ve basılı tutun.|
|**Silgi**|Görüntü bir alfa kanalını destekliyorsa pikselleri tamamen saydam renge ayarlar. Aksi takdirde pikselleri etkin arka plan rengine ayarlar.|
|**Çizgi,** **Dikdörtgen,** **Yuvarlanmış Dikdörtgen**, **Üç Nokta**|Görüntüye bir şekil çizer. Özellikler penceresinde ana hat rengini ve  kalınlığını ayarlayabilirsiniz.<br /><br /> Eşit genişlik ve yüksekliğe sahip bir temel öğe çizmek için, çizimde **Shift** tuşuna basın ve basılı tutun.|
|**Metin**|Metin çizmek için ön plan renk seçimini kullanır. Arka plan rengi, arka plan rengi seçimi tarafından belirlenir. Saydam bir arka plan için arka plan renk seçiminin alfa değeri 0'dır. Metin bölgesi etkin durumdayken, Metnin diğer addan koruma vuruşu ile çizilecek olup olmadığını ve Özellikler penceresinde Değer , Yazı Tipi, Boyut **ve** stil(**Kalın**, **İtalik** veya Altı Çizili) metnini de **ayarabilirsiniz.**   Metin bölgesi artık etkin olmadığı zaman metnin içeriği ve görünümü son hale getirildi.|
|**Döndür**|Görüntüyü saat yönünde 90 derece döndürür.|
|**Döşeme**|Görüntüyü etkin seçime göre kırpıyor.|

### <a name="work-with-mip-levels"></a>MIP düzeyleriyle çalışma

DirectDraw Surface (*.dds)* gibi bazı görüntü biçimleri doku-alanı Ayrıntı Düzeyi (LOD) için MIP düzeylerini destekler. MIP düzeyleri oluşturma ve bu düzeylerle çalışma hakkında daha fazla bilgi için [bkz. Nasıl 2012: MIP düzeyleri oluşturma ve değiştirme](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="work-with-transparency"></a>Saydamlık ile çalışma

DirectDraw Surface (*.dds)* gibi bazı görüntü biçimleri saydamlığı destekler. Kullandığınız araça bağlı olarak saydamlığı çeşitli yollarla kullanabilirsiniz. Renk seçiminin saydamlık düzeyini belirtmek için Özellikler **penceresinde** renk seçiminin **A** (alfa) bileşenini ayarlayın.

Aşağıdaki tabloda, farklı türlerde araçların saydamlığın nasıl uygulandığını denetlemesi açık almaktadır:

|Araç|Açıklama|
|----------|-----------------|
|**Kalem,** **Fırça,** **Airbrush,** **Çizgi,** **Dikdörtgen,** **Yuvarlanmış Dikdörtgen,** **Üç Nokta**, **Metin**|Etkin renk seçimini görüntüyle birlikte karıştırmak  için Özellikler  penceresinde Kanallar özellik grubunu genişletin, **Alfa** kanalında **Çiz** onay kutusunu ayarlayın ve ardından normal şekilde çizin.<br /><br /> Etkin renk seçimini kullanarak çizmek ve görüntünün alfa değerini olduğu gibi bırakmak için Alfa kanalının **Çiz** **onay** kutusunu temizleyin ve ardından normal şekilde çizin.|
|**Doldur**|Etkin renk seçimini görüntüyle birlikte karıştırmak için, doldurulacak alanı seçmeniz gerekir.<br /><br /> Görüntünün üzerine yazmak için etkin renk seçimini (alfa kanalının değeri dahil) kullanmak için **Shift** tuşuna basın ve ardından doldurulacak alanı seçin.|

### <a name="image-properties"></a>Görüntü özellikleri

Görüntünün çeşitli **özelliklerini** belirtmek için Özellikler penceresini kullanabilirsiniz. Örneğin, görüntüyü yeniden boyutlandırmak için genişlik ve yükseklik özelliklerini ayarlayın.

Aşağıdaki tabloda görüntü özellikleri açık almaktadır:

|Özellik|Açıklama|
|--------------|-----------------|
|Width|Görüntünün genişliği.|
|Height|Görüntünün yüksekliği.|
|Piksel Başına Bit|Her pikseli temsil eden bit sayısı. Bu özelliğin değeri görüntünün **Renk Biçimine** bağlıdır.|
|Saydam Seçim|Seçim katmanını ana görüntüyle birlikte, seçim katmanının alfa değerine göre karıştırmak için **True;** aksi takdirde **False olur.** Bu öğe yalnızca alfa desteği olan görüntüler için kullanılabilir.|
|Biçimlendir|Görüntünün renk biçimi. Görüntü biçimine bağlı olarak çeşitli renk biçimleri belirtebilirsiniz. Renk biçimi, görüntüye dahil edilen renk kanallarının sayısını ve türlerini ve çeşitli kanalların boyutunu ve kodlamasını tanımlar.|
|Mip Düzeyi|Etkin MIP düzeyi. Bu öğe yalnızca MIP düzeylerine sahip dokular için kullanılabilir.|
|Mip Düzeyi Sayısı|Görüntüde miP düzeylerinin toplam sayısı. Bu öğe yalnızca MIP düzeylerine sahip dokular için kullanılabilir.|
|Çerçeve Sayısı|Görüntüdeki toplam kare sayısı. Bu öğe yalnızca doku dizilerini destekleyen görüntüler için kullanılabilir.|
|Çerçeve|Geçerli çerçeve. Yalnızca ilk kare görünüme sahip olabilir; Görüntü kaydedilebilirken diğer tüm kareler kaybolur.|
|Derinlik Dilimi Sayısı|Görüntüde yer alan derinlik dilimlerinin toplam sayısı. Bu öğe yalnızca birim dokularını destekleyen görüntüler için kullanılabilir.|
|Derinlik Dilimi|Geçerli derinlik dilimi. Yalnızca ilk dilim görünüme sahip olabilir; Görüntüyü kaydeden diğer tüm dilimler kaybolur.|

> [!NOTE]
> Döndür **özelliği tüm** araçlara ve seçili bölgelere uygulandığı için, özellikler penceresinin alt kısmında her **zaman** diğer araç özellikleriyle birlikte görünür. **Başka bir** seçim veya etkin araç yoksa görüntünün tamamı örtülü olarak seçildiğinden döndür seçeneği her zaman görüntülenir. Döndür özelliği hakkında daha **fazla bilgi için** bkz. Araç [özellikleri.](#tool -properties)

### <a name="resize-images"></a>Görüntüleri yeniden boyutlandırma

Bir görüntüyü yeniden boyutlandırmanın iki yolu vardır. Her iki durumda da Görüntü **Düzenleyicisi,** görüntüyü yeniden örneklemek için çift ilişkilendirme kullanır.

- Özellikler **penceresinde** Genişlik ve Yükseklik özellikleri için **yeni** **değerler** belirtin.

- Görüntünün tamamını seçin ve kenarlığı işaretleyicilerini kullanarak görüntüyü yeniden boyutlandırabilirsiniz.

### <a name="selected-regions"></a>Seçili bölgeler

Görüntü **Düzenleyicisi'nde yapılan seçimler** görüntünün etkin olan bölgelerini tanımlar. Etkin bölgeler araçlardan ve dönüşümlerden etkilenir. Etkin bir seçim olduğunda, seçilen bölgenin dışındaki alanlar çoğu araç ve dönüştürmeden etkilenmez. Etkin bir seçim yoksa görüntünün tamamı etkindir.

Çoğu araç **(Kalem,** **Fırça,** **Airbrush,** **Fill,** **Silgi** ve 2D temel öğeler) ve dönüştürmeler (**Döndürme,** **Kırpma,** Renkleri Ters **Çevirme,** Yatay Çevirme **ve** Dikey **Çevirme)** etkin seçimle kısıtlanmış veya tanımlanmıştır. Ancak, bazı araçlar **(Eyedropper** ve **Text**) ve dönüştürmeler (**Mips** Oluştur) herhangi bir etkin seçimden etkilenmez. Bu araçlar her zaman görüntünün tamamı etkin seçim gibi davranır.

Bir bölgeyi seçerken, orantılı (kare) seçim yapmak için **Shift** tuşuna basarak ve basılı tutarak. Aksi takdirde seçim kısıtlanmaz.

#### <a name="resize-selections"></a>Seçimleri yeniden boyutlandırma

Bir bölgeyi seçdikten sonra, seçim işaretçisi boyutunu değiştirerek bölgeyi veya görüntü içeriğini yeniden boyutlandırabilirsiniz. Seçilen bölgeyi yeniden boyutlandırırken, seçilen bölgenin davranışını yeniden boyutlandırırken değiştirmek için aşağıdaki değiştirici anahtarları kullanabilirsiniz:

**Ctrl** - Seçilen bölgenin içeriğini yeniden boyutlandırılmadan önce kopyalar. Bu, kopya yeniden boyutlandırılırken özgün görüntüyü olduğu gibi bırakır.

**Shift** - Seçilen bölgeyi özgün boyutuyla orantılı olarak yeniden boyutlandırılır.

**Alt** - Seçim bölgesi boyutunu değiştirir. Bu, görüntüyü değiştirilmeden bırakır.

Aşağıdaki tabloda geçerli değiştirici anahtar birleşimleri açık almaktadır:

|Ctrl|Shift|Alt|Açıklama|
|----------|-----------|---------|-----------------|
||||Seçilen bölgenin içeriğini yeniden boyutlandırıyor.|
||**Shift**||Seçilen bölgenin içeriğini orantılı olarak yeniden boyutlandırıyor.|
|||**Alt**|Seçilen bölgeyi yeniden boyutlandırıyor. Bu, yeni bir seçim bölgesi tanımlar.|
||**Shift**|**Alt**|Seçilen bölgeyi orantılı olarak yeniden boyutlandırıyor. Bu, yeni bir seçim bölgesi tanımlar.|
|**Ctrl**|||Seçilen bölgenin içeriğini kopyalar ve yeniden boyutlandırılır.|
|**Ctrl**|**Shift**||Seçilen bölgenin içeriğini kopyalar ve ardından orantılı olarak yeniden boyutlandırılır.|

### <a name="tool-properties"></a>Araç özellikleri

Bir araç seçiliyken, görüntüyü nasıl **etkilediğine** ilişkin ayrıntıları belirtmek için Özellikler penceresini kullanabilirsiniz. Örneğin Kalem aracının kalınlığını veya **Fırça** aracının rengini **ayarlayabilirsiniz.**

Hem ön plan rengini hem de arka plan rengini ayarlayın. Her ikisi de kullanıcı tanımlı opaklık sağlamak için bir alfa kanalını destekler. Ayarlar tüm araçlar için geçerlidir. Fare kullanıyorsanız, sol fare düğmesi ön plan rengine, sağ fare düğmesi ise arka plan rengine karşılık gelir.

Aşağıdaki tabloda araç özellikleri açık almaktadır:

|Araç|Özellikler|
|----------|----------------|
|Tüm araçlar ve seçimler|**Döndürme**<br /> Seçim veya araç etkisinin saat yönünde döndürülecek miktarını derece olarak tanımlar.|
|**Kalem,** **Fırça,** **Airbrush,** **Silgi**|**Kalınlık**<br /> Araçtan etkilenen alan boyutunu tanımlar.|
|**Metin**|**Kenar yumuşatma**<br /> Diğer ad kenarlara sahip olan metinleri çizer. Bu metin daha düzgün bir görünüm sağlar.<br /><br /> **Değer**<br /> Çizilecek metin.<br /><br /> **Yazı tipi**<br /> Metni çizmek için kullanılan yazı tipi.<br /><br /> **Boyut**<br /> Metnin boyutu.<br /><br /> **Kalın**<br /> Yazı tipini kalın yapar.<br /><br /> **İtalik**<br /> Yazı tipini italik yapar.<br /><br /> **Altı çizili**<br /> Yazı tipini altı çizili yapar.|
|**2D Temel**|**Kenar yumuşatma**<br /> Diğer adlara sahip kenarlara sahip ilkelleri çizer. Bu, onlara daha sorunsuz bir görünüm sağlar.<br /><br /> **Kalınlık**<br /> Temel öğenin sınırını oluşturan çizginin kalınlığını tanımlar.<br /><br /> **Radius X**<br /> (Yalnızca yuvarlanmış dikdörtgen) İlkelin üst ve alt kenarları için yuvarlama yarıçapını tanımlar.<br /><br /> **Radius Y**<br /> (Yalnızca yuvarlanmış dikdörtgen) İlkelin sol ve sağ kenarları için yuvarlama yarıçapını tanımlar.|
|**Kalem,** **Fırça,** **Airbrush**, **2D Temel**|**Kanallar**<br /> Görüntüleme ve çizim için belirli renk kanallarını etkinleştirme veya devre dışı bırakma. Görünüm **belirli** bir renk kanalı için ayarlanırsa, bu kanal görüntüde görünür; aksi takdirde, görünür değildir. **Draw belirli** bir renk kanalı için ayarlanırsa, bu kanal çizim işlemleri tarafından etkilenir; aksi takdirde, değildir.|
|**Wand Selection**, **Fill**|**Tolerans**<br /> Daha az veya daha fazla benzer rengin etkilenen veya seçilen bölgenin bir parçası olarak kabul edildiklerine bitişik renkler arasındaki en büyük farkı tanımlar. Varsayılan olarak, değer 32'dir, yani özgün rengin 32 gölgelik (açık veya koyu) içindeki bitişik piksellerin bölgenin bir parçası olarak kabul edilir.|

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

|Komut|Klavye kısayolları|
|-------------| - |
|Seçim **moduna** geçme|**S**|
|Yakınlaştırma **moduna** geçme|**Z**|
|Kaydırma **moduna** geçme|**K**|
|Tümünü seç|**Ctrl tuşunu basılı tutarak** + **A**|
|Geçerli seçimi sil|**Silme**|
|Geçerli seçimi iptal et|**Esc** (kaçış)|
|Yakınlaştır|**Ctrl tuşunu basılı tutarak** + **Fare tekerleği ileri**<br /><br /> **Ctrl tuşunu basılı tutarak** + **PageUp**<br /><br /> Artı İşareti ( **+** )|
|Uzaklaştır|**Ctrl tuşunu basılı tutarak** - **Fare tekerleği geriye doğru**<br /><br /> **Ctrl tuşunu basılı tutarak** - **PageDown**<br /><br /> Eksi İşareti ( **-** )|
|Görüntüyü yukarı kaydır|**Fare tekerleği geriye doğru**<br /><br /> **PageDown**|
|Görüntüyü aşağı kaydır|**Fare tekerleği ileriye doğru**<br /><br /> **PageUp**|
|Görüntüyü sola kaydır|**Shift ile kaydırma** + **Fare tekerleği geriye doğru**<br /><br /> **Fare tekerleği sol**<br /><br /> **Shift ile kaydırma** + **PageDown**|
|Görüntüyü sağa kaydır|**Shift ile kaydırma** + **Fare tekerleği ileri**<br /><br /> **Fare tekerleği sağ**<br /><br /> **Shift ile kaydırma** + **PageUp**|
|Gerçek boyuta yakınlaştırma|**Ctrl tuşunu basılı tutarak** + **0** (sıfır)|
|Görüntüyü pencereye sığdır|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **F**|
|Görüntüyü pencere genişliğine Sığdır|**CTRL** + **G**, **CTRL** + **i**|
|Kılavuza geç|**CTRL** + **G**, **CTRL** + **g**|
|Görüntüyü geçerli seçime Kırp|**CTRL** + **G**, **CTRL** + **C**|
|Sonrakini görüntüle (daha yüksek ayrıntı) MıP düzeyi|**CTRL** + **G**, **CTRL** + **6**|
|Öncekini görüntüle (düşük ayrıntı) MıP düzeyi|**CTRL** + **G**, **CTRL** + **7**|
|Kırmızı renk kanalını değiştirme|**CTRL** + **G**, **CTRL** + **1**|
|Yeşil renk kanalını aç|**CTRL** + **G**, **CTRL** + **2**|
|Mavi renk kanalını aç|**CTRL** + **G**, **CTRL** + **3**|
|Alfa (saydam) kanalını değiştirme|**CTRL** + **G**, **CTRL** + **4**|
|Alfa dama tahtası düzenine geç|**CTRL** + **G**, **CTRL** + **B**|
|Düzensiz seçim aracına geç|**L**|
|Değnek seçim aracına geç|**M**|
|Kurşun Kalem aracına geç|**P**|
|Fırça aracına geç|**Kenarı**|
|Fill aracına geç|**Vadeli**|
|Silgi aracına geç|**A**|
|Metin aracına geç|**T**|
|Renk seç (damlalık) aracına geç|**Kaydedemiyorum**|
|Etkin seçimi ve içeriğini taşıyın.|**Ok** tuşları.|
|Etkin seçimi ve içeriğini yeniden boyutlandırın.|**CTRL** + **Ok** tuşları|
|Etkin seçimi taşıyın, ancak içeriğini değil.|**SHIFT** + **Ok** tuşları|
|Etkin seçimi yeniden boyutlandırın, ancak içeriğini değil.|**SHIFT** + **CTRL** + **Ok** tuşları|
|Geçerli katmanı Yürüt|**Döndürülmesini**|
|Araç kalınlığını azalt|**[**|
|Araç kalınlığını artır|**]**|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Oyunlar ve uygulamalar için 3B varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|dokular ve görüntüler, 3b modeller ve gölgelendirici efektleri gibi grafik varlıklarıyla çalışmak için Visual Studio kullanabileceğiniz araçlara genel bir bakış sağlar.|
|[Model düzenleyicisi](../designers/model-editor.md)|3b modellerle çalışmak için Visual Studio Model düzenleyicisi ' nin nasıl kullanılacağını açıklar.|
|[Gölgelendirici tasarımcısı](../designers/shader-designer.md)|gölgelendiricilerle çalışmak için Visual Studio gölgelendirici tasarımcısının nasıl kullanılacağını açıklar.|
