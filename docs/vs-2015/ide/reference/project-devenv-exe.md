---
title: -Proje (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- project Devenv switch (/project)
- Devenv, /project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f9c54691ed343493ef1e43798faf4d2ab6f60fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662117"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Derleme, Temizleme, yeniden oluşturma veya dağıtma için belirtilen çözüm yapılandırması içinde tek bir projeyi tanımlar.

## <a name="syntax"></a>Sözdizimi

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName
[/project ProjName] [/projectconfig ProjConfigName]
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

- @No__t_0,/`clean`, `/rebuild` veya `/deploy` komutunun bir parçası kullanılmalıdır.

- Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

- Hatalar da dahil olmak üzere derlemeler için Özet bilgiler, **komut** penceresinde veya `/out` anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek
 Bu örnek, `MySolution` `Debug` çözüm yapılandırması içinde `Debug` proje yapı yapılandırması kullanarak proje `CSharpConsoleApp` oluşturur.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) [/ProjectConfig (devenv. exe)](../../ide/reference/projectconfig-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv. exe](../../ide/reference/clean-devenv-exe.md) ) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (](../../ide/reference/deploy-devenv-exe.md) devenv. exe) [/Out](../../ide/reference/out-devenv-exe.md) (devenv. exe)
