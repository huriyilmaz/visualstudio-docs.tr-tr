---
title: -Upgrade (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 24bb6160f9895f129c4d7d36c2b0aa8a56ca282a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657907"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Çözüm dosyasını ve tüm proje dosyalarını veya belirtilen proje dosyasını, bu dosyalar için geçerli [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] biçimlerine güncelleştirir.

## <a name="syntax"></a>Sözdizimi

```
devenv SolutionFile | ProjectFile /upgrade
```

## <a name="arguments"></a>Arguments
 tüm çözümü ve projelerini yükseltiyorsanız `SolutionFile` gerekir. Çözüm dosyasının yolu ve adı. Yalnızca çözüm dosyasının adını veya çözüm dosyasının tam yolunu ve adını girebilirsiniz. Adlı klasör veya dosya henüz yoksa, oluşturulur.

 tek bir projeyi yükseltiyorsanız gerekli `ProjectFile`. Çözüm içindeki bir proje dosyasının yolu ve adı. Yalnızca proje dosyasının adını veya proje dosyasının tam yolunu ve adını girebilirsiniz. Adlı klasör veya dosya henüz yoksa, oluşturulur.

## <a name="remarks"></a>Açıklamalar
 Yedeklemeler otomatik olarak oluşturulur ve geçerli dizinde oluşturulan yedekleme adlı bir dizine kopyalanır.

 Kaynak denetimli çözümlerin veya projelerin yükseltibilmeleri için önce kullanıma alınması gerekir.

 @No__t_0 anahtarının kullanılması [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] başlamaz. Yükseltmenin sonuçları, çözüm veya projenin geliştirme dili için yükseltme raporunda görülebilir. Hata veya kullanım bilgisi döndürülmedi. Projeleri [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yükseltme hakkında daha fazla bilgi için bkz. [nasıl yapılır: başarısız Visual Studio proje yükseltmelerinde sorun giderme](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).

## <a name="example"></a>Örnek
 Bu örnek, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] çözümleri için varsayılan klasörünüzdeki "MyProject. sln" adlı bir çözüm dosyasını yükseltir.

```
devenv "MyProject.sln" /upgrade
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: başarısız Visual Studio proje yükseltmeleri](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md) [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) sorunlarını giderme
