---
title: -ProjectConfig (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a33c7cbaef473e75631bb4ac6c0d217198cbf250
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662095"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

@No__t_0 bağımsız değişkeninde adlı projeyi derlediğinizde, temizledikten, yeniden oluşturduğunuzda veya dağıttığınızda uygulanacak bir proje derleme yapılandırması belirtir.

## <a name="syntax"></a>Sözdizimi

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Arguments
 /Build `/project` `ProjName` tarafından belirtilen projeyi oluşturur.

 /Clean, bir derleme sırasında oluşturulan tüm ara dosyaları ve çıkış dizinlerini temizler.

 /Rebuild Temizleme, daha sonra `/project` `ProjName` tarafından belirtilen projeyi oluşturur.

 /Deploy, projenin bir derleme veya yeniden oluşturma işleminden sonra dağıtılacağını belirtir.

 `SolnConfigName` gerekiyor. @No__t_0 adlı çözüme uygulanacak Çözüm yapılandırmasının adı.

 `SolutionName` gerekiyor. Çözüm dosyasının tam yolu ve adı.

 /Project Isteğe bağlı `ProjName`. Çözüm içindeki bir proje dosyasının yolu ve adı. @No__t_0 klasöründen proje dosyasına veya projenin görünen adına veya proje dosyasının tam yolunu ve adına göreli bir yol girebilirsiniz.

 /ProjectConfig Isteğe bağlı `ProjConfigName`. Adlı `/project` uygulanacak bir proje derleme yapılandırması adı.

## <a name="remarks"></a>Açıklamalar

- @No__t_1,/`clean`, `/rebuild` veya `/deploy` komutunun bir parçası olarak `/project` anahtarla kullanılmalıdır.

- Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

- Hatalar da dahil olmak üzere derlemeler için Özet bilgiler, **komut** penceresinde veya `/out` anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek
 Bu örnek, `MySolution` `Debug` çözüm yapılandırması içinde `Debug` proje yapı yapılandırması kullanarak proje `CSharpConsoleApp` oluşturur.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) [/Project (devenv. exe)](../../ide/reference/project-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv. exe](../../ide/reference/clean-devenv-exe.md) ) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy](../../ide/reference/deploy-devenv-exe.md) (devenv. [exe)](../../ide/reference/out-devenv-exe.md)
