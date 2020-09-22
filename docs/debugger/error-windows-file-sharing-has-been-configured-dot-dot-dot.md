---
title: Windows dosya paylaşımı yapılandırıldı... | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17dbb1f3493ead985ac946331fdbff7933b6d604
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851677"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Hata: Windows dosya paylaşımı yapılandırıldı...
Windows dosya paylaşımı, uzak bilgisayara farklı bir Kullanıcı adı kullanarak bağlanacak şekilde yapılandırılmıştır. Bu, uzaktan hata ayıklama ile uyumsuzdur

 Geçerli dosya paylaşım yapılandırması, uzak bilgisayara farklı bir Kullanıcı adı kullanılarak bağlanacak şekilde ayarlanır. Bu senaryoda Uzaktan hata ayıklama mümkün değildir.

 Bu hatayı düzeltmek için, diğer hesap adını kullanarak bilgisayarda oturum açın veya dosya paylaşımını, altında hata ayıkladığınız hesap adını kullanacak şekilde değiştirin.

 Bu Kullanıcı adını kullanarak uzak bilgisayara bağlanmak istiyorsanız, öncelikle uzak bilgisayar bağlantısını kesmeniz gerekir.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Diğer hesap adını kullanarak yerel makinenizde, hata ayıkladığınız makinede oturum açın.

     —veya—

     . Uzak bilgisayarla bağlantısını kesin ve ardından, hesap adınızı kullanarak diğer makineye bağlanmak için dosya paylaşımını yeniden yapılandırın:

    1. **Başlat** menüsünde, **Donatılar**' ın üzerine gelin ve ardından **komut istemi**' ne tıklayın.

    2. Windows komut isteminde şunu yazın:

         `net use /delete computer_name`

    3. Windows Yardımı 'nda belgelenen yöntemlerden birini kullanarak dosya paylaşım ayarlarınızı değiştirin.