---
title: 'Hata: &lt;name &gt; makineye bağlanılamıyor. Makine ağ üzerinde bulunamadı. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 7d0f820156714a726d506d8871d4e42a8dc12a23
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736830"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Hata: &lt;name &gt; makineye bağlanılamıyor. Makine ağ üzerinde bulunamadı.
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
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
- [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)