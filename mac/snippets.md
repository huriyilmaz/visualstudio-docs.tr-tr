---
title: Kod Parçacıkları
description: Mac için Visual Studio'da etkili bir şekilde programlamak için kod parçacıkları nasıl kullanılır?
author: cobey
ms.author: cobey
ms.date: 02/07/2019
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 1dacc935549d738ff1b5e84c3ac4420c343155fd
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "68787694"
---
# <a name="code-snippets"></a>Kod parçacıkları

Kod parçacıkları, genellikle _kod şablonları_olarak adlandırılır, kod ekleme ve kod önceden yazılmış blokların düzenlenmesine izin olarak verimli programlama için yararlıdır. Kod parçacıkları kullanmak, hızlı bir şekilde ortak desenler eklemek, hatta geliştirici olarak sözdiziminden emin değilken yeni desenler öğrenmek için uygun olabilir. C#, F#, HTML, XML, Python ve Razor için sağlanan şablonlar vardır.

Bu bölümde, koddaki parçacıklar nasıl oluşturulup eklenilip kullanılacağı açıklanmaktadır.

## <a name="inserting-a-snippet"></a>Parçacık ekleme

Kod parçacıkları eklemenin bazı farklı yolları vardır ve bunlardan bazıları aşağıda açıklanmıştır:

- **Sekme Genişletme** &ndash; Şablon adını yazmaya başlayın, listeden seçin ve eklemek için **Sekme**, **Sekme** tuşuna basın:

  ![Kodda Sekme Genişletme](media/source-editor-image13.png)

- **Araç Kutusu** &ndash; Tüm kod parçacıklarının listesini görüntülemek için araç kutusu pedini kullanın. Araç kutusundaki herhangi bir şablonu kaynak kodundaki doğru konuma sürükleyin:

  [![Araç Kutusundaki Kod parçacıkları](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **Şablonlar komutunu** &ndash; ekle şu anda şablon eklemek için varsayılan anahtar bağlama kümesi yoktur. Bir tane oluşturmak için **Visual Studio > Tercihleri > Anahtar Bağlamaları'na** göz atın ve arama yapın. `template` Bu, Bağlamayı Edit alanına istenen anahtar bağlamayı eklemenize olanak tanır, ardından **Uygula'yı**tıklatın:

  ![Şablon Uycama komutu](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>Yeni bir şablon oluşturma

Kullanabileceğiniz ve düzenlediğiniz çeşitli dillerde varolan birçok şablon olsa da, Visual Studio > **Tercihleri > Metin Editörü > Kod Parçacıkları'na**yönlendirilerek yeni şablonlar da eklenebilir:

![Yeni şablon uy](media/source-editor-image12.png)

Parçacıklar oluşturmak veya bunları yeniden oluşturmak için **Ekle** veya **Edit** düğmelerine basın.

## <a name="keywords-in-code-snippets"></a>Kod parçacıklarındaki anahtar kelimeler

Düzenleyiciye bir kod parçacığı takıldıktan sonra, tanımlanan anahtar kelimeler vurgulanır ve aralarında sekme ler tarafından düzenlenebilir. Anahtar kelimeler kod snippet'inde bir "değişken" gibi çalışır `$` ve anahtar kelimenin adından önce ve sonra bir dolar işareti yerleştirilerek tanımlanır. 

**Edit şablonu** penceresi aşağıda gösterilmiştir ve `prop` yerleşik parçacık düzenlemiştir. Parçacık, pencerenin &ndash; `$type$` `$name$` &ndash; sağ tarafında başka özellikler (varsayılan değer ve araç ucu gibi) ayarlanabilen iki anahtar kelime içerir:

![Şablon pencereyi edin](media/source-editor-image12z.png)

Aşağıdaki alanlar bir parçacık tanımlamak için kullanılır:

- **Kısayol** &ndash; Parçacık eklemek için kullanıcının yazdığı metin.
- **Grup** &ndash; Parçacıkları, bu değer kullanılarak snippet içerik menüsünde birlikte gruplandırılır.
- **Açıklama** &ndash; Snippet amacı nın açıklaması.
- **Mime** &ndash; Denetimler hangi dosya türlerinde snippet kullanılabilir.
- **Genişletilebilir şablon,** &ndash; kısayolu yazarak imleçte parçacık eklenebilmesi için bunun kontrol edilebilmesini sağlayın.
- **Şablonla** &ndash; surround mı Surround'taki bu kısayolu editördeki içerik **menüsüyle** listelemek için bu seçeneği işaretleyin.
- **Şablon metni** &ndash; Düzenleyiciye eklenecek gerçek parçacık. Anahtar kelime yer tutucular, örneğin dolar işaretleri yle bir belirteci çevreleyerek tanımlanabilir. `$type$`.
- **Anahtar kelime özellik paneli** &ndash; Pencerenin sağ tarafında, bir anahtar kelime `type`(örneğin) seçmek ve varsayılan değer ve araç ipucu gibi özellikleri düzenlemek için üstteki açılır listeyi kullanın.

## <a name="using-keywords-in-the-editor"></a>Editörde anahtar kelimeleri kullanma

Yukarıda tanımlanan gibi anahtar kelimeleriçeren bir parça kullanmak için kısayolu yazın ve **Sekme'ye** iki kez basın ve parçacık içeriği imlecin yanına eklenir:

![Anahtar kelimeleri gösteren eklenen parçacık](media/source-editor-image12a.png)

Arasında `object` hareket etmek ve `MyProperty` sınıfınız için snippet'i özelleştirmek için **Sekme** tuşuna basın.

Bir anahtar kelime, bu `for` örnek gibi bir snippet `$i$` tekrarlanabilir, anahtar kelime 3 kez görünür fark:

![Yinelenen anahtar kelimelerle parçacık şablonu](media/source-editor-image12b.png)

Düzenleyicide kullanıldığında, **Sekme** tuşu ilk `i` ve `max`. Farklı bir değişken `i` adı ile aşırı yazarsanız, üç örnek de güncelleştirilir:

![Birden çok anahtar kelime gösteren eklenen parçacık](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>Ayrılmış anahtar sözcükler

Bir parçacıkta kullanabileceğiniz iki ayrılmış anahtar kelime vardır:

- `$selected$`&ndash; Snippet şablon **işaretli surround ise,** bu anahtar kelime snippet seçildiğinde editörvurgulanan metin ile değiştirilir.
- `$end$`&ndash; Kullanıcı anahtar kelimeleri bir snippet'te düzenlemeyi bitirdiğinde, imleç `$end$` anahtar kelimenin bulunduğu yere yerleştirilir.

Önceki `for` bölümdeki parçacık, bu ayrılmış anahtar kelimelerin bir örneğidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları (Windows'ta Visual Studio)](/visualstudio/ide/code-snippets)
