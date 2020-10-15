---
title: Mevcut koddan bir AI projesi oluşturma
description: Mevcut Python kodunu bir Visual Studio projesine getirmek için Visual Studio Tools for AI nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: ef62b0a5f3fac00aba0648008a47d35e0adc89f4
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099264"
---
# <a name="create-an-ai-project-from-existing-code"></a>Mevcut koddan bir AI projesi oluşturma

[Visual Studio Tools for AI](installation.md)yükledikten sonra, var olan Python kodunu bir Visual Studio projesine getirmek kolaydır.

> [!Important]
> Burada açıklanan işlem özgün kaynak dosyalarını taşımaz veya kopyalamaz. Bir kopyalama ile çalışmak istiyorsanız önce klasörü çoğaltın.

1. Visual Studio 'Yu başlatın ve **dosya > yeni > proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda, "**AI araçları**" araması yapın, "**var olan Python kodundan**" şablonu seçin, projeye bir ad ve konum verin ve **Tamam**' ı seçin.

   ![Mevcut koddan yeni proje, 1. adım](media/create-project-existing/new-ai-project.png)

3. Görüntülenen sihirbazda, mevcut kodunuzun yolunu ayarlayın, dosya türleri için bir filtre ayarlayın ve projenizin gerektirdiği arama yollarını belirtin ve ardından **Tamam**' ı seçin. Hangi arama yollarının olduğunu bilmiyorsanız, bu alanı boş bırakın.

   ![Mevcut koddan yeni proje, adım 2](media/create-project-existing/azurebatch-newproject.png)

   Mevcut kodunuz bir Azure Machine Learning projesinin parçasıysa, deneme hesabı, çalışma alanı, hangi bağlamların kullanılacağını ve daha fazlasını içeren önemli Azure Machine Learning yapılandırma ayrıntılarının başarılı bir şekilde dönüştürülmesini sağlamak için **, Azure Machine Learning klasörünü** kontrol edin.

4. Bir başlangıç dosyası ayarlamak için **Çözüm Gezgini**dosyasında dosyayı bulun, sağ tıklayın ve **başlangıç dosyası olarak ayarla**' yı seçin.

5. **CTRL** + **F5** 'e basarak veya hata ayıklama > hata **ayıklama olmadan Başlat**'ı seçerek programı çalıştırın.

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio 'da Python ile çalışma](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Mevcut bir Python ortamını el ile tanımla](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
