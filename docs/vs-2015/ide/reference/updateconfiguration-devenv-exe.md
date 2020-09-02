---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50773821b328ea81381744bc6f32b3907cd1c5bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657916"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Sistemdeki paketleri birleştirmeye ve tüm DEĞIŞIKLIKLER için MEF önbelleğini denetlemeye bildirir.

## <a name="syntax"></a>Syntax

```
devenv /updateconfiguration
```

## <a name="remarks"></a>Açıklamalar
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bir VSıX paketi yüklediğinizde bu komutu otomatik olarak çalıştırır. `devenv.exe /updateconfiguration`MEF önbelleğini güncelleştiren şekilde dosyalarınıza düzeltme eki uygulandıktan sonra çalıştırmalısınız [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Bu, Düzeltmelerinizin yeterli olup olmadığını değerlendirmenizi sağlar.

## <a name="example"></a>Örnek
 Aşağıdaki komut satırı, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sistemdeki paketleri birleştirmeye ve tüm DEĞIŞIKLIKLER için MEF önbelleğini denetlemeye neden olur.

```
Devenv.exe /updateconfiguration
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Devenv komut satırı anahtarlarında](../../ide/reference/devenv-command-line-switches.md) geliştirme ayarlarını özelleştirme
