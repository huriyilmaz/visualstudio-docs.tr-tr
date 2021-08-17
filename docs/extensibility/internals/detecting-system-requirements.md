---
title: Sistem gereksinimleri algılanıyor | Microsoft Docs
description: yüklü olan Visual Studio sürümü gibi sistem gereksinimlerini algılamak için Microsoft Windows Installer yapılandırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 09c83eabb15c1ba4573bc35925529f46d4fb9ad6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069971"
---
# <a name="detect-system-requirements"></a>Sistem gereksinimlerini Algıla
Visual Studio yüklü olmadığı takdirde vspackage işlevi çalışamaz. vspackage yüklemesini yönetmek için Microsoft Windows Installer kullandığınızda yükleyiciyi, Visual Studio yüklenip yüklenmediğini algılamak için yapılandırabilirsiniz. ayrıca, belirli bir Windows sürümü veya belirli bir RAM miktarı gibi, sistemi diğer gereksinimlere göre denetlemek için de yapılandırabilirsiniz.

## <a name="detect-visual-studio-editions"></a>Visual Studio sürümlerini algıla
 bir Visual Studio sürümünün yüklenip yüklenmediğini öğrenmek için, **yükleme** kayıt defteri REG_DWORD anahtarı değerinin, aşağıdaki tabloda listelendiği gibi uygun klasörde *1* olduğunu doğrulayın. Visual Studio sürümlerinin bir hiyerarşisi olduğunu unutmayın:

1. Kurumsal

2. Professional

3. Topluluk

Daha yeni bir sürüm yüklendiğinde, bu sürüm için kayıt defteri anahtarlarının yanı sıra önceki sürümleri için de eklenir. yani, Enterprise sürümü yüklüyse, **yükleme** anahtarı Enterprise için *1* , ayrıca Professional ve Community sürümleri için olarak ayarlanır. Bu nedenle, yalnızca ihtiyacınız olan en son sürümü denetlemeniz gerekir.

> [!NOTE]
> Kayıt defteri düzenleyicisinin 64 bitlik sürümünde, 32-bit anahtarlar **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\** altında görüntülenir. Visual Studio anahtarlar **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\** altındadır.

|Ürün|Anahtar|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Visual Studio 2015 kabuğu (tümleşik ve yalıtılmış)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Visual Studio çalışırken algıla
 vspackage yüklenirken Visual Studio çalışıyorsa vspackage doğru şekilde kaydedilemez. yükleyicinin Visual Studio çalıştığını algılaması ve sonra programı yüklemeyi reddetmelidir. Windows Yükleyici, bu tür algılamayı etkinleştirmek için tablo girişlerini kullanmanıza izin vermez. Bunun yerine, aşağıdaki gibi bir özel eylem oluşturmanız gerekir: `EnumProcesses` *devenv.exe* işlemini algılamak için işlevini kullanın ve ardından bir başlatma koşulunda kullanılan bir yükleyici özelliği ayarlayın veya kullanıcıdan Visual Studio kapatmasını isteyen bir iletişim kutusunu koşullu olarak görüntüleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer ile vspackages 'i yükler](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
