---
title: -Proje (devenv.exe) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662117"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Derleme, Temizleme, yeniden oluşturma veya dağıtma için belirtilen çözüm yapılandırması içinde tek bir projeyi tanımlar.

## <a name="syntax"></a>Söz dizimi

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName
[/project ProjName] [/projectconfig ProjConfigName]
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

- `devenv /build`,/ `clean` , `/rebuild` Veya komutunun bir parçası olarak kullanılmalıdır `/deploy` .

- Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

- Hatalar da dahil olmak üzere derlemeler için Özet bilgiler, **komut** penceresinde veya anahtarla belirtilen herhangi bir günlük dosyasında görüntülenebilir `/out` .

## <a name="example"></a>Örnek
 Bu örnek, `CSharpConsoleApp` ' `Debug` nin çözüm yapılandırmasındaki proje derleme yapılandırması ' nı kullanarak projeyi oluşturur `Debug` `MySolution` .

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) [/projectconfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md) [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
