---
title: Visual C/C++ özel görselleştiricisi uyumluluğu
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
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 9fdd44be89fde2fbc26038c8b88fff405876264f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72430623"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C/C++ özel görselleştiricisi uyumluluğu

C++, Visual Studio 2019 ' den başlayarak, yoğun bellek gerektiren bileşenleri barındırmak için bir dış 64 bit işlem kullanan geliştirilmiş bir hata ayıklayıcı içerir. Bu güncelleştirmenin bir parçası olarak, C/C++ ifade değerlendiricisi için bazı uzantılar, yeni hata ayıklayıcı ile uyumlu hale getirmek için güncelleştirilmeleri gerekir.

Şu anda eski bir c/c++ Ee eklentisi veya c/c++ özel görselleştiricisi kullanıyorsanız, bu dış işlemin kullanımını **Araçlar**  >  **Seçenekler**  >  **hata ayıklaması**' na giderek kapatabilir ve sonra **dış işlemdeki hata ayıklama sembollerini yükle (yalnızca yerel)** seçimini kaldırabilirsiniz. Bu seçeneğin işaretini kaldırırsanız, IDE (devenv.exe) işlemi içinde bellek kullanımında önemli bir artış oluşur. Bu nedenle, büyük projelerde hata ayıklamayı düşünüyorsanız, bu hata ayıklama seçeneği ile uyumlu hale getirmek için uzantının sahibiyle çalışmanız önerilir.

Eski bir C/C++ EE eklentisi veya C/C++ özel görselleştiricisi sahibiyseniz, uzantınızı [Conkablosu genişletilebilirlik örnekleri wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting)'deki bir çalışan işleminde yükleme konusunda daha fazla bilgi edinebilirsiniz. [C/C++ özel görselleştiricisi örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer)de bulabilirsiniz.