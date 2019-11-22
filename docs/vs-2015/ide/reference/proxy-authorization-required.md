---
title: Ara sunucu yetkilendirmesi gerekli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848817691d7fae32f2240e3d6cac4451c4ce58c4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297812"
---
# <a name="proxy-authorization-required"></a>Proxy Yetkilendirmesi Gerekiyor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Ara sunucu yetkilendirmesi gerekli** hatası genellikle, kullanıcılar bir ara sunucu aracılığıyla Visual Studio Online kaynaklarına bağlandığında oluşur ve proxy sunucusu çağrıları engeller.

Bu hatayı düzeltmek için aşağıdaki adımlardan birini veya daha fazlasını deneyin:

- Visual Studio'yu yeniden başlatın. Bir ara sunucu kimlik doğrulaması iletişim kutusu görünür. İletişim kutusunda kimlik bilgilerinizi girin.

- Yukarıdaki adım sorunu çözmezse, bu durum proxy sunucunuzun https://go.microsoft.com adresler için kimlik bilgilerini istemez ancak *. visualStudio.com adresleri için bunu yapar. Bu sunucular için, Visual Studio 'daki tüm oturum açma senaryolarının engellemesini kaldırmak için izin verilenler listesine aşağıdaki URL 'Leri eklemeniz gerekir:

  - *.windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- https://go.microsoft.com adresini izin verilenler listesinden kaldırabilirsiniz. böylece, Visual Studio yeniden başlatıldığında hem https://go.microsoft.com adresi hem de sunucu uç noktaları için proxy kimlik doğrulama iletişim kutusu görünür.

- Proxy 'niz ile varsayılan kimlik bilgilerinizi kullanmak istiyorsanız, aşağıdakileri yapın:

   1. : **%ProgramFiles%\Microsoft Visual Studio 14.0 \ Common7\IDE** (veya **% ProgramFiles (x86)% \ Microsoft Visual Studio 14.0 \ Common7\IDE**) içinde devenv. exe. config (devenv. exe yapılandırma dosyası) bulun.

   2. Yapılandırma dosyasında `<system.net>` bloğunu bulun ve şu kodu ekleyin:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      `proxyaddress="<http://<yourproxy:port#>`ağ için doğru proxy adresini ekleyin.

- Proxy 'yi kullanmanıza izin veren kodu eklemek için [Bu blog gönderisine](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) ilişkin yönergeleri izleyin.
