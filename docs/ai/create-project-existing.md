---
title: Mevcut koddan bir AI projesi oluşturma
description: mevcut Python kodunu bir Visual Studio projesine getirmek için aı Visual Studio Araçları nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-ai-tools
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 0f3ff4f40a42cfb7f4e3582abdb760af5dfffde9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045534"
---
# <a name="create-an-ai-project-from-existing-code"></a>Mevcut koddan bir AI projesi oluşturma

[aı için Visual Studio Araçları](installation.md)yükledikten sonra, var olan Python kodunu bir Visual Studio projesine getirmek kolaydır.

> [!Important]
> Burada açıklanan işlem özgün kaynak dosyalarını taşımaz veya kopyalamaz. Bir kopyalama ile çalışmak istiyorsanız önce klasörü çoğaltın.

1. Visual Studio başlatın ve **dosya > yeni > Project** seçin.

2. **yeni Project** iletişim kutusunda, "**aı araçları**" araması yapın, "**var olan Python kodundan**" şablonunu seçin, projeye bir ad ve konum verin ve **tamam**' ı seçin.

   ![mevcut koddan yeni Project, 1. adım](media/create-project-existing/new-ai-project.png)

3. Görüntülenen sihirbazda, mevcut kodunuzun yolunu ayarlayın, dosya türleri için bir filtre ayarlayın ve projenizin gerektirdiği arama yollarını belirtin ve ardından **Tamam**' ı seçin. Hangi arama yollarının olduğunu bilmiyorsanız, bu alanı boş bırakın.

   ![mevcut koddan yeni Project, adım 2](media/create-project-existing/azurebatch-newproject.png)

   mevcut kodunuz bir Azure Machine Learning projesinin parçasıysa, deneme hesabı, çalışma alanı, hangi bağlamların kullanılacağını ve daha fazlasını içeren önemli Azure Machine Learning yapılandırma ayrıntılarının başarılı bir şekilde dönüştürülmesini sağlamak için **, Azure Machine Learning klasörünü** kontrol edin.

4. Bir başlangıç dosyası ayarlamak için **Çözüm Gezgini** dosyasında dosyayı bulun, sağ tıklayın ve **başlangıç dosyası olarak ayarla**' yı seçin.

5. **CTRL** + **F5** 'e basarak veya hata ayıklama > hata **ayıklama olmadan Başlat**'ı seçerek programı çalıştırın.

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio 'de Python ile çalışma](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Mevcut bir Python ortamını el ile tanımla](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
