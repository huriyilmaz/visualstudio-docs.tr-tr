---
title: Depoyu kopyalama
description: bir Python kodu deposunu klonlamak ve bundan bir proje oluşturmak için aı Visual Studio Araçları nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 91678f7d0e6843c569e069b30f1c8e5017b254d9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122053494"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Visual Studio Python kodu deposunu kopyalama

[aı için Visual Studio Araçları](installation.md)yükledikten sonra Python kodu deposunu kolayca kopyalayabilir ve bundan bir proje oluşturabilirsiniz.

1. GitHub depolarına bağlanmak için Visual Studio yükleyiciyi çalıştırın, **değiştir**' i seçin ve **ayrı bileşenler** sekmesini seçin. **kod araçları** bölümüne gidin, **Visual Studio için GitHub uzantısı**' nı seçin ve **değiştir**' i seçin.

    ![Visual Studio yükleyicisinde GitHub uzantısı seçiliyor](media/create-project-repo/installation-github-extension.png)

2. Visual Studio başlatın.

3. GitHub veya Azure DevOps 'e bağlanabildiğinizi veya bir depoyu klonlayabileceğiniz **Takım Gezgini** penceresini açmak için **> görüntüle Takım Gezgini** ' yi seçin.

    ![bir depoyu Azure DevOps, GitHub ve kopyalamayı gösteren takım gezgini penceresi](media/create-project-repo/team-explorer-devops.png)

4. **Yerel Git depoları** altındaki URL alanında, `https://github.com/Microsoft/samples-for-ai` öğesini girin, kopyalanmış dosyalar için bir klasör girin ve **Kopyala**' yı seçin.

    > [!Tip]
    > Takım Gezgini içinde belirttiğiniz klasör klonlanan dosyaları almak için özel klasördür. Komutun aksine `git clone` , Takım Gezgini bir kopyanın oluşturulması, otomatik olarak deponun adı ile bir alt klasör oluşturmaz.

5. Kopyalama tamamlandığında, depo panosuna gitmek için Takım Gezgini alt kısmındaki depo klasörüne çift tıklayın. **Çözümler** altında **Yeni**' yi seçin.

    ![Takım Gezgini penceresi, bir kopyadan yeni bir proje oluşturma](media/create-project-repo/team-explorer-new-project.png)

6. görüntülenen **yeni Project** iletişim kutusunda "**var olan Python kodundan**" seçeneğini belirleyin, proje için bir ad belirleyin, **konumu** depoyla aynı klasöre ayarlayın ve **tamam**' ı seçin. Görüntülenen sihirbazda **son**' u seçin.

7. Menüden **Çözüm Gezgini > görüntüle** ' yi seçin.

8. Çözüm Gezgini, `TensorFlow Examples> MNIST` düğümünü genişletin, sağ tıklayın `convolutional.py` ve **başlangıç dosyası olarak ayarla**' yı seçin. bu adım, projeyi çalıştırırken hangi dosyayı kullanması gerektiğini Visual Studio söyler.

9.  + Programı çalıştırmak için CTRL **F5** tuşuna basın veya hata ayıklama **> Başlat** ' ı seçin. Bir hata görürseniz, önceki adımda çalışma dizini ayarını yeniden denetleyin.

10. Program başarıyla çalıştırıldığında, eğitim ve test veri kümenizi indirmeye başlar, sonra modeli eğitme ve hata hızınızı çıktı olarak görürsünüz. Hata oranını zaman içinde azaltmayı istiyorsunuz

    ![Python MNIST programından ilk çıkış](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Anaconda kullanıyorsanız ve eksik sayısal tuş takımı hakkında bir hata alırsanız, [Python ortamınızı Anaconda kullanacak şekilde değiştirmeniz](../python/selecting-a-python-environment-for-a-project.md)gerekebilir.

11. İlerlemeyi TensorBoard ile görselleştirebilirsiniz. Projenize sağ tıklayın ve ardından **Tensorboard Çalıştır** ' a tıklayın ve ardından çıkış tablosu günlüklerinizin dizinini seçin.

   ![bağlam menüsünde seçili olan mnist projesi ve tensorboard çalıştır seçeneği ile Visual Studio Çözüm Gezgini ekran görüntüsü.](media/create-project-repo/run-tensorboard.png)

12. Fazla mesaiyi azalttığını ve bu da kaliteyi geliştirdiğine dikkat edin.

   ![TensorBoard günlüklerinden verileri görselleştiren dört grafik gösteren ana TensorBoard penceresinin ekran görüntüsü.](media/create-project-repo/tensorboard.png)
