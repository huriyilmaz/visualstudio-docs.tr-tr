---
title: -SafeMode (devenv.exe) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665503"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Güvenli modda başlatılır, yalnızca varsayılan ortam ve hizmetler yükleniyor.

## <a name="syntax"></a>Syntax

```
devenv /SafeMode
```

## <a name="remarks"></a>Açıklamalar
 Bu anahtar, başlatıldığında tüm üçüncü taraf VSPackages 'nin yüklenmesini engeller [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve böylece kararlı yürütmeyi sağlar.

## <a name="description"></a>Açıklama
 Aşağıdaki örnek [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] güvenli modda başlatılır.

## <a name="code"></a>Kod

```
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv Komut Satırı Anahtarları](../../ide/reference/devenv-command-line-switches.md)
