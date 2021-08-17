---
description: bu hata, Visual Studio Uzaktan Hata Ayıklama İzleyicisi (msvsmon) çalıştırmayı deneyen kullanıcının yerel bilgisayarda bir hesabı olmadığında oluşur.
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
ms.openlocfilehash: 693ea4cbd24937c1603b4e029bbc9670f7c9e90f61c1fa66d7aeb2265ebc2fc4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420124"
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
