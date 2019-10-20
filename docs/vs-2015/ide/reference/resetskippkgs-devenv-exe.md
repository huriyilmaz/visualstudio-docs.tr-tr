---
title: -ResetSkipPkgs (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 207ceb92d84c2186aeec49c205d8d32f4d7aa969
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665569"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

, Sorun VSPackages 'ın yüklenmesinin önüne geçmek isteyen kullanıcılar tarafından VSPackages 'a eklenen yüklemeyi atlama seçeneklerini temizler, sonra [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] başlatır.

## <a name="syntax"></a>Sözdizimi

```
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Açıklamalar
 Bir Skipyükleme etiketinin varlığı, VSPackage yüklemesini devre dışı bırakır. etiketi temizlemek, VSPackage yüklemesini yeniden etkinleştirilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, tüm Skipyükleme etiketlerini temizler.

```
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv Komut Satırı Anahtarları](../../ide/reference/devenv-command-line-switches.md)
