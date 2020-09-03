---
title: Katman modeli uzantısı dağıtma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c11c952223854ff1b4b963e24615e7abe831496
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669872"
---
# <a name="deploy-a-layer-model-extension"></a>Katman modeli uzantısı dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'nun diğer kullanıcıları, Visual Studio kullanarak oluşturduğunuz katman modelleme uzantılarını yükleyebilir.

## <a name="installing-your-extension"></a>Uzantınızı yükleme
 Uzantınız, diğer bilgisayarlara yükleyebileceğiniz bir VSıX dosyasına derlenir. Uzantıyı, Visual Studio 'nun ana örneğinde kullanılabilir hale getirmek için geliştirme bilgisayarınıza da yükleyebilirsiniz.

#### <a name="to-install-the-extension"></a>Uzantıyı yüklemek için

1. **Kaynak. vsix. manifest**dosyasını içeren projede, dosya Gezgini 'nde **açık \\ \\ bin*** öğesini açın.

2. ** \* . Vsix** dosyasını uzantıyı yüklemek istediğiniz bilgisayara kopyalayın.

3. Hedef bilgisayarda, Windows Gezgini 'nde *. vsix dosyasına çift tıklayın.

    VSıX yükleyicisi açılır.

#### <a name="to-uninstall-the-extension"></a>Uzantıyı kaldırmak için

1. Visual Studio 'da, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' e tıklayın.

2. Uzantının adına tıklayın ve ardından **Kaldır**' a tıklayın.

## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Team Foundation yapı sunucusuna Uzantı yükleme
 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] sunucularda normalde Visual Studio yüklü değildir ve bu nedenle VSıX 'i çift tıklayarak yükleyemezsiniz. Yüklemesi, [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] BIR VSIX uzantısının çalışmasına izin veren bazı bileşenleri içerir, ancak uzantıyı el ile yüklemeniz gerekir.

#### <a name="to-install-your-layer-extension-on-a-esprbuild-server"></a>Katman uzantınızı bir sunucusuna yüklemek için [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]

1. **. Vsix** dosyalarını geliştirme bilgisayarınızdan [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] bilgisayara kopyalayın.

     VSıX dosyasını aşağıdaki konumlardan birine yerleştirin:

    - Tüm kullanıcılar ve hizmetler için yüklemek için:

         %ProgramFiles%\Microsoft Visual Studio [sürüm] \Common7\IDE\Extensions\Microsoft

    - Yalnızca çalıştıran ağ hizmetine yüklemek için [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] :

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio \\ [sürüm] \Extensions\Microsoft

    - [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]Belirli bir kullanıcı olarak etkileşimli modda çalışacak şekilde yapılandırdıysanız, yalnızca bu kullanıcı için yükleyebilirsiniz:

         %LocalAppData%\Microsoft\VisualStudio \\ [sürüm] \Extensions\Microsoft

        > [!NOTE]
        > % LocalAppData%, genellikle *DriveName*: Users*Kullanıcı adı*appdatalocal.

2. Her VSıX dosyasını aynı konumdaki bir klasöre genişletin:

    1. Dosya adı uzantısını **. vsix** iken **. zip**olarak değiştirin.

    2. . Zip dosyasının içeriğini bir klasöre ayıklayın.

    3. . Zip dosyasını silme

3. Yeniden başlatın [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] .
