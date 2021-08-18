---
description: Bu hata, Visual Studio Uzaktan Hata Ayıklama İzleyicisi (msvsmon) çalıştırmaya çalışan kullanıcının yerel bilgisayarda bir hesabı yoksa oluşur.
title: Uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisinin bu bilgisayara bağlanma izni yok
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c47e28d061b710c8a4782852f7b3e736bf9520ef
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134083"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Hata: Uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisinin bu bilgisayara bağlanma izni yok.

Bu hata, Visual Studio Uzaktan Hata Ayıklama İzleyicisi (msvsmon) çalıştırmaya çalışan kullanıcının yerel bilgisayarda bir hesabı yoksa oluşur. Eski hata ayıklama altyapısı kullanılarak uzaktan hata ayıklaması sırasında bu hata oluşabilir.

## <a name="to-fix-this-problem"></a>Bu sorunu çözmek için

- Visual Studio hata ayıklayıcısı ana bilgisayarına, uzak bilgisayarda msvsmon çalıştıran kullanıcı hesabıyla aynı ad ve parola ile bir kullanıcı hesabı ekleyin,

   \- veya -

- msvsmon'ı yerel bilgisayara çağırma izni olan bir kullanıcı olarak çalıştırın. Bu, kullanıcının msvsmon bilgisayarda bir etki alanı kullanıcısı ve yönetici olması gerektiğini belirtir. msvsmon'ı çalıştırmak için kullanıcı hesabını iki şekilde belirtebilirsiniz:

  - msvsmon simgesine sağ tıklayın ve kısayol menüsünde **Farklı** Çalıştır'ı seçin

    \- veya -

  - Komut İstemi'nde komutunu `runas.exe` çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
