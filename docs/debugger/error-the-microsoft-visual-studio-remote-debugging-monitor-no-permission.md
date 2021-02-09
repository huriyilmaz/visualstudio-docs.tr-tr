---
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
ms.workload:
- multiple
ms.openlocfilehash: 150d49d25c8c39d927c64a2cd463a068559847b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871344"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Hata: Uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisinin bu bilgisayara bağlanma izni yok.

Bu hata, Visual Studio Uzaktan Hata Ayıklama İzleyicisi (msvsmon) çalıştırmayı deneyen kullanıcının yerel bilgisayarda bir hesabı olmadığında oluşur. Bu hata, eski hata ayıklama altyapısı kullanılarak uzaktan hata ayıklanırken oluşabilir.

## <a name="to-fix-this-problem"></a>Bu sorunu gidermek için

- Uzak bilgisayarda msvsmon çalıştıran kullanıcı hesabıyla aynı adı ve parolayı kullanarak, Visual Studio hata ayıklayıcısı ana bilgisayarına bir kullanıcı hesabı ekleyin.

   \- veya

- Msvsmon 'i yerel bilgisayara çağırma izni olan bir kullanıcı olarak çalıştırın. Bu, kullanıcının msvsmon bilgisayarında bir etki alanı kullanıcısı ve yönetici olması gerektiği anlamına gelir. Msvsmon çalıştırmak için Kullanıcı hesabını iki şekilde belirtebilirsiniz:

  - Msvsmon simgesine sağ tıklayın ve kısayol menüsünde **Farklı Çalıştır** ' ı seçin.

    \- veya

  - Komut Isteminde komutunu çalıştırın `runas.exe` .

## <a name="see-also"></a>Ayrıca bkz.

- [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)