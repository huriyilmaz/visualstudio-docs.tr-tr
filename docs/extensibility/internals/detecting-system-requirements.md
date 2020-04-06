---
title: Sistem Gereksinimlerini algılama | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708731"
---
# <a name="detect-system-requirements"></a>Sistem gereksinimlerini algılama
Visual Studio yüklü olmadığı sürece VSPackage çalışmaz. VSPackage'ınızın yüklenmesini yönetmek için Microsoft Windows Installer'ı kullandığınızda, Visual Studio'nun yüklü olup olmadığını algılamak için yükleyiciyi yapılandırabilirsiniz. Ayrıca, sistemi diğer gereksinimler için (örneğin, Windows'un belirli bir sürümü veya belirli bir RAM miktarı) denetlemek üzere yapılandırabilirsiniz.

## <a name="detect-visual-studio-editions"></a>Visual Studio sürümlerini algıla
 Visual Studio'nun bir sürümünün yüklü olup olmadığını belirlemek için, **yükleme** kayıt defteri anahtarının değerinin aşağıdaki tabloda listelenen ilgili klasörde *(REG_DWORD) 1* olduğunu doğrulayın. Visual Studio sürümlerinin bir hiyerarşisi olduğunu unutmayın:

1. Enterprise

2. Professional

3. Topluluk

Daha yeni bir sürüm yüklendiğinde, önceki sürümlerin yanı sıra bu sürümün kayıt defteri anahtarları da eklenir. Diğer bir nokta, Enterprise sürümü yüklenirse, **Yükle** tuşu Enterprise için *1'in* yanı sıra Profesyonel ve Topluluk sürümleri için ayarlanır. Bu nedenle, yalnızca ihtiyacınız olan en son sürümü denetlemeniz gerekir.

> [!NOTE]
> Kayıt defteri düzenleyicisinin 64 bit sürümünde, 32 bit tuşları **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**altında görüntülenir. Visual Studio tuşları **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servis\\**altındadır.

|Ürün|Anahtar|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servis\14.0\kurumsal|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servis\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servis\14.0\topluluk|
|Visual Studio 2015 Shell (entegre ve izole)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servis\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Visual Studio çalışırken algıla
 VSPackage yüklendiğinde Visual Studio çalışıyorsa VSPackage'ınız doğru şekilde kaydedilemez. Yükleyici Visual Studio'nun ne zaman çalıştığını algılamalı ve programı yüklemeyi reddetmelidir. Windows Installer, bu tür bir algılamayı etkinleştirmek için tablo girişlerini kullanmanıza izin vermez. Bunun yerine, aşağıdaki gibi özel bir eylem `EnumProcesses` oluşturmanız gerekir: *devenv.exe* işlemini algılamak için işlevi kullanın ve ardından başlatma durumunda kullanılan bir yükleyici özelliğini ayarlayın veya kullanıcıdan Visual Studio'yu kapatmasını gerektiren bir iletişim kutusunu koşullu olarak görüntüleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer ile VSPackages yükleyin](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
