---
title: Python in Visual Studio öğreticisi 0. adım, yükleme
titleSuffix: ''
description: Visual Studio'da Python ile çalışmaya temel bir kılavuz olan 0. adım (yükleme önkoşulları) .
ms.date: 09/14/2021
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: vs-acquisition
ms.workload:
- python
- data-science
ms.openlocfilehash: 1e712d5df44dd87f07b50b243e8e63ed9e1ad0bf
ms.sourcegitcommit: 59613afd06a8f184efab8e108410066824a2b712
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2021
ms.locfileid: "127920074"
---
# <a name="install-python-support-in-visual-studio"></a>Visual Studio’da Python desteğini yükleme

> [!Note]
> Python desteği şu anda yalnızca Visual Studio Windows. Mac ve Linux'ta Python desteği, [Visual Studio Code.](https://code.visualstudio.com/docs/python/python-tutorial)

1. Uygulama için en son Visual Studio yükleyicisini indirin ve Windows. Python desteği 15.2 ve sonraki sürümlerde mevcuttur. Daha önce Visual Studio, Araç Ve Visual Studio Ekle'yi seçerek **yükleyiciyi** açın ve  >  **yükleyiciyi çalıştırın.**

    > [!div class="nextstepaction"]
    > [Yükleme Visual Studio Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Bu Community bireysel geliştiricilere, sınıf öğrenimine, akademik araştırmalara ve açık kaynak geliştirmeye göre tasarlanmıştır. Diğer kullanımlar için, [Visual Studio Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) veya [Visual Studio Enterprise.](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

1. Yükleyici, belirli geliştirme alanları için ilgili seçenekler grupları olan iş yüklerinin listesini sunar. Python için Python geliştirme iş **yükünü seçin ve** Yükle'yi **seçin:**

    ![Uygulama yükleyicisinde seçilen Python geliştirme iş yükünün Visual Studio görüntüsü.](media/installation-python-workload.png)

1. Python desteğini hızlı bir şekilde test etmek **Visual Studio, Alt** I tuşuna +  basarak Python Etkileşimli **penceresini açın** ve `2+2` girin. **4** çıkışını görmüyorsanız, adımlarınızı yeniden işaretleyin.

    ::: moniker range="<=vs-2019"
    ![Etkileşimli pencerede Python'ın test denemesi ekran görüntüsü.](media/installation-interactive-test.png)
    ::: moniker-end

    ::: moniker range=">=vs-2022"
    ![Visual Studio 2022 etkileşimli penceresinden Python'ın test şekilde test 2022 ekran görüntüsü.](media/vs-2022/python-interactive.png)
    ::: moniker-end

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [1. Adım: Python projesi oluşturma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Mevcut Python yorumlayıcıyı el ile tanımlama](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2015 ve önceki sürümlerde Python desteğini yükleme](installing-python-support-in-visual-studio.md)
- [Yükleme konumları](installing-python-support-in-visual-studio.md#install-locations)
