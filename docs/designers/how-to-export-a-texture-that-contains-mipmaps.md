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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589415"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Nasıl yapılı: Mipmaps içeren bir doku dışa aktarma

Görüntü İçerik Ardışık Bir dizi, projenizin oluşturma aşamasının bir parçası olarak kaynak görüntüden mipmaps oluşturabilir. Belirli efektleri elde etmek için bazen her MIP düzeyinin görüntü içeriğini el ile belirtmeniz gerekir. Her MIP düzeyinin görüntü içeriğini el ile belirtmeniz gerekmediğinde, oluşturma zamanında mipmaps oluşturmak mipmap içeriğinin hiçbir zaman eşitlenmemiş olmasını sağlar. Ayrıca, çalışma zamanında mipmaps oluşturma performans maliyetini ortadan kaldırır.

Bu makale şunları kapsamaktadır:

- Kaynak görüntünün Görüntü İçerik Ardışık Alanı tarafından işlenecek şekilde yapılandırılması.

- Görüntü İçerik Ardışık Alanı'nı mipmaps oluşturacak şekilde yapılandırma.

## <a name="export-mipmaps"></a>Mipmaps dışa aktarma

Mipmapping, bir 3D oyun veya uygulamada dokulu yüzeyler için otomatik ekran alanı Ayrıntı Düzeyi sağlar. Bir dokunun aşağıda örneklenmiş sürümlerini önceden hesaplayarak bir oyunun veya uygulamanın oluşturma performansını artırır. Önceden bilgi işlem aşağı örneklenmiş sürümler, her örneklenin tüm dokusunun aşağı örneklenmiş olması gerekmediği anlamına gelir.

### <a name="to-export-a-texture-that-has-mipmaps"></a>Mipmaps olan bir doku dışa aktarmak için

1. Temel bir doku ile başlayın. Varolan bir resim dosyasını yükleyin veya nasıl açıklansın: [Temel bir doku oluşturun.](../designers/how-to-create-a-basic-texture.md) Mipmaps'i desteklemek için, 64x64, 256x256 veya 512x512 gibi iki boyutun aynı gücüyle genişlik ve yüksekliğe sahip bir doku belirtin.

2. Oluşturduğunuz doku dosyasını, Görüntü İçerik Ardışık Alanı tarafından işlenir şekilde yapılandırın. **Çözüm Gezgini'nde,** oluşturduğunuz doku dosyasının kısayol menüsünü açın ve ardından **Özellikler'i**seçin. Yapılandırma **Özellikleri** > **Genel** sayfasında, **Madde Türü** özelliğini Görüntü İçerik **Ardışık Alanı**olarak ayarlayın. **İçerik** özelliğinin **Evet** ve **Yapıdan Dışla** olarak ayarlandıklarından emin **olun.** **Uygula**’yı seçin.

   **Resim İçeriği Yapı Denetimi** yapılandırma özelliği sayfası görüntülenir.

3. Mipmaps oluşturmak için Görüntü İçerik Ardışık Yapıl.' Yapılandırma **Özellikleri** > **Resim İçerik Boru Hattı** > **Genel** sayfasında, **Mips oluştur** özelliğini Evet **(/generatemips)** olarak ayarlayın.

4. **Tamam'ı**seçin.

Projeyi oluşturduğunuzda, Görüntü İçerik Ardışık Alanı kaynak görüntüyü çalışma biçiminden MIP düzeyleri de dahil olmak üzere belirttiğiniz çıktı biçimine dönüştürür. Sonuç, projenin çıktı dizinine kopyalanır.
