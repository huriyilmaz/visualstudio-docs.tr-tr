---
title: -SafeMode (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 28480399238c1c915056d3929f8fd188cfff7eca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665503"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

@No__t_0, yalnızca varsayılan ortam ve Hizmetleri yükleyerek güvenli modda başlatır.

## <a name="syntax"></a>Sözdizimi

```
devenv /SafeMode
```

## <a name="remarks"></a>Açıklamalar
 Bu anahtar, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] başladığında tüm üçüncü taraf VSPackages 'leri önler ve bu sayede kararlı yürütme sağlar.

## <a name="description"></a>Açıklama
 Aşağıdaki örnek, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] güvenli modda başlatır.

## <a name="code"></a>Kod

```
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv Komut Satırı Anahtarları](../../ide/reference/devenv-command-line-switches.md)
