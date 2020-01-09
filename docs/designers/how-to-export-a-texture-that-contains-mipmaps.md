---
title: "Nasıl yapılır: Mipmap'leri İçeren Dokuyu Dışa Aktarma"
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71d570e6dc7544911ebe2bb279aafb3a07620cbc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589415"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Nasıl yapılır: MIN haritaları içeren bir dokuyu dışarı aktarma

Görüntü Içeriği ardışık düzeni, projenizin derleme aşamasının bir parçası olarak bir kaynak görüntüden MIN ile haritalar oluşturabilir. Bazı etkilere ulaşmak için bazen her MıP düzeyinin görüntü içeriğini el ile belirtmeniz gerekir. Her MıP düzeyinin görüntü içeriğini el ile belirtmeniz gerekmiyorsa, derleme zamanında mı haritaları oluşturmak mipmap içeriklerinin hiçbir zaman eşitleme dışı olmamasını sağlar. Ayrıca, çalışma zamanında MINFO haritaları oluşturmanın performans maliyetini ortadan kaldırır.

Bu makalede ele alınmıştır:

- Görüntü Içeriği ardışık düzeni tarafından işlenecek kaynak görüntüyü yapılandırma.

- Görüntü Içeriği ardışık düzenini, MIN haritaları oluşturmak için yapılandırma.

## <a name="export-mipmaps"></a>MIN haritaları dışarı aktar

IBU eşleme, 3B oyun veya uygulamadaki dokulu yüzeyler için otomatik ekran alanı ayrıntı düzeyi sağlar. Bir dokunun örnek oluşturma sürümlerini önceden hesaplayarak bir oyunun veya uygulamanın işleme performansını geliştirir. Önceden bilgi işlem, örneklenir-örnek sürümler, tüm dokunun örneklendiği her seferinde alt örneklendiği anlamına gelir.

### <a name="to-export-a-texture-that-has-mipmaps"></a>MIN haritaları olan bir dokuyu dışarı aktarmak için

1. Temel bir dokuyla başlayın. Varolan bir resim dosyasını yükleyin veya [nasıl yapılır: temel doku oluşturma](../designers/how-to-create-a-basic-texture.md)bölümünde açıklandığı gibi bir tane oluşturun. Mı haritalarını desteklemek için, her iki boyutu da aynı olan, örneğin 64x64, 256x256 veya 512x512 gibi bir genişlik ve yüksekliğe sahip bir doku belirtin.

2. Yeni oluşturduğunuz doku dosyasını, görüntü Içeriği ardışık düzeni tarafından işlenecek şekilde yapılandırın. **Çözüm Gezgini**, oluşturduğunuz doku dosyasının kısayol menüsünü açın ve ardından **Özellikler**' i seçin. **Yapılandırma özellikleri** > **genel** sayfasında, **öğe türü** özelliğini **görüntü içeriği ardışık düzeni**olarak ayarlayın. **İçerik** özelliğinin **Evet** **olarak ayarlandığından**ve **derlemeden hariç tutduğunuzdan** emin olun. **Uygula**’yı seçin.

   **Görüntü Içeriği ardışık düzen** yapılandırma özelliği sayfası görüntülenir.

3. Görüntü Içeriği ardışık düzenini, MIN haritaları oluşturacak şekilde yapılandırın. **Yapılandırma özellikleri** > **görüntü Içeriği ardışık > düzeni** **genel** sayfasında, **MIPS özelliği oluştur** ' u **Evet (/generatemıps)** olarak ayarlayın.

4. Seçin **Tamam**.

Projeyi oluşturduğunuzda, görüntü Içeriği ardışık düzeni, kaynak görüntüsünü MıP düzeyleri dahil olmak üzere, çalışma biçiminden belirlediğiniz çıkış biçimine dönüştürür. Sonuç projenin çıkış dizinine kopyalanır.
