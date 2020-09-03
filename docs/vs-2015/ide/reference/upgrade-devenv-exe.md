---
title: -Yükselt (devenv.exe) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657907"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Çözüm dosyasını ve tüm proje dosyalarını veya belirtilen proje dosyasını, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Bu dosyaların geçerli biçimlerine güncelleştirir.

## <a name="syntax"></a>Söz dizimi

```
devenv SolutionFile | ProjectFile /upgrade
```

## <a name="arguments"></a>Bağımsız değişkenler
 `SolutionFile` Bir çözümün tamamını ve projelerini yükseltiyorsanız gereklidir. Çözüm dosyasının yolu ve adı. Yalnızca çözüm dosyasının adını veya çözüm dosyasının tam yolunu ve adını girebilirsiniz. Adlı klasör veya dosya henüz yoksa, oluşturulur.

 `ProjectFile` Tek bir projeyi yükseltiyorsanız gereklidir. Çözüm içindeki bir proje dosyasının yolu ve adı. Yalnızca proje dosyasının adını veya proje dosyasının tam yolunu ve adını girebilirsiniz. Adlı klasör veya dosya henüz yoksa, oluşturulur.

## <a name="remarks"></a>Açıklamalar
 Yedeklemeler otomatik olarak oluşturulur ve geçerli dizinde oluşturulan yedekleme adlı bir dizine kopyalanır.

 Kaynak denetimli çözümlerin veya projelerin yükseltibilmeleri için önce kullanıma alınması gerekir.

 Anahtar kullanılması `/upgrade` başlamaz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Yükseltmenin sonuçları, çözüm veya projenin geliştirme dili için yükseltme raporunda görülebilir. Hata veya kullanım bilgisi döndürülmedi. ' De projeleri yükseltme hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bkz. [nasıl yapılır: başarısız Visual Studio proje yükseltmelerinde sorun giderme](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).

## <a name="example"></a>Örnek
 Bu örnek, çözümler için varsayılan klasörünüzdeki "MyProject. sln" adlı bir çözüm dosyasını yükseltir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

```
devenv "MyProject.sln" /upgrade
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: başarısız Visual Studio proje yükseltmeleri](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md) [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) sorunlarını giderme
