---
title: Direct2D ve JavaScript uygulamaları için bir dokuyu dışarı aktarma
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 546f7255b1c2846bdbd05bba0593b30bad9beacd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85768999"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascript-apps"></a>Nasıl yapılır: Direct2D veya JavaScript uygulamaları ile kullanmak için doku dışarı aktarma

Görüntü Içeriği ardışık düzeni, Direct2D's iç işleme kurallarıyla uyumlu dokular oluşturabilir. Bu tür dokular, Direct2D kullanan uygulamalarda ve JavaScript kullanılarak oluşturulan UWP uygulamalarında kullanım için uygundur.

Bu belge Şu etkinlikleri gösterir:

- Görüntü Içeriği ardışık düzeni tarafından işlenecek kaynak görüntüyü yapılandırma.

- Direct2D veya JavaScript uygulamasında kullanabileceğiniz bir doku oluşturmak için görüntü Içeriği ardışık düzenini yapılandırma.

  - Blok ile sıkıştırılmış bir *. DDS* dosyası oluşturun.

  - Ön çarpılmış Alfa Oluştur.

  - Mipmap oluşturmayı devre dışı bırakın.

## <a name="rendering-conventions-in-direct2d"></a>Direct2D 'de işleme kuralları

Direct2D bağlamında kullanılan dokuların bu Direct2D iç işleme kurallarına uyması gerekir:

- Direct2D, ön çarpılmış alfa kullanarak saydamlığı ve ayrımı uygular. Doku saydamlığı veya ayrımı kullanmıyor olsa bile, Direct2D ile kullanılan dokuların ön çarpılmış Alfa içermesi gerekir. Ön çarpılmış Alfa hakkında daha fazla bilgi için bkz. [nasıl yapılır: ön çarpılmış Alfa içeren dokuyu dışarı aktarma](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).

- Dokunun, bu blok sıkıştırma biçimlerinden biri kullanılarak *. DDS* biçiminde sağlanması gerekir:

  - BC1_UNORM sıkıştırma

  - BC2_UNORM sıkıştırma

  - BC3_UNORM sıkıştırma

- MIN haritaları desteklenmez.

### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Direct2D işleme kurallarıyla uyumlu bir doku oluşturmak için

1. Temel bir dokuyla başlayın. Mevcut bir görüntüyü yükleyin veya [nasıl yapılır: temel doku oluşturma](../designers/how-to-create-a-basic-texture.md)bölümünde açıklandığı gibi yeni bir tane oluşturun. *. DDS* biçimindeki blok sıkıştırmasını desteklemek için, boyutun boyutunun dört katı olan genişlik ve yüksekliğe sahip bir doku belirtin, örneğin, 100x100, 128x128 veya 256x192. II eşlemesi desteklenmediğinden, dokunun kare olması gerekmez ve iki boyutta bir üssü olmalıdır.

2. Doku dosyasını görüntü Içeriği ardışık düzeni tarafından işlenecek şekilde yapılandırın. **Çözüm Gezgini**' de, az önce oluşturduğunuz doku dosyasının kısayol menüsünü açın ve ardından **Özellikler**' i seçin. **Yapılandırma özellikleri**  >  **genel** sayfasında, **öğe türü** özelliğini **görüntü içeriği ardışık düzeni**olarak ayarlayın. **İçerik** özelliğinin **Evet** olarak ayarlandığından ve **derlemeden hariç tut** ' un **Hayır**olarak ayarlandığından emin olun ve ardından **Uygula** düğmesini seçin. **Görüntü Içeriği ardışık düzen** yapılandırma özelliği sayfası görüntülenir.

3. Çıkış biçimini, blok ile sıkıştırılmış biçimlerden birine ayarlayın. **Yapılandırma özellikleri**  >  **görüntüsü içerik ardışık düzeni**  >  **genel** sayfasında, **Sıkıştır** özelliğini **BC3_UNORM Compression (/Compress: BC3_UNORM)** olarak ayarlayın. Gereksinimlerinize bağlı olarak diğer BC1, BC2 veya BC3 biçimlerinden birini seçebilirsiniz. Direct2D Şu anda BC4, BC5, BC6 veya BC7 dokularını desteklemez. Farklı BC biçimleri hakkında daha fazla bilgi için bkz. [blok sıkıştırma (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-block-compression).

   > [!NOTE]
   > Belirtilen sıkıştırma biçimi, görüntü Içeriği ardışık düzeni tarafından üretilen dosyanın biçimini belirler. Bu, görüntü düzenleyicisinde kaynak görüntünün **Biçim** özelliğinden farklıdır. Bu, disk üzerinde depolanan kaynak görüntü dosyasının biçimini ( *çalışma biçimi*) belirler. Genellikle, sıkıştırılmış bir çalışma biçimi istemezsiniz.

4. Görüntü Içeriği ardışık düzenini, ön çarpılmış alfa kullanan çıkış oluşturacak şekilde yapılandırın. **Yapılandırma özellikleri**  >  **görüntüsü içerik ardışık düzeni**  >  **genel** sayfasında, **önceden çarpılan Alfa biçimi** özelliğini **Evet (/generatepremultipliedalpha)** olarak ayarlayın.

5. Görüntü içeriği ardışık düzenini, MIN için MIT haritaları oluşturmamasını sağlayacak şekilde yapılandırın. **Yapılandırma özellikleri**  >  **görüntüsü içerik ardışık düzeni**  >  **genel** sayfasında, **MIPS özelliğini oluştur** ' u **Hayır**olarak ayarlayın.

6. **Tamam** düğmesini seçin.

   Projeyi oluşturduğunuzda, görüntü Içeriği ardışık düzeni kaynak görüntüyü çalışma biçiminden belirlediğiniz çıkış biçimine dönüştürür — dönüştürme, ön çarpılmış Alfa oluşturmayı içerir — ve sonuç projenin çıkış dizinine kopyalanır.
