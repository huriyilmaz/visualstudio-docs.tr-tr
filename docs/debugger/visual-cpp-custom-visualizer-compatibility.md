---
title: Visual C/C++ Özel Görselleştirici Uyumluluğu
description: Visual Studio 2019'daki yeni bir özellik, eski C/C++ ifade değerlendiricisi eklentileri ve özel görselleştiricilerle uyumlu olabilir. Ayrıntılar için bu makaleye bakın.
ms.custom: SEO-VS-2020
ms.date: 01/28/2019
ms.prod: visual-studio-dev16
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4948a4a3b82e4b713d590ffc9c8f8283ca495ea4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051813"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C/C++ Özel Görselleştirici Uyumluluğu

C++ Visual Studio 2019'dan başlayarak, yoğun bellek kullanan bileşenlerini barındırmak için dış 64 bit işlem kullanan geliştirilmiş bir hata ayıklayıcı içerir. Bu güncelleştirmenin bir parçası olarak, C/C++ ifade değerlendiricisine yönelik belirli uzantıların yeni hata ayıklayıcıyla uyumlu olması için güncelleştirilmiş olması gerekir.

Şu anda eski bir C/C++ EE eklenti veya C/C++ özel görselleştiricisi tüketiyorsanız, Araçlar Seçenekler Hata Ayıklama'ya gidip dış işlemde hata ayıklama simgelerini yükle  >    >   **'yi (yalnızca yerel)** seçerek bu dış işlem kullanımını kapatabilirsiniz. Bu seçeneğin seçimini kaldırsanız, IDE (devenv.exe) işlemi içinde bellek kullanımında önemli bir artış oluşur. Bu nedenle, büyük projelerde hata ayıklamayı bekliyorsanız, uzantının sahibiyle birlikte çalışarak bu hata ayıklama seçeneğiyle uyumlu olması önerilir.

Eski bir C/C++ EE eklentisinin veya C/C++ özel görselleştiricisinin sahibiyseniz, uzantınızı çalışan işlemi içinde yükleme hakkında daha fazla bilgi [için, Artık genişletilebilirlik](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting)örnekleri wiki'sinde bulabilirsiniz. [C/C++ özel görselleştiricisi örneğini de bulabilirsiniz.](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer)