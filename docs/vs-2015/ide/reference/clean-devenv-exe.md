---
title: -Temizle (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- clean Devenv switch
- /clean Devenv switch
- Devenv, /clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 043e9373f242523b7925a9ae775be6789f7cfc20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660879"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tüm ara dosyaları ve çıkış dizinlerini temizler.

## <a name="syntax"></a>Söz dizimi

```
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `FileName` Gerekli. Çözüm dosyasının veya proje dosyasının tam yolu ve adı.

 /Project `ProjName` isteğe bağlı. Çözüm içindeki bir proje dosyasının yolu ve adı. `SolutionName`Klasörden proje dosyasına ya da projenin görünen adına veya proje dosyasının tam yolunu ve adına göreli bir yol girebilirsiniz.

 /ProjectConfig `ProjConfigName` isteğe bağlıdır. Adlandırılmış bir temizlik sırasında kullanılacak bir proje derleme yapılandırması adı `/project` .

## <a name="remarks"></a>Açıklamalar
 Bu anahtar, tümleşik geliştirme ortamı (IDE) içindeki **Çözümü Temizle** menü komutuyla aynı işlevi gerçekleştirir.

 Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

 Temizlerle ilgili özet bilgiler, hatalar da dahil olmak üzere **komut** penceresinde veya anahtarla belirtilen herhangi bir günlük dosyasında görüntülenebilir `/out` .

## <a name="example"></a>Örnek
 İlk örnek çözüm `MySolution` dosyasında belirtilen varsayılan yapılandırmayı kullanarak çözümü temizler.

 İkinci örnek, `CSharpConsoleApp` `Debug` öğesinin çözüm yapılandırması içindeki proje derleme yapılandırması kullanılarak projeyi temizler `Debug` `MySolution` .

```
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean

devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) [/build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
