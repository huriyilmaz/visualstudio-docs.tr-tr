---
title: Kullanarak yalıtılmış Kabuğu değiştirme. Pkgundef dosyası | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eab02fe900e96ba37c63faae535974788f99ba78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538400"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>.Pkgundef Dosyası Kullanarak Yalıtılmış Kabuğu Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir yalıtılmış Kabuk uygulamasından belirtilen kayıt defteri girişlerini hariç tutmak için. pkgundef dosyasını değiştirebilirsiniz. Genellikle, bir uygulama bir bilgisayarda ilk kez başlatıldığında, Visual Studio Kabuğu mevcut Visual Studio kayıt defteri girişlerini uygulamanın kök kayıt defteri anahtarına kopyalar. Bu, şu anda yüklü VSPackages 'e yönelik tüm başvuruları içerir.  
  
 Yalıtılmış bir kabuk uygulamasından belirli bir kayıt defteri girişini dışlamak için, anahtar tarafından izlenen uygulama. pkgundef dosyasına ekleyin. Anahtarlar ve girdiler. pkgdef dosyasında olduğu gibi gösterilir; diğer bir deyişle, [$RootKey $] veya [$RootKey $ \\ *AltAnahtar*] ve "*Entry*" =*değeri*, burada *alt anahtar* , kaldırılacak olan anahtar, *giriş* , kaldırılacak giriştir ve *değeri* ya da olur `""` `dword:00000000` .  
  
 Birden çok girişi bir kayıt defteri anahtarından dışlamak için, anahtarı tek bir kez listeleyerek her girdinin hariç tutulması için bir satır gelmelidir.  
  
 Yalıtılmış bir kabuk uygulamasından tüm kayıt defteri anahtarını dışlamak için, anahtarı Application. pkgundef dosyasına ekleyin, ancak bu anahtar için herhangi bir kayıt defteri girişi belirtmeyin.  
  
 . Pkgundef dosyasına yorum ekleyebilirsiniz. Tek satırlık bir yorum, ilk iki karakterle iki eğik çizgiye sahip olmalıdır.  
  
 Örneğin, **Araçlar** menüsünde **veritabanına Bağlan** ve **r 'ye Bağlan** komutlarını kaldırmak için satırın açıklamasını kaldırabilirsiniz:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 ve şu satırı ekleyin:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 uygulamanın. pkgundef dosyasına.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio özelliklerinin paket GUID 'Leri](../extensibility/package-guids-of-visual-studio-features.md)   
 [Yalıtılmış Kabuğu Özelleştirme](../extensibility/customizing-the-isolated-shell.md)
