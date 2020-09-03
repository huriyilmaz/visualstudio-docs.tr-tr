---
title: -Derleme (devenv.exe) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660981"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Belirtilen çözüm yapılandırma dosyasını kullanarak bir çözüm oluşturur.

## <a name="syntax"></a>Söz dizimi

```
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `SolutionName` Gerekli. Çözüm dosyasının tam yolu ve adı.

 `SolnConfigName` Gerekli. İçinde adlı çözümü derlemek için kullanılacak Çözüm yapılandırmasının adı `SolutionName` .

 /Project `ProjName` isteğe bağlı. Çözüm içindeki bir proje dosyasının yolu ve adı. `SolutionName`Klasörden proje dosyasına ya da projenin görünen adına veya proje dosyasının tam yolunu ve adına göreli bir yol girebilirsiniz.

 /ProjectConfig `ProjConfigName` isteğe bağlıdır. Adlandırılmış oluşturulurken kullanılacak bir proje derleme yapılandırması adı `/project` .

## <a name="remarks"></a>Açıklamalar
 Bu anahtar, tümleşik geliştirme ortamı (IDE) içinde **yapı çözümü** menü komutu ile aynı işlevi gerçekleştirir.

 Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

 Hatalar da dahil olmak üzere derlemeler için Özet bilgiler, **komut** penceresinde veya anahtarla belirtilen herhangi bir günlük dosyasında görüntülenebilir `/out` .

 Bu komut yalnızca son derlemeden bu yana değiştirilen projeleri oluşturur. Bir Çözümdeki tüm projeleri oluşturmak için [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)kullanın.

## <a name="example"></a>Örnek
 Bu örnek, `CSharpConsoleApp` ' `Debug` nin çözüm yapılandırmasındaki proje derleme yapılandırması ' nı kullanarak projeyi oluşturur `Debug` `MySolution` .

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'Da projeler ve çözümler oluşturma ve Temizleme](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
