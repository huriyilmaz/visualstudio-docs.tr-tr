---
title: -Komutu (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9083d14c82eb2d283431e28d03bbbf96c14258cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660850"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Tümleşik geliştirme ortamı (IDE) başlatıldıktan sonra belirtilen komutu yürütür.

## <a name="syntax"></a>Söz dizimi

```
devenv /command CommandName
```

## <a name="arguments"></a>Bağımsız değişkenler
 `CommandName` Gerekli. Bir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] komutun veya diğer adının, çift tırnak işareti içine alınmış adı. Komut ve diğer ad sözdizimi hakkında daha fazla bilgi için bkz. [Visual Studio komutları](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Açıklamalar
 Başlangıç tamamlandıktan sonra IDE, adlandırılmış komutunu yürütür. Bu anahtarı kullanırsanız, IDE [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Başlangıçta başlangıç sayfasını görüntülemez.

 Bir eklenti bir komut kullanıma sunarsa, bu anahtarı komut satırından eklentiyi başlatmak için kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: eklenti yöneticisini kullanarak eklentileri denetleme](https://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).

## <a name="example"></a>Örnek
 Bu örnek [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , sık kullanılan dosyaları aç makrosunu başlatır ve otomatik olarak çalıştırır.

```
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
