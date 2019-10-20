---
title: -Build (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 419716d750771908a43318d051cb0b4681d35149
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660981"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Belirtilen çözüm yapılandırma dosyasını kullanarak bir çözüm oluşturur.

## <a name="syntax"></a>Sözdizimi

```
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Arguments
 `SolutionName` gerekiyor. Çözüm dosyasının tam yolu ve adı.

 `SolnConfigName` gerekiyor. @No__t_0 adlı çözümü oluşturmak için kullanılacak Çözüm yapılandırmasının adı.

 /Project Isteğe bağlı `ProjName`. Çözüm içindeki bir proje dosyasının yolu ve adı. @No__t_0 klasöründen proje dosyasına veya projenin görünen adına veya proje dosyasının tam yolunu ve adına göreli bir yol girebilirsiniz.

 /ProjectConfig Isteğe bağlı `ProjConfigName`. Adlı `/project` oluşturulurken kullanılacak bir proje derleme yapılandırması adı.

## <a name="remarks"></a>Açıklamalar
 Bu anahtar, tümleşik geliştirme ortamı (IDE) içinde **yapı çözümü** menü komutu ile aynı işlevi gerçekleştirir.

 Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

 Hatalar da dahil olmak üzere derlemeler için Özet bilgiler, **komut** penceresinde veya `/out` anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

 Bu komut yalnızca son derlemeden bu yana değiştirilen projeleri oluşturur. Bir Çözümdeki tüm projeleri oluşturmak için [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)kullanın.

## <a name="example"></a>Örnek
 Bu örnek, `MySolution` `Debug` çözüm yapılandırması içinde `Debug` proje yapı yapılandırması kullanarak proje `CSharpConsoleApp` oluşturur.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'Da projeler ve çözümler oluşturma ve Temizleme](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/Clean (devenv.](../../ide/reference/clean-devenv-exe.md) exe) [/Out (devenv. exe](../../ide/reference/out-devenv-exe.md) )
