---
title: -Kurulum (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a923d1f3532548ebc6ed651a0739e0e5792f7967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663529"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Menüleri, araç çubuklarını ve komut gruplarını açıklayan kaynak meta verilerini, tüm kullanılabilir VSPackages 'lerden birleştirmeye zorlar.

## <a name="syntax"></a>Syntax

```
devenv /setup
```

## <a name="remarks"></a>Açıklamalar
 Bu anahtar bağımsız değişken almaz. `devenv /setup`Komut genellikle yükleme işleminin son adımı olarak verilir. `/setup`Anahtarın kullanımı başlamaz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

 `devenv` [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) ve [/ınstallvstempsyonlar (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) anahtarlarını kullanabilmeniz için yönetici olarak çalıştırmanız gerekir.

## <a name="example"></a>Örnek
 Bu örnek, VSPackages içeren bir sürümünü yüklemenin son adımını gösterir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

```
devenv /setup
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv Komut Satırı Anahtarları](../../ide/reference/devenv-command-line-switches.md)
