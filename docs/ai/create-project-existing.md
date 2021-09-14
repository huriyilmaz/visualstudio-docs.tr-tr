---
title: Mevcut koddan bir AI projesi oluşturma
description: Mevcut Python kodunu bir Visual Studio Araçları projesine getirmek için AI için Visual Studio öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633393"
---
# <a name="create-an-ai-project-from-existing-code"></a>Mevcut koddan bir AI projesi oluşturma

AI için [Visual Studio Araçları yüklediniz](installation.md)mi, mevcut Python kodunu bir Visual Studio projesine getirebilirsiniz.

> [!Important]
> Burada açıklanan işlem özgün kaynak dosyaları taşımaz veya kopyalamaz. Bir kopyayla çalışmak için önce klasörü çoğaltabilirsiniz.

1. Yeni Visual Studio'ı açın **ve Yeni > Dosya'> Project.**

2. Yeni **uygulama Project** iletişim kutusunda "**AI Tools**" araması yazın, " Mevcut **Python** kodundan " şablonunu seçin, projeye bir ad ve konum girin ve Tamam'ı **seçin.**

   ![Mevcut Project yeni kaynak, 1. adım](media/create-project-existing/new-ai-project.png)

3. Görüntülenen sihirbazda, mevcut kodunuzun yolunu ayarlayın, dosya türleri için bir filtre ayarlayın ve projenizin gerektirdiği arama yollarını belirtin ve tamam'ı **seçin.** Arama yollarının ne olduğunu bilmiyorsanız bu alanı boş bırakın.

   ![Mevcut Project yeni kaynak, 2. adım](media/create-project-existing/azurebatch-newproject.png)

   Mevcut kodunuz bir Azure Machine Learning projesinin parçası ise, Deneme hesabı, Çalışma Alanı, hangi işlem bağlamlarının ve daha fazlası gibi önemli Azure Machine Learning yapılandırma ayrıntılarının başarılı bir şekilde dönüştürmesini sağlamak için **Is Azure Machine Learning** klasörünü kontrol edin.

4. Bir başlangıç dosyası ayarlamak için dosyanın başlangıç **Çözüm Gezgini** sağ tıklayın ve Başlangıç Dosyası Olarak **Ayarla'yı seçin.**

5. **Ctrl** F5 tuşlarına basarak veya Hata Ayıkla'> +  **Hata Ayıklamadan Başlat'ı seçerek programı çalıştırın.**

> [!div class="nextstepaction"]
> [Öğretici: Python ile Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Mevcut Bir Python ortamını el ile tanımlama](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
