---
title: Direct2D ve JavaScript uygulamaları için Doku Verme
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d163aafa8b00ce1d59b1fc7b597ab5ca535a1ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72635506"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascript-apps"></a>Nasıl kullanılır: Direct2D veya JavaScript uygulamalarıyla kullanmak için bir doku dışa aktarma

Görüntü İçerik Ardışık Etki Alanı, Direct2D'nin dahili işleme kurallarıyla uyumlu dokular oluşturabilir. Bu tür dokular Direct2D kullanan uygulamalarda ve JavaScript kullanılarak oluşturulan UWP uygulamalarında kullanım için uygundur.

Bu belge şu etkinlikleri gösterir:

- Kaynak görüntünün Görüntü İçerik Ardışık Alanı tarafından işlenecek şekilde yapılandırılması.

- Görüntü İçerik Ardışık Bir Yapılandırma,Direct2D veya JavaScript uygulamasında kullanabileceğiniz bir doku oluşturacak şekilde yapılandırır.

  - Blok sıkıştırılmış *.dds* dosyası oluşturun.

  - Önceden çoğaltılmış alfa oluşturun.

  - Mipmap neslini devre dışı.

## <a name="rendering-conventions-in-direct2d"></a>Direct2D'de kuralları oluşturma

Direct2D bağlamında kullanılan dokular bu Direct2D dahili işleme kurallarına uygun olmalıdır:

- Direct2D, önceden çoğaltılmış alfayı kullanarak şeffaflık ve saydamlığı uygular. Direct2D ile kullanılan dokular, doku saydamlık veya saydamlık kullanmasa bile, önceden çoğaltılmış alfa içermelidir. Önceden çarpılmış alfa hakkında daha fazla bilgi için [bkz.](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)

- Doku, aşağıdaki blok sıkıştırma biçimlerinden biri kullanılarak *.dds* biçiminde sağlanmalıdır:

  - BC1_UNORM sıkıştırma

  - BC2_UNORM sıkıştırma

  - BC3_UNORM sıkıştırma

- Mipmaps desteklenmez.

### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Direct2D işleme kurallarıyla uyumlu bir doku oluşturmak için

1. Temel bir doku ile başlayın. Varolan bir görüntüyü yükleyin veya nasıl açıklanabilirsiniz: [Temel bir doku oluşturun.](../designers/how-to-create-a-basic-texture.md) *.dds* biçiminde blok sıkıştırmayı desteklemek için, 100x100, 128x128 veya 256x192 gibi dört boyutun katları olan genişlik ve yüksekliğe sahip bir doku belirtin. Mipmapping desteklenmedığından, doku kare olmak zorunda değildir ve iki boyutunda bir güç olması gerekmez.

2. Doku dosyasını Görüntü İçerik Ardışık Alanı tarafından işlenir şekilde yapılandırın. **Çözüm Gezgini'nde,** oluşturduğunuz doku dosyasının kısayol menüsünü açın ve ardından **Özellikler'i**seçin. Yapılandırma **Özellikleri** > **Genel** sayfasında, **Madde Türü** özelliğini Görüntü İçerik **Ardışık Alanı**olarak ayarlayın. **İçerik** özelliğinin **Evet** ve **İçten Dışla** olarak Ayarlandıktan emin **olun, Hayır**olarak ayarlandı ve ardından **Uygula** düğmesini seçin. **Resim İçeriği Yapı Denetimi** yapılandırma özelliği sayfası görüntülenir.

3. Çıktı biçimini blok sıkıştırılmış biçimlerden birine ayarlayın. Yapılandırma **Özellikleri** > **Resim İçerik Boru Hattı** > **Genel** sayfasında, sıkıştırma **(/sıkıştırma:BC3_UNORM) BC3_UNORM** **sıkıştır** özelliğini ayarlayın. Gereksinimlerinize bağlı olarak diğer BC1, BC2 veya BC3 biçimlerinden herhangi birini seçebilirsiniz. Direct2D şu anda BC4, BC5, BC6 veya BC7 dokularını desteklemiyor. Farklı BC biçimleri hakkında daha fazla bilgi için, [Blok sıkıştırma (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-block-compression)bakın.

   > [!NOTE]
   > Belirtilen sıkıştırma biçimi, Görüntü İçerik Ardışık Alanı tarafından üretilen dosyanın biçimini belirler. Bu, kaynak görüntü dosyasının diskte depolandığı biçimi belirleyen Görüntü Düzenleyicisi'ndeki kaynak görüntünün **Biçim** özelliğinden farklıdır. *working format* Genellikle, sıkıştırılmış bir çalışma biçimi istemezsiniz.

4. Önceden çoğaltılmış alfa kullanan çıktı üretmek için Görüntü İçerik Ardışık Alanı'nı yapılandırın. Yapılandırma **Özellikleri** > **Resim İçerik Boru Hattı** > **Genel** sayfasında, **Önceden çarpılmış alfa biçimi** özelliğini Evet **(/generatepremultipliedalpha)** olarak ayarlayın.

5. Mipmaps oluşturmaması için görüntü içeriği ardışık yapıyı yapılandırın. Configuration **Properties** > **Image Content Pipeline** > **Genel** sayfasında, **Mips oluştur** özelliğini **No**olarak ayarlayın.

6. **Tamam** düğmesini seçin.

   Projeyi oluşturduğunuzda, Görüntü İçerik Ardışık Alanı kaynak görüntüyü çalışma biçiminden belirttiğiniz çıktı biçimine dönüştürür—dönüştürme önceden çoğaltılmış alfa oluşturmayı içerir ve sonuç projenin çıktı dizinine kopyalanır.
