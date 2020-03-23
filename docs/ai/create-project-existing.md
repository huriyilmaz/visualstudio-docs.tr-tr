---
title: Varolan koddan bir AI projesi oluşturma
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 0981a276a21e1b3f816c6a182df29f1c4adb0d1c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72777450"
---
# <a name="create-an-ai-project-from-existing-code"></a>Varolan koddan bir AI projesi oluşturma

[AI için Visual Studio Tools'u yükledikten](installation.md)sonra, mevcut Python kodunu Visual Studio projesine katmak kolaydır.

> [!Important]
> Burada açıklanan işlem özgün kaynak dosyalarını hareket ettirmez veya kopyalamaz. Bir kopyayla çalışmak istiyorsanız, önce klasörü çoğaltın.

1. Visual Studio'u başlatın ve **Dosya > Yeni > Projesi'ni**seçin.

2. Yeni **Proje** iletişim kutusunda , "**AI Tools**" araması yapın, "**Varolan Python kodundan**" şablonunu seçin, projeye bir ad ve konum verin ve **Tamam'ı**seçin.

   ![Mevcut Koddan Yeni Proje, adım 1](media/create-project-existing/new-ai-project.png)

3. Görünen sihirbazda, varolan kodunuza giden yolu ayarlayın, dosya türleri için bir filtre ayarlayın ve projenizin gerektirdiği arama yollarını belirtin, ardından **Tamam'ı**seçin. Arama yollarının ne olduğunu bilmiyorsanız, alanı boş bırakın.

   ![Mevcut Koddan Yeni Proje, adım 2](media/create-project-existing/azurebatch-newproject.png)

   Varolan kodunuz bir Azure Machine Learning projesinin parçasıysa, Deneme Hesabı, kullanılacak içerikleri hesaplayan Workspace ve daha fazlası gibi önemli Azure Machine Learning yapılandırma ayrıntılarının başarılı bir şekilde dönüştürülmesini sağlamak için **Azure Machine Learning klasörünü** kontrol edin.

4. Başlangıç dosyasını ayarlamak **için, Dosyayı Solution Explorer'da**bulun , sağ tıklatın ve **Başlangıç Dosyası olarak ayarla'yı**seçin.

5. **Ctrl**+**F5** tuşuna basarak veya Hata Ayıklama olmadan Başlat > Hata Ayıklama'yı seçerek programı **çalıştırın.**

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio Python ile çalışma](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Varolan bir Python ortamını el ile tanımlama](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
