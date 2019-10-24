---
title: Mevcut koddan bir AI projesi oluşturma
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 0981a276a21e1b3f816c6a182df29f1c4adb0d1c
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777450"
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

   Mevcut kodunuz bir Azure Machine Learning projesinin parçasıysa, deneme hesabı, çalışma alanı gibi önemli Azure Machine Learning yapılandırma ayrıntılarının başarılı bir şekilde dönüştürülmesini sağlamak için **Azure Machine Learning klasörünü** kontrol edin. kullanım için işlem bağlamları ve daha fazlası.

4. Bir başlangıç dosyası ayarlamak için **Çözüm Gezgini**dosyasında dosyayı bulun, sağ tıklayın ve **başlangıç dosyası olarak ayarla**' yı seçin.

5. Programı, **Ctrl** +**F5** tuşuna basarak veya hata ayıklama **> hata ayıklama olmadan Başlat**' a seçerek çalıştırın.

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio 'da Python ile çalışma](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Mevcut bir Python ortamını el ile tanımla](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
