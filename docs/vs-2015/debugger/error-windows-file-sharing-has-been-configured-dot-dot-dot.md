---
title: 'Hata: Windows dosya paylaşımı yapılandırıldı... | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c45a1b74-61ec-4c64-9e2c-13051a4f50a5
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96d65ae615522bcee43ddf5e8181e96eecc0d958
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157507"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Hata: Windows dosya paylaşımı yapılandırıldı...
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
