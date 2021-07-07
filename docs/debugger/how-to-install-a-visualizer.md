---
title: Görselleştirici yüklemesi | Microsoft Docs
description: Visual Studio ' de hata ayıklama kullanımı için kullanılabilir olacak şekilde bir Görselleştirici yüklemeyi anlayın.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 611347acfe48e561653d644097d56d029b6a4fa6
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298263"
---
# <a name="how-to-install-a-visualizer"></a>Nasıl Yapılır: Görselleştiriciyi Yükleme
Görselleştirici oluşturduktan sonra, ' de kullanılabilir olacak şekilde Görselleştirici 'yı yüklemelisiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Görselleştirici yüklenmesi basit bir işlemdir.

> [!NOTE]
> UWP uygulamalarında yalnızca standart metin, HTML, XML ve JSON Görselleştiriciler desteklenir. Özel (Kullanıcı tarafından oluşturulan) Görselleştiriciler desteklenmez.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Visual Studio 2019 için bir görselleştirici yüklemek için

1. Oluşturduğunuz Görselleştiriciyi içeren DLL dosyasını bulun.

   Genellikle, hem hata ayıklayıcı tarafında DLL hem de hata ayıklanan tarafı DLL 'SI hedef platform olarak **herhangi BIR CPU** belirtse en iyisidir. Hata ayıklayıcı-yan DLL, **herhangi BIR CPU** veya **32 bit** olmalıdır. Hata ayıklanan tarafı DLL için hedef platform, hata ayıklanan işleme karşılık gelmelidir.

   >[!NOTE]
   > hata ayıklayıcı tarafı görselleştiricisi Visual Studio işleme yüklenir, bu nedenle bir .NET Framework DLL olmalıdır. hata ayıklanan tarafı, Visual Studio hata ayıklamanın ne olduğuna bağlı olarak .NET Framework ya da .NET Standard olabilir.

2. [Hata ayıklayıcı yan](create-custom-visualizers-of-data.md#to-create-the-debugger-side) dll 'sini (ve bağımlı olduğu dll 'leri) aşağıdaki konumlardan birine kopyalayın:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioVersion*`\Visualizers`

3. [Hata ayıklanan yan](create-custom-visualizers-of-data.md#to-create-the-visualizer-object-source-for-the-debuggee-side) dll 'yi aşağıdaki konumlardan birine kopyalayın:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\`*VisualStudioVersion* `\Visualizers\` *Framework*

    Burada *Framework* şunlardan biri:
    - `net2.0` çalışma zamanını çalıştıran debuggees için `.NET Framework` .
    - `netstandard2.0``netstandard 2.0`(veya) desteği olan bir çalışma zamanı kullanan debuggees için `.NET Framework v4.6.1+` `.NET Core 2.0+` .
    - `netcoreapp` çalışma zamanını çalıştıran debuggees için `.NET Core` . (destekler `.NET Core 2.0+` )

   Bağımsız bir Görselleştirici oluşturmak istiyorsanız debugayıklanan taraf DLL gereklidir. Bu DLL, yöntemlerini uygulayabilen veri nesnesi için kod içerir <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .

   Hata ayıklanan tarafı kodu çok hedefliyorsanız, hata ayıklanan tarafı DLL 'nin en düşük desteklenen TFı klasörüne yerleştirilmesi gerekir.

4. Hata ayıklama oturumunu yeniden başlatın.

> [!NOTE]
> yordam Visual Studio 2017 ve üzeri sürümlerde farklıdır. Bu makalenin [önceki sürümüne](how-to-install-a-visualizer.md?view=vs-2017&preserve-view=true) bakın.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Visual Studio 2017 ve üzeri için bir görselleştirici yüklemek için

> [!IMPORTANT]
> yalnızca .NET Framework görselleştiriciler Visual Studio 2017 ve daha eski sürümlerde desteklenir.

1. Derleyecek Görselleştiriciyi içeren DLL 'i bulun.

2. DLL 'yi aşağıdaki konumlardan birine kopyalayın:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioVersion*`\Visualizers`

3. Hata ayıklama oturumunu yeniden başlatın.

> [!NOTE]
> Uzaktan hata ayıklama için yönetilen bir Görselleştirici kullanmak istiyorsanız, uzak bilgisayardaki aynı yola DLL 'yi kopyalayın.
::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
- [Nasıl Yapılır: Görselleştirici Yazma](create-custom-visualizers-of-data.md)
