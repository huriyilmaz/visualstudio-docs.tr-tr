---
title: -Updateconfiguration (devenv. exe) | Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657916"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv. exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sistemdeki [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] paketlerini birleştirmek ve tüm değişiklikler için MEF önbelleğini denetlemek [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bildirir.

## <a name="syntax"></a>Sözdizimi

```
devenv /updateconfiguration
```

## <a name="remarks"></a>Açıklamalar
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bir VSıX paketi yüklediğinizde bu komutu otomatik olarak çalıştırır. @No__t_1 MEF önbelleğini güncelleştirmesi için dosyalarınızda düzeltme eki uygulandıktan sonra `devenv.exe /updateconfiguration` çalıştırmalısınız. Bu, Düzeltmelerinizin yeterli olup olmadığını değerlendirmenizi sağlar.

## <a name="example"></a>Örnek
 Aşağıdaki komut satırı, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sistemdeki [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] paketlerini birleştirmeye ve tüm değişiklikler için MEF önbelleğini denetlemeye neden olur.

```
Devenv.exe /updateconfiguration
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Devenv komut satırı anahtarlarında](../../ide/reference/devenv-command-line-switches.md) geliştirme ayarlarını özelleştirme
