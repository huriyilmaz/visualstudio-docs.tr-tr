---
title: -Yeniden derle (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 008169829a6cf76e959d00f010959239a5f390b5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665656"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Belirtilen çözüm yapılandırmasını temizler ve oluşturur.

## <a name="syntax"></a>Sözdizimi

```
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Arguments
 `SolnConfigName` gerekiyor. @No__t_0 adlı çözümü yeniden derlemek için kullanılacak Çözüm yapılandırmasının adı.

 `SolutionName` gerekiyor. Çözüm dosyasının tam yolu ve adı.

 /Project Isteğe bağlı `ProjName`. Çözüm içindeki bir proje dosyasının yolu ve adı. @No__t_0 klasöründen proje dosyasına veya projenin görünen adına veya proje dosyasının tam yolunu ve adına göreli bir yol girebilirsiniz.

 /ProjectConfig Isteğe bağlı `ProjConfigName`. Adlı `/project` yeniden oluşturulurken kullanılacak bir proje derleme yapılandırması adı.

## <a name="remarks"></a>Açıklamalar

- Bu anahtar, tümleşik geliştirme ortamı (IDE) içinde **çözümü yeniden derle** menü komutuyla aynı işlevi gerçekleştirir.

- Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

- Temizlerle ilgili özet bilgiler, hatalar da dahil olmak üzere, **komut** penceresinde veya `/out` anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek
 Bu örnek, `MySolution` `Debug` çözüm yapılandırması içinde `Debug` proje yapı yapılandırması kullanılarak proje `CSharpWinApp` temizler ve yeniden oluşturur.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv. exe](../../ide/reference/clean-devenv-exe.md) ) [/Out (devenv. exe](../../ide/reference/out-devenv-exe.md) )
