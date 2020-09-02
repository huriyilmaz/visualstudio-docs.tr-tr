---
title: Sistem gereksinimleri algılanıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 51
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 467554b8e50878bcdf1029e4792bbf168a09fa11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788476"
---
# <a name="detecting-system-requirements"></a>Sistem Gereksinimlerini Algılama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio yüklü değilse VSPackage işlevi çalışamaz. VSPackage yüklemesini yönetmek için Microsoft Windows Installer kullandığınızda, yükleyiciyi, Visual Studio 'nun yüklü olup olmadığını algılamak için yapılandırabilirsiniz. Ayrıca, sistemi diğer gereksinimlere göre (örneğin, belirli bir Windows sürümü veya belirli bir RAM miktarı) denetlemek üzere de yapılandırabilirsiniz.  
  
## <a name="detecting-visual-studio-editions"></a>Visual Studio sürümleri algılanıyor  
 Visual Studio 'nun bir sürümünün yüklü olup olmadığını anlamak için, aşağıdaki tabloda listelendiği gibi yükleme kayıt defteri anahtarının değerini uygun klasörde (REG_DWORD) 1 olduğunu doğrulayın. Visual Studio sürümlerinin bir hiyerarşisi olduğunu unutmayın:  
  
1. Enterprise  
  
2. Professional  
  
3. Topluluk  
  
   "Daha yüksek" bir sürüm yüklendiğinde, bu sürüm için kayıt defteri anahtarlarının yanı sıra "daha düşük" sürümler de eklenir. Diğer bir deyişle, Enterprise Edition yüklüyse, kuruluş için yükleme anahtarı 1, profesyonel ve topluluk sürümleri için de 1 olarak ayarlanır. Bu nedenle, yalnızca ihtiyacınız olan "en yüksek" sürümü için onay almanız gerekir.  
  
> [!NOTE]
> Kayıt defteri düzenleyicisinin 64 bitlik sürümünde, 32-bit anahtarlar HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node altında görüntülenir \\ . Visual Studio anahtarları HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing altındadır \\ .  
  
|Ürün|Anahtar|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 kabuğu (tümleşik ve yalıtılmış)|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Visual Studio 'nun ne zaman çalıştığını algılama  
 VSPackage yüklendiğinde, Visual Studio çalışıyorsa VSPackage doğru şekilde kaydedilemez. Yükleyici, Visual Studio 'Nun ne zaman çalıştığını algılamalıdır ve sonra programı yüklemeyi reddeder. Windows Installer, bu tür algılamayı etkinleştirmek için tablo girişlerini kullanmanıza izin vermez. Bunun yerine, aşağıdaki gibi bir özel eylem oluşturmanız gerekir: `EnumProcesses` devenv.exe işlemini algılamak için Işlevini kullanın ve ardından bir başlatma koşulunda kullanılan bir yükleyici özelliği ayarlayın veya kullanıcıdan Visual Studio 'yu kapatmasını isteyen bir iletişim kutusunu koşullu olarak görüntüleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Installer ile VSPackage Yükleme](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
