---
title: 'Nasıl yapılır: MIN haritaları Içeren bir dokuyu dışa aktarma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 55418f40f57e2279100fbb1c9ba4d12fae83a19c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664438"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Nasıl yapılır: Mipmap'leri İçeren Dokuyu Dışa Aktarma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görüntü Içeriği ardışık düzeni, projenizin derleme aşamasının bir parçası olarak bir kaynak görüntüden MIN ile haritalar oluşturabilir. Her MıP düzeyinin görüntü içeriğini el ile belirtmeniz gerekmiyorsa — derleme zamanında MIMS haritaları oluşturmak mipmap içeriğinin hiçbir zaman eşitleme olmamasını sağlar ve çalışma zamanında MIMS haritaları oluşturma performans maliyetini ortadan kaldırır.

 Bu belge Şu etkinlikleri gösterir:

- Görüntü Içeriği ardışık düzeni tarafından işlenecek kaynak görüntüyü yapılandırma.

- Görüntü Içeriği ardışık düzenini, MIN haritaları oluşturmak için yapılandırma.

## <a name="exporting-mipmaps"></a>MIN haritaları dışarı aktarılıyor
 IBU eşleme, 3B oyun veya uygulamadaki dokulu yüzeyler için otomatik ekran alanı ayrıntı düzeyi sağlar. Bir dokunun, tüm dokuların örneklendiği her seferinde aşağı örneklenebilir olması için, bir dokusunun örneklendiği sürümlerini önceden hesaplayarak, bir oyunun veya uygulamanın işleme performansını geliştirir.

#### <a name="to-export-a-texture-that-has-mipmaps"></a>MIN haritaları olan bir dokuyu dışarı aktarmak için

1. Temel bir dokuyla başlayın. Varolan bir resim dosyasını yükleyin veya [nasıl yapılır: temel doku oluşturma](../designers/how-to-create-a-basic-texture.md)bölümünde açıklandığı gibi bir tane oluşturun. Mı haritalarını desteklemek için, her iki boyutu da aynı olan, örneğin 64x64, 256x256 veya 512x512 gibi bir genişlik ve yüksekliğe sahip bir doku belirtin.

2. Yeni oluşturduğunuz doku dosyasını, görüntü Içeriği ardışık düzeni tarafından işlenecek şekilde yapılandırın. **Çözüm Gezgini**' de, az önce oluşturduğunuz doku dosyasının kısayol menüsünü açın ve ardından **Özellikler**' i seçin. **Yapılandırma özellikleri**, **genel** sayfasında, **öğe türü** özelliğini **görüntü içeriği ardışık düzeni**olarak ayarlayın. **İçerik** özelliğinin **Evet** olarak ayarlandığından ve **derlemeden hariç tut** ' un **Hayır**olarak ayarlandığından emin olun ve ardından **Uygula** düğmesini seçin. **Görüntü Içeriği ardışık düzen** yapılandırma özelliği sayfası görüntülenir.

3. Görüntü Içeriği ardışık düzenini, MIN haritaları oluşturacak şekilde yapılandırın. **Yapılandırma özellikleri**, **görüntü içeriği ardışık düzeni**, **genel** sayfasında, **MIPS oluştur** özelliğini **Evet (/generatemıps)** olarak ayarlayın.

4. **Tamam** düğmesini seçin.

   Projeyi oluşturduğunuzda, görüntü Içeriği ardışık düzeni kaynak görüntüyü çalışma biçiminden, MıP düzeyleri dahil olmak üzere belirttiğiniz çıkış biçimine dönüştürür ve sonuç projenin çıkış dizinine kopyalanır.
