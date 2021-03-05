---
title: Makine adı ile bağlantı kurulamıyor &lt; &gt; . Makine ağ üzerinde bulunamadı. | Microsoft Belgeleri
description: 'Bu davranış, aşağıdaki koşullardan biri doğru olduğunda meydana gelir: (1) uzak bilgisayar bağlantınız kesildi. (2) uzak bilgisayardaki kullanıcı hesabınız devre dışı bırakıldı. (3) uzak bilgisayarın parolasının süresi doldu.'
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e0d83f043e020ad3c65ac0f986ec174fac95585
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146437"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Hata: makine &lt; adına bağlanılamıyor &gt; . Makine ağ üzerinde bulunamadı.
Bu davranış, aşağıdaki koşullardan biri doğru olduğunda meydana gelir:

- Uzak bilgisayarla bağlantınız kesildi.

- Uzak bilgisayardaki kullanıcı hesabınız devre dışı bırakıldı.

- Uzak bilgisayardaki parolanızın süresi doldu.

### <a name="to-resolve-this-behavior"></a>Bu davranışı çözümlemek için

- Yerel bilgisayarın ve uzak bilgisayarın aynı ağda bulunduğundan emin olun. Bunu yapmak için, uzak bilgisayara erişmeyi denemek üzere Microsoft Windows Explorer (veya dosya Gezgini) kullanın.

     '

- Uzak bilgisayara bağlanmak için kullandığınız kullanıcı hesabının etkinleştirildiğinden emin olun.

     '

- Uzak bilgisayara bağlanmak için kullandığınız parolanın geçerli olduğundan ve süresi dolmadığından emin olun.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
- [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)
