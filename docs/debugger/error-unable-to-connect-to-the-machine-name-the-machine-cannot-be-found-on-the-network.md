---
title: Hata-makine &lt; adına bağlanılamıyor &gt; . Makine ağ üzerinde bulunamadı. | Microsoft Belgeleri
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
ms.openlocfilehash: 8618a15ab4dcd6c9bbc0d9d8ab9bf347552883b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460149"
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