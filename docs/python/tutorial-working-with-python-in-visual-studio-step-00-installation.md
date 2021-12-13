---
title: Visual Studio eğitim adım 0, yükleme
titleSuffix: ''
description: Visual Studio 'de Python ile çalışmaya yönelik temel bir izlenecek yolun 0. adımı (yükleme önkoşulları).
ms.date: 09/14/2021
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.custom: vs-acquisition
ms.workload:
- python
- data-science
ms.openlocfilehash: f02fc5c537bbbdaa80b40f989014c14e36aacd46
ms.sourcegitcommit: 0f2af2f1a8cf0a481fd8f673accf3aebf2e262c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "134714821"
---
# <a name="install-python-support-in-visual-studio"></a>Visual Studio’da Python desteğini yükleme

> [!Note]
> Python desteği şu anda yalnızca Windows için Visual Studio kullanılabilir. Mac ve Linux 'ta Python desteği [Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial)aracılığıyla kullanılabilir.

1. Windows için en son Visual Studio yükleyiciyi indirin ve çalıştırın. Sürüm 15,2 ve sonrasında Python desteği mevcuttur. zaten Visual Studio yüklüyse, **araçlar**  >  **araçlar ve özellikler ekle**' yi seçerek Visual Studio açın ve yükleyiciyi çalıştırın.

    > [!div class="nextstepaction"]
    > [Visual Studio Community yüklensin](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Community sürümü bireysel geliştiriciler, ders öğrenimi, akademik araştırmalar ve açık kaynak geliştirme içindir. diğer kullanımlar için [Visual Studio Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) veya [Visual Studio Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)yükler.

1. Yükleyici, belirli geliştirme alanlarında ilgili seçenek grupları olan iş yüklerinin bir listesini sağlar. Python için **Python geliştirme** iş yükünü seçin ve **yüklemeyi** seçin:

    ![Visual Studio yükleyicisinde seçilen Python geliştirme iş yükünün ekran görüntüsü.](media/installation-python-workload.png)

1. python desteğini hızlıca test etmek için Visual Studio başlatın, **Alt** + **i** tuşlarına basarak **Python etkileşimli** penceresini açın ve girin `2+2` . **4** çıkışını görmüyorsanız, adımlarınızı yeniden denetleyin.

    ::: moniker range="<=vs-2019"
    ![Etkileşimli pencere aracılığıyla Python test etme ekran görüntüsü.](media/installation-interactive-test.png)
    ::: moniker-end

    ::: moniker range=">=vs-2022"
    ![Visual Studio 2022 etkileşimli penceresi aracılığıyla Python test etme ekran görüntüsü.](media/vs-2022/python-interactive.png)
    ::: moniker-end

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [1. Adım: Python projesi oluşturma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Mevcut bir Python yorumlayıcısını el ile tanımla](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2022 ' de Python desteği 'ni yükler](installing-python-support-in-visual-studio.md#visual-studio-2022)
- [Visual Studio 2019 ' de Python desteği 'ni yükler](installing-python-support-in-visual-studio.md#visual-studio-2019)
- [Visual Studio 2015 ' de Python desteği 'ni yükler](installing-python-support-in-visual-studio.md#visual-studio-2015)
