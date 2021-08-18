---
title: "Nasıl yapılır: Mipmap'leri İçeren Dokuyu Dışa Aktarma"
description: Görüntü İçeriği İşlem Hattı'nın projenizi oluşturmanın bir parçası olarak bir kaynak görüntüden mipmap'ler oluşturmasını öğrenin. Bu sayede mipmap'ler hiçbir zaman eşitnin dışından kullanılamaz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: a0dc90b70c20e93a2f454f2ddcd5aa2840593927
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104709"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Nasıl edilir: Mipmap'ler içeren dokuyu dışarı aktarma

Görüntü İçeriği İşlem Hattı, projenizin derleme aşamasının bir parçası olarak bir kaynak görüntüden mipmap'ler oluşturabilirsiniz. Belirli etkileri elde etmek için bazen her MIP düzeyinin görüntü içeriğini el ile belirtmeniz gerekir. Her MIP düzeyinin görüntü içeriğini el ile belirtmenize gerek olmadığınız zaman, derleme zamanında mipmap'ler oluşturmak, mipmap içeriklerinin hiçbir zaman eşit olmayan hale geldiğinden sağlar. Ayrıca çalışma zamanında mipmap oluşturmanın performans maliyetini de ortadan kaldırıyor.

Bu makale şunları kapsar:

- Görüntü İçeriği İşlem Hattı tarafından işlenecek kaynak görüntüyü yapılandırma.

- Mipmap'ler oluşturmak için Görüntü İçeriği İşlem Hattını yapılandırma.

## <a name="export-mipmaps"></a>Mipmap'leri dışarı aktarma

Mipmapping, 3B bir oyun veya uygulamada doyma desenli yüzeyler için otomatik ekran alanı Ayrıntı Düzeyi sağlar. Dokudan alınan örnekli sürümleri önceden hesap kullanarak bir oyunun veya uygulamanın işleme performansını artırır. Önceden hesaplanan örnekli sürümler, doku örneğinin her örneklemede aşağı örnekleme yapmak zorunda olmadığını ifade eder.

### <a name="to-export-a-texture-that-has-mipmaps"></a>Mipmap'leri olan dokuyu dışarı aktarma

1. Temel dokuyla başlama. Var olan bir görüntü dosyasını yükleme veya Oluşturma: Temel doku oluşturma [konusunda açıklandığı gibi bir tane oluşturun.](../designers/how-to-create-a-basic-texture.md) Mipmap'leri desteklemek için genişliği ve yüksekliği aynı boyuttaki iki güçlü doku belirtin; örneğin, 64x64, 256x256 veya 512x512.

2. Yeni oluşturduğunuz doku dosyasını Görüntü İçeriği İşlem Hattı tarafından işlenecek şekilde yapılandırma. Bu **Çözüm Gezgini,** oluşturduğunuz doku dosyasının kısayol menüsünü açın ve özellikler'i **seçin.** Yapılandırma Özellikleri **Genel**  >  **sayfasında** Öğe Türü özelliğini **Görüntü İçeriği İşlem** Hattı **olarak ayarlayın.** content özelliğinin **Evet ve**  Derlemeden Dışla özelliğinin **Hayır olarak** ayarlanmış olduğundan emin **olun.** **Uygula**’yı seçin.

   Görüntü **İçeriği İşlem Hattı** yapılandırma özelliği sayfası görüntülenir.

3. Mipmap'ler oluşturmak için Görüntü İçeriği İşlem Hattını yapılandırma. Yapılandırma Özellikleri **Görüntü İçeriği**  >  **İşlem Hattı**  >  **Genel** sayfasında, **Mips Oluştur** özelliğini Evet **(/generatemips) olarak ayarlayın.**

4. **Tamam**’ı seçin.

Projeyi derlemek için Görüntü İçeriği İşlem Hattı, kaynak görüntüyü çalışma biçiminden MIP düzeyleri de dahil olmak üzere belirttiğiniz çıkış biçimine dönüştürür. Sonuç, projenin çıkış dizinine kopyalanır.
