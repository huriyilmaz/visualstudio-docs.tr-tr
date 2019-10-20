---
title: -Deploy (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 620be9ea458d55a8c9610079b357cc9466a03f56
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660779"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir derleme veya yeniden derlemeden sonra bir çözüm dağıtır. Yalnızca yönetilen kod projeleri için geçerlidir.

## <a name="syntax"></a>Sözdizimi

```
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]
```

## <a name="arguments"></a>Arguments
 `SolnConfigName` gerekiyor. @No__t_0 adlı çözümü oluşturmak için kullanılacak Çözüm yapılandırmasının adı.

 `SolutionName` gerekiyor. Çözüm dosyasının tam yolu ve adı.

 /Project Isteğe bağlı `ProjName`. Çözüm içindeki bir proje dosyasının yolu ve adı. @No__t_0 klasöründen proje dosyasına veya projenin görünen adına veya proje dosyasının tam yolunu ve adına göreli bir yol girebilirsiniz.

 /ProjectConfig Isteğe bağlı `ProjConfigName`. Adlı `/project` oluşturulurken kullanılacak bir proje derleme yapılandırması adı.

## <a name="remarks"></a>Açıklamalar
 Belirtilen proje bir dağıtım projesi olmalıdır. Belirtilen proje bir dağıtım projesi değilse, derlenen proje dağıtılması için geçirildiğinde hata vererek başarısız olur.

 Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

 Hatalar da dahil olmak üzere derlemeler için Özet bilgiler, **komut** penceresinde veya `/out` anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek
 Bu örnek, `MySolution` `Release` çözüm yapılandırması içinde `Release` proje yapı yapılandırması kullanarak proje `CSharpConsoleApp` dağıtır.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) [/Project (devenv. exe)](../../ide/reference/project-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv. exe](../../ide/reference/clean-devenv-exe.md) ) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/Out (devenv](../../ide/reference/out-devenv-exe.md) . exe)
