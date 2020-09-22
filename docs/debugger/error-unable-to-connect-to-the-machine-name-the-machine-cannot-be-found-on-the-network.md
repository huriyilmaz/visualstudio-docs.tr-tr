---
title: Makine adı ile bağlantı kurulamıyor &lt; &gt; . Makine ağ üzerinde bulunamadı. | Microsoft Belgeleri
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1ab43773b4aa9d2535eb6ac157ec39333907731
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852517"
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
- [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)