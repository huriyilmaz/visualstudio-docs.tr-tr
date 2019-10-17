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
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430623"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C/C++ özel görselleştiricisi uyumluluğu

Visual Studio 2019 ' den itibaren C++ , yoğun bellek gerektiren bileşenleri barındırmak için bir dış 64 bit işlem kullanan geliştirilmiş bir hata ayıklayıcı içerir. Bu güncelleştirmenin bir parçası olarak, C/C++ Expression değerlendirici için bazı uzantıların yeni hata ayıklayıcı ile uyumlu hale getirmek için güncelleştirilmeleri gerekir.

Şu andaC++ eski bir c/Ee eklentisi veya c/C++ özel görselleştiricisi kullanıyorsanız, bu dış işlemin kullanımını devre dışı bırakabilirsiniz  > **Seçenekler** > **hata ayıklama**ve sonra **hata ayıklama yükleme kaldırma Dış işlemdeki semboller (yalnızca yerel)** . Bu seçeneğin işaretini kaldırırsanız, IDE (devenv. exe) işlemi içinde bellek kullanımında önemli bir artış oluşur. Bu nedenle, büyük projelerde hata ayıklamayı düşünüyorsanız, bu hata ayıklama seçeneği ile uyumlu hale getirmek için uzantının sahibiyle çalışmanız önerilir.

Eski bir C/C++ Ee eklentisi veya c/C++ özel görselleştiricisi sahibiyseniz, uzantınızı, [conkablosu genişletilebilirlik örnekleri wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting)'deki bir çalışan işleminde yükleme konusunda daha fazla bilgi edinebilirsiniz. Ayrıca, [C/C++ özel bir Görselleştirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer)de bulabilirsiniz.