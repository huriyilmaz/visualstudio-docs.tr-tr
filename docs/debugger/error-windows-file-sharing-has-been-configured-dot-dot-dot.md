---
description: Windows paylaşımı, uzak bilgisayara farklı bir kullanıcı adı kullanarak bağlanacak şekilde yapılandırıldı.
title: Windows paylaşımı yapılandırıldı... | Microsoft Docs
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
ms.openlocfilehash: 2c0ea67f32474b124d4f6e4987de6a0491b6aaba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154362"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Hata: Windows dosya paylaşımı yapılandırıldı...
Windows paylaşımı, uzak bilgisayara farklı bir kullanıcı adı kullanarak bağlanacak şekilde yapılandırıldı. Bu, uzaktan hata ayıklamayla uyumsuzdur

 Geçerli dosya paylaşımı yapılandırması, farklı bir kullanıcı adı kullanarak uzak bilgisayara bağlanacak şekilde ayarlanır. Bu senaryoda uzaktan hata ayıklama mümkün değildir.

 Bu hatayı düzeltmek için, diğer hesap adını kullanarak bilgisayarda oturum açın veya dosya paylaşımını, hata ayıklamak istediğiniz hesap adını kullanmak üzere değiştirebilirsiniz.

 Bu kullanıcı adını kullanarak uzak bilgisayara bağlanmak için önce uzak bilgisayar bağlantısını kesmelisiniz.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Diğer hesap adını kullanarak yerel makinede( hata ayıklarken) oturum açın.

     —veya—

     . Uzak bilgisayarla bağlantıyı kesin ve ardından dosya paylaşımını hesap adınızla diğer makineye bağlanmak için yeniden yapılandırabilirsiniz:

    1. Başlat menüsünde **Donatılar'ın** üzerine **gelin** ve ardından Komut **İstemi'ne tıklayın.**

    2. Komut Windows yazın:

         `net use /delete computer_name`

    3. Dosya paylaşım ayarlarınızı, yardım için belgelenmiş yöntemlerden birini Windows değiştirin.
