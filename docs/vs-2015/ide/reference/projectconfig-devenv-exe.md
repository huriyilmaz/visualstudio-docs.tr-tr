---
title: -ProjectConfig (devenv.exe) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662095"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bağımsız değişkende adlı projeyi derlediğinizde, temizledikten, yeniden oluşturduğunuzda veya dağıttığınızda uygulanacak bir proje derleme yapılandırması belirtir `/project` .

## <a name="syntax"></a>Söz dizimi

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Bağımsız değişkenler
 /Build tarafından belirtilen projeyi oluşturur `/project` `ProjName` .

 /Clean, bir derleme sırasında oluşturulan tüm ara dosyaları ve çıkış dizinlerini temizler.

 /Rebuild temizler ve tarafından belirtilen projeyi oluşturur `/project` `ProjName` .

 /Deploy, projenin bir derleme veya yeniden oluşturma işleminden sonra dağıtılacağını belirtir.

 `SolnConfigName` Gerekli. İçinde adlı çözüme uygulanacak Çözüm yapılandırmasının adı `SolutionName` .

 `SolutionName` Gerekli. Çözüm dosyasının tam yolu ve adı.

 /Project `ProjName` isteğe bağlı. Çözüm içindeki bir proje dosyasının yolu ve adı. `SolutionName`Klasörden proje dosyasına ya da projenin görünen adına veya proje dosyasının tam yolunu ve adına göreli bir yol girebilirsiniz.

 /ProjectConfig `ProjConfigName` isteğe bağlıdır. Adlandırılmış bir proje yapı yapılandırmasının adı `/project` .

## <a name="remarks"></a>Açıklamalar

- `/project` `devenv /build` ,/ `clean` , `/rebuild` , Veya komutunun bir parçası olarak anahtar ile birlikte kullanılmalıdır `/deploy` .

- Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

- Hatalar da dahil olmak üzere derlemeler için Özet bilgiler, **komut** penceresinde veya anahtarla belirtilen herhangi bir günlük dosyasında görüntülenebilir `/out` .

## <a name="example"></a>Örnek
 Bu örnek, `CSharpConsoleApp` ' `Debug` nin çözüm yapılandırmasındaki proje derleme yapılandırması ' nı kullanarak projeyi oluşturur `Debug` `MySolution` .

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) [/project (devenv.exe)](../../ide/reference/project-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md) [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
