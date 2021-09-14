---
title: Visual Studio eğitim adım 0, yükleme
titleSuffix: ''
description: Visual Studio 'de Python ile çalışmaya yönelik temel bir izlenecek yolun 0. adımı (yükleme önkoşulları).
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: vs-acquisition
ms.workload:
- python
- data-science
ms.openlocfilehash: ae1ee69e663e96f0456c351cc0446b5ba2bd69ff
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628281"
---
# <a name="install-python-support-in-visual-studio"></a>Visual Studio’da Python desteğini yükleme

> [!Note]
> Python desteği şu anda yalnızca Windows için Visual Studio kullanılabilir; Mac ve Linux 'ta Python desteği [Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial)aracılığıyla kullanılabilir.

1. Windows için en son Visual Studio yükleyiciyi indirin ve çalıştırın (sürüm 15,2 ve üzeri sürümlerde Python desteği mevcuttur). zaten Visual Studio yüklüyse, Visual Studio yükleyiciyi çalıştırın ve 2. adıma gidin.

    > [!div class="nextstepaction"]
    > [Visual Studio Community yüklensin](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Community sürümü bireysel geliştiriciler, ders öğrenimi, akademik araştırmalar ve açık kaynak geliştirme içindir. diğer kullanımlar için [Visual Studio Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) veya [Visual Studio Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)yükler.

1. Yükleyici, belirli bir geliştirme alanı için ilgili seçeneklerin grupları olan iş yüklerinin bir listesini sunar. Python için **Python geliştirme** iş yükünü seçin ve **yüklemeyi** seçin:

    ![Visual Studio yükleyicisinde Python geliştirme iş yükü](media/installation-python-workload.png)

1. python desteğini hızlıca test etmek için Visual Studio başlatın, **Alt** + **i** tuşlarına basarak **Python etkileşimli** penceresini açın ve girin `2+2` . **4** çıkışını görmüyorsanız, adımlarınızı yeniden denetleyin.

    ![Etkileşimli pencere aracılığıyla Python test etme](media/installation-interactive-test.png)

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [1. Adım: Python projesi oluşturma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Mevcut bir Python yorumlayıcısını el ile tanımla](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2015 ve önceki sürümlerde Python desteği yüklemesi](installing-python-support-in-visual-studio.md)
- [Konum yüklemeleri](installing-python-support-in-visual-studio.md#install-locations)
