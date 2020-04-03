---
title: Bir repo klonlama
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: d146d801a1519d3282b4e2c5dd72fd23b0df7206
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638639"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Visual Studio'da Python kodunun deposunu klonlama

[AI için Visual Studio Tools'u yükledikten](installation.md)sonra Python kodunun deposunu kolayca klonlayabilir ve ondan bir proje oluşturabilirsiniz.

1. GitHub depolarına bağlanmak için Visual Studio yükleyicisini çalıştırın, **Değiştir'i**seçin ve **Tek tek bileşenler** sekmesini seçin. Kod **araçları** bölümüne aşağı kaydırın, Visual Studio **için GitHub uzantısını**seçin ve **Değiştir'i**seçin.

    ![Visual Studio yükleyicisinde GitHub uzantısını seçme](media/create-project-repo/installation-github-extension.png)

2. Visual Studio’yu başlatın.

3. GitHub veya Azure DevOps'> bağlanabileceğiniz veya bir depoyu klonlayabildiğiniz Team Explorer penceresini açmak için Takım **Gezgini'ni** **Görüntüle'yi** seçin.

    ![Azure DevOps, GitHub ve bir depoyu klonlama gösteren takım gezgini penceresi](media/create-project-repo/team-explorer-devops.png)

4. **Yerel Git Depoları**altında URL alanında `https://github.com/Microsoft/samples-for-ai`, girin , klonlanmış dosyalar için bir klasör girin ve **Klon**seçin.

    > [!Tip]
    > Team Explorer'da belirttiğiniz klasör, klonlanan dosyaları almak için belirli klasördür. Komutun `git clone` aksine, Team Explorer'da bir klon oluşturmak otomatik olarak deponun adını içeren bir alt klasör oluşturmaz.

5. Klonlama tamamlandığında, depo panosuna gitmek için Team Explorer'ın altındaki depo klasörünü çift tıklatın. **Çözümler**altında, **Yeni'yi**seçin.

    ![Takım gezgini penceresi, klondan yeni bir proje oluşturma](media/create-project-repo/team-explorer-new-project.png)

6. Görünen **Yeni Proje** iletişim kutusunda , "**Varolan Python Kodundan**" seçeneğini belirleyin, proje için bir ad belirtin, **Konum'u** depoyla aynı klasöre ayarlayın ve **Tamam'ı**seçin. Görünen sihirbazda **Finish'i**seçin.

7. Menüden **> Çözüm Gezgini'ni** Görüntüle'yi seçin.

8. Çözüm Gezgini'nde `TensorFlow Examples> MNIST` düğümü genişletin, `convolutional.py`sağ tıklatın ve **Başlangıç Dosyası olarak Ayarla'yı**seçin. Bu adım Visual Studio'ya projeyi çalıştırırken hangi dosyayı kullanması gerektiğini söyler.

9. Programı çalıştırmak için **Ctrl**+**F5** tuşuna basın veya Hata **Ayıklama > Başlat'ı** seçin. Bir hata görürseniz, önceki adımda çalışma dizini ayarını yeniden denetleyin.

10. Program başarılı bir şekilde çalıştığında, eğitim inizi ve test veri kümenizi indirmeye başladığını, ardından modeli eğitip hata oranınızı çıktınız göreceksiniz. Hata oranının zaman içinde düşmesini istiyorsunuz

    ![Python MNIST programından ilk çıktı](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Anaconda kullanıyorsanız ve eksik numpy hakkında bir hata almak, [Anaconda kullanmak için Python ortamını değiştirmeniz](../python/selecting-a-python-environment-for-a-project.md)gerekebilir.

11. TensorBoard ile ilerlemeyi görselleştirebilirsiniz. Projenizi sağ tıklatın ve **TensorBoard çalıştır'ı** tıklatın ve sonra çıkış TensorBoard günlüklerinin dizini seçin.

   ![çalışma tensorboard](media/create-project-repo/run-tensorboard.png)

12. Fazla mesaiyi azaltan hataya dikkat edin, bu da kalitenin iyileştiği anlamına gelir.

   ![çalışma tensorboard](media/create-project-repo/tensorboard.png)
