---
description: bu hata, Visual Studio Uzaktan Hata Ayıklama İzleyicisi (msvsmon) çalıştırmayı deneyen kullanıcının yerel bilgisayarda bir hesabı olmadığında oluşur.
title: Uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisinin bu bilgisayara bağlanma izni yok
titleSuffix: ''
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
ms.openlocfilehash: d9da7bd57c8032e1cb795550b040c53450a2c6b3
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972628"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Hata: Uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisinin bu bilgisayara bağlanma izni yok.

bu hata, Visual Studio Uzaktan Hata Ayıklama İzleyicisi (msvsmon) çalıştırmayı deneyen kullanıcının yerel bilgisayarda bir hesabı olmadığında oluşur. Bu hata, eski hata ayıklama altyapısı kullanılarak uzaktan hata ayıklanırken oluşabilir.

## <a name="to-fix-this-problem"></a>Bu sorunu gidermek için

- Visual Studio hata ayıklayıcı ana bilgisayara, uzak bilgisayarda msvsmon çalıştıran kullanıcı hesabıyla aynı adı ve parolayı kullanarak bir kullanıcı hesabı ekleyin.

   \- veya

- Msvsmon 'i yerel bilgisayara çağırma izni olan bir kullanıcı olarak çalıştırın. Bu, kullanıcının msvsmon bilgisayarında bir etki alanı kullanıcısı ve yönetici olması gerektiği anlamına gelir. Msvsmon çalıştırmak için Kullanıcı hesabını iki şekilde belirtebilirsiniz:

  - Msvsmon simgesine sağ tıklayın ve kısayol menüsünde **Farklı Çalıştır** ' ı seçin.

    \- veya

  - Komut Isteminde komutunu çalıştırın `runas.exe` .

## <a name="see-also"></a>Ayrıca bkz.

- [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
