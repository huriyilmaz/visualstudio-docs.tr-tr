---
title: 'Python in Visual Studio öğreticisi 0. adım, yükleme'
titleSuffix: ''
description: Visual Studio'da Python ile çalışmaya temel bir kılavuz olan 0. adım (yükleme önkoşulları).
ms.date: 02/01/2022
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.custom: 'vs-acquisition, devdivchpfy22'
ms.workload:
  - python
  - data-science
---

# <a name="install-python-support-in-visual-studio"></a>Visual Studio’da Python desteğini yükleme

> [!Note]
> Python desteği şu anda yalnızca Visual Studio için Windows. Mac ve Linux'ta Python desteği, [Visual Studio Code.](https://code.visualstudio.com/docs/python/python-tutorial)

1. Uygulama için en son Visual Studio yükleyicisini indirin ve Windows. Python desteği 15.2 ve sonraki sürümlerde kullanılabilir. Daha önce Visual Studio, Araçları ve Visual Studio'yi  >  seçerek **yükleyiciyi açın ve çalıştırın**.

    > [!div class="nextstepaction"]
    > [Yükleme Visual Studio Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Bu Community bireysel geliştiricilere, sınıf öğrenimine, akademik araştırmalara ve açık kaynak geliştirmeye göre tasarlanmıştır. Diğer kullanımlar için, [Visual Studio Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) veya [Visual Studio Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted).

1. Yükleyici, belirli geliştirme alanları için ilgili seçeneklerin grupları olan iş yüklerinin bir listesini sağlar. Python için Python geliştirme iş **yükünü seçin ve** Yükle'yi **seçin**:

    ![Uygulama yükleyicisinde seçilen Python geliştirme iş yükünün Visual Studio görüntüsü.](media/installation-python-workload.png)

1. Python desteğini hızlı bir şekilde test etmek Visual Studio **AltI tuşuna**+ basarak **Python Etkileşimli penceresini açın** ve girin`2+2`. **4** çıkışını görmüyorsanız adımlarınızı yeniden işaretleyin.

    ::: moniker range="<=vs-2019"
    ![Etkileşimli pencerede Python'ın test  denemesi ekran görüntüsü.](media/installation-interactive-test.png)
    ::: moniker-end

    ::: moniker range=">=vs-2022"
    ![Visual Studio 2022 etkileşimli penceresinde Python'ın test 2022'de test etme ekran görüntüsü.](media/vs-2022/python-interactive.png)
    ::: moniker-end

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [1. Adım: Python projesi oluşturma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2022'de Python desteğini yükleme](installing-python-support-in-visual-studio.md#visual-studio-2022)
- [Visual Studio 2019'da Python desteğini yükleme](installing-python-support-in-visual-studio.md#visual-studio-2019)
- [Visual Studio 2015'te Python desteğini yükleme](installing-python-support-in-visual-studio.md#visual-studio-2015)
- [Mevcut Python yorumlayıcıyı el ile tanımlama](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
