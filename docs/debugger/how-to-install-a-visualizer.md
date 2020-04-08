---
title: 'Nasıl Yapılsın: Görselleştirici Yükleme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 499d644cc8374b070cedaf058b0e4dc17d155bdc
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880266"
---
# <a name="how-to-install-a-visualizer"></a>Nasıl Yapılır: Görselleştiriciyi Yükleme
Bir görselleştirici oluşturduktan sonra, görselleştiriciyi 'de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]kullanılabilir hale getirecek şekilde yüklemeniz gerekir. Görselleştirici yüklemek basit bir işlemdir.

> [!NOTE]
> UWP uygulamalarında yalnızca standart metin, HTML, XML ve JSON görselleştiricileri desteklenir. Özel (kullanıcı tarafından oluşturulan) görüntüleyiciler desteklenmez.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Visual Studio 2019 için görselleştirici yüklemek için
  
1. Oluşturduğun görselleştiriciyi içeren DLL'yi bulun.

   Genellikle, hem hata ayıklama tarafı DLL hem de hata ayıklama tarafı DLL hedef platform olarak **Herhangi bir CPU** belirtin en iyisidir. Hata ayıklayıcı tarafı DLL **herhangi bir CPU** veya **32-bit**olmalıdır. Hata ayıklama tarafı DLL için hedef platformu debugee işlemi karşılık gelmelidir.

2. [Debugger Side](create-custom-visualizers-of-data.md#to-create-the-debugger-side) DLL'yi (ve bağlı olduğu herhangi bir DL'yi) aşağıdaki konumlardan herhangi biri için kopyalayın:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioSürüm*`\Visualizers`
    
3. Hata [Ayıklama Yan](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) DLL'sini aşağıdaki konumlardan herhangi biri için kopyalayın:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Çerçevesi*

    - `My Documents\`*VisualStudioSürüm* `\Visualizers\` *Çerçevesi*

    *Çerçeve* ya nerede:
    - `net2.0``.NET Framework` çalışma saatini çalıştıran hata ayıklamalar için.
    - `netstandard2.0`destekleyen `netstandard 2.0` bir çalışma zamanı kullanarak hata`.NET Framework v4.6.1+` ayıklamalar için ( veya `.NET Core 2.0+`).
    - `netcoreapp``.NET Core` çalışma saatini çalıştıran hata ayıklamalar için. (destekler `.NET Core 2.0+`)

4. Hata ayıklama oturumunu yeniden başlatın.

> [!NOTE]
> Visual Studio 2017 ve daha büyük bir yöntem farklı. Bu makalenin [önceki sürümüne](how-to-install-a-visualizer.md?view=vs-2017) bakın.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Visual Studio 2017 ve üzeri için görselleştirici yüklemek için

> [!IMPORTANT]
> Visual Studio 2017 ve daha büyük lerinde yalnızca .NET Framework görselleştiricileri desteklenir.

1. Oluşturduğun görselleştiriciyi içeren DLL'yi bulun.

2. DLL'yi aşağıdaki konumlardan herhangi biri için kopyalayın:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioSürüm*`\Visualizers`

3. Hata ayıklama oturumunu yeniden başlatın.

> [!NOTE]
> Uzaktan hata ayıklama için yönetilen bir görselleştirici kullanmak istiyorsanız, DLL'yi uzak bilgisayarda aynı yola kopyalayın.
::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
- [Nasıl Yapılır: Görselleştirici Yazma](create-custom-visualizers-of-data.md)
