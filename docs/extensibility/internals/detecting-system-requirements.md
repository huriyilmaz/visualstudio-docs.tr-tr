---
title: Sistem gereksinimleri algılanıyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ab254df5d53f379704128d8860b8d7fe5655bae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708731"
---
# <a name="detect-system-requirements"></a>Sistem gereksinimlerini Algıla
Visual Studio yüklü değilse VSPackage işlevi çalışamaz. VSPackage yüklemesini yönetmek için Microsoft Windows Installer kullandığınızda, yükleyiciyi, Visual Studio 'nun yüklü olup olmadığını algılamak için yapılandırabilirsiniz. Ayrıca, sistemi diğer gereksinimlere göre (örneğin, belirli bir Windows sürümü veya belirli bir RAM miktarı) denetlemek üzere de yapılandırabilirsiniz.

## <a name="detect-visual-studio-editions"></a>Visual Studio sürümlerini Algıla
 Visual Studio 'nun bir sürümünün yüklü olup olmadığını anlamak için, aşağıdaki tabloda listelendiği gibi **yükleme** kayıt defteri anahtarının değerini uygun klasörde *(REG_DWORD) 1* olduğunu doğrulayın. Visual Studio sürümlerinin bir hiyerarşisi olduğunu unutmayın:

1. Enterprise

2. Professional

3. Topluluk

Daha yeni bir sürüm yüklendiğinde, bu sürüm için kayıt defteri anahtarlarının yanı sıra önceki sürümleri için de eklenir. Diğer bir deyişle, Enterprise sürümü yüklüyse, kuruluş için ve profesyonel ve topluluk sürümleri için **yükleme** anahtarı *1* olarak ayarlanır. Bu nedenle, yalnızca ihtiyacınız olan en son sürümü denetlemeniz gerekir.

> [!NOTE]
> Kayıt defteri düzenleyicisinin 64 bitlik sürümünde, 32-bit anahtarlar **HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node \\ **altında görüntülenir. Visual Studio anahtarları **HKEY_LOCAL_MACHINE \software\wow6432node\microsoft\devdiv\vs\servicing \\ **altındadır.

|Ürün|Anahtar|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Visual Studio 2015 kabuğu (tümleşik ve yalıtılmış)|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Visual Studio 'nun ne zaman çalıştığını Algıla
 VSPackage yüklendiğinde, Visual Studio çalışıyorsa VSPackage doğru şekilde kaydedilemez. Yükleyici, Visual Studio 'Nun ne zaman çalıştığını algılamalıdır ve sonra programı yüklemeyi reddeder. Windows Installer, bu tür algılamayı etkinleştirmek için tablo girişlerini kullanmanıza izin vermez. Bunun yerine, aşağıdaki gibi bir özel eylem oluşturmanız gerekir: `EnumProcesses` *devenv.exe* işlemini algılamak için işlevini kullanın ve ardından bir başlatma koşulunda kullanılan bir yükleyici özelliği ayarlayın veya kullanıcıdan Visual Studio 'yu kapatmasını isteyen bir iletişim kutusunu koşullu olarak görüntüleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer Ile VSPackages 'ı yükler](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
