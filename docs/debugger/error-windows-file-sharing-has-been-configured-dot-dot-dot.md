---
description: Windows dosya paylaşımı, uzak bilgisayara farklı bir kullanıcı adı kullanarak bağlanacak şekilde yapılandırılmıştır.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 19574e8b77c163c96ab63617a84703806fd145e881058e6d6037618d675642d2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121362863"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Hata: Windows dosya paylaşımı yapılandırıldı...
Windows dosya paylaşımı, uzak bilgisayara farklı bir kullanıcı adı kullanarak bağlanacak şekilde yapılandırılmıştır. Bu, uzaktan hata ayıklama ile uyumsuzdur

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

    3. dosya paylaşım ayarlarınızı Windows yardım altında belgelenen yöntemlerden birini kullanarak değiştirin.
