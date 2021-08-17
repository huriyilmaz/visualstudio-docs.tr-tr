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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 246cd6c88961206491f9f4a079331d60d9a18b52
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097226"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Hata: makine &lt; adına bağlanılamıyor &gt; . Makine ağ üzerinde bulunamadı.
Bu davranış, aşağıdaki koşullardan biri doğru olduğunda meydana gelir:

- Uzak bilgisayarla bağlantınız kesildi.

- Uzak bilgisayardaki kullanıcı hesabınız devre dışı bırakıldı.

- Uzak bilgisayardaki parolanızın süresi doldu.

### <a name="to-resolve-this-behavior"></a>Bu davranışı çözümlemek için

- Yerel bilgisayarın ve uzak bilgisayarın aynı ağda bulunduğundan emin olun. bunu yapmak için, uzak bilgisayara erişmeyi denemek üzere Microsoft Windows gezgini 'ni (veya dosya gezgini) kullanın.

     '

- Uzak bilgisayara bağlanmak için kullandığınız kullanıcı hesabının etkinleştirildiğinden emin olun.

     '

- Uzak bilgisayara bağlanmak için kullandığınız parolanın geçerli olduğundan ve süresi dolmadığından emin olun.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
- [hata ayıklayıcı Ayarlar ve hazırlığı](../debugger/debugger-settings-and-preparation.md)
