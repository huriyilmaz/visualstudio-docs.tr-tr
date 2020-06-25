---
title: Depoyu kopyalama
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 9bb3aa4a7aa9818f42f99860956e0e2ae73b2b7f
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371592"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Visual Studio 'da Python kodu deposunu kopyalama

[Visual Studio Tools for AI](installation.md)yükledikten sonra Python kodu deposunu kolayca kopyalayabilir ve bundan bir proje oluşturabilirsiniz.

1. GitHub depolarına bağlanmak için, Visual Studio yükleyicisi 'ni çalıştırın, **Değiştir**' i seçin ve **ayrı bileşenler** sekmesini seçin. **kod araçları** bölümünde aşağı kaydırın, **Visual Studio Için GitHub Uzantısı**' nı seçin ve **Değiştir**' i seçin.

    ![Visual Studio yükleyicisi 'nde GitHub uzantısını seçme](media/create-project-repo/installation-github-extension.png)

2. Visual Studio’yu başlatın.

3. GitHub veya Azure DevOps 'a bağlanabildiğinizi veya bir depoyu klonlayabileceğiniz **Takım Gezgini** penceresini açmak için **> Takım Gezgini görüntüle** ' yi seçin.

    ![Azure DevOps, GitHub ve bir depoyu klonlama gösteren Takım Gezgini penceresi](media/create-project-repo/team-explorer-devops.png)

4. **Yerel Git depoları**altındaki URL alanında, `https://github.com/Microsoft/samples-for-ai` öğesini girin, kopyalanmış dosyalar için bir klasör girin ve **Kopyala**' yı seçin.

    > [!Tip]
    > Takım Gezgini içinde belirttiğiniz klasör klonlanan dosyaları almak için özel klasördür. Komutun aksine `git clone` , Takım Gezgini bir kopyanın oluşturulması, otomatik olarak deponun adı ile bir alt klasör oluşturmaz.

5. Kopyalama tamamlandığında, depo panosuna gitmek için Takım Gezgini alt kısmındaki depo klasörüne çift tıklayın. **Çözümler**altında **Yeni**' yi seçin.

    ![Takım Gezgini penceresi, bir kopyadan yeni bir proje oluşturma](media/create-project-repo/team-explorer-new-project.png)

6. Görüntülenen **Yeni proje** iletişim kutusunda "**var olan Python kodundan**" seçeneğini belirleyin, proje için bir ad belirleyin, **konumu** depoyla aynı klasöre ayarlayın ve **Tamam**' ı seçin. Görüntülenen sihirbazda **son**' u seçin.

7. Menüden **Çözüm Gezgini > görüntüle** ' yi seçin.

8. Çözüm Gezgini, `TensorFlow Examples> MNIST` düğümünü genişletin, sağ tıklayın `convolutional.py` ve **başlangıç dosyası olarak ayarla**' yı seçin. Bu adım, Visual Studio 'Nun projeyi çalıştırırken hangi dosyayı kullanması gerektiğini söyler.

9. **Ctrl** + Programı çalıştırmak için CTRL**F5** tuşuna basın veya hata ayıklama **> Başlat** ' ı seçin. Bir hata görürseniz, önceki adımda çalışma dizini ayarını yeniden denetleyin.

10. Program başarıyla çalıştırıldığında, eğitim ve test veri kümenizi indirmeye başlar, sonra modeli eğitme ve hata hızınızı çıktı olarak görürsünüz. Hata oranını zaman içinde azaltmayı istiyorsunuz

    ![Python MNIST programından ilk çıkış](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Anaconda kullanıyorsanız ve eksik sayısal tuş takımı hakkında bir hata alırsanız, [Python ortamınızı Anaconda kullanacak şekilde değiştirmeniz](../python/selecting-a-python-environment-for-a-project.md)gerekebilir.

11. İlerlemeyi TensorBoard ile görselleştirebilirsiniz. Projenize sağ tıklayın ve ardından **Tensorboard Çalıştır** ' a tıklayın ve ardından çıkış tablosu günlüklerinizin dizinini seçin.

   ![tensorboard Çalıştır](media/create-project-repo/run-tensorboard.png)

12. Fazla mesaiyi azalttığını ve bu da kaliteyi geliştirdiğine dikkat edin.

   ![tensorboard Çalıştır](media/create-project-repo/tensorboard.png)
