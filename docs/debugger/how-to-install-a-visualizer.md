---
title: 'Nasıl yapılır: Görselleştirici yüklemesi | Microsoft Docs'
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
ms.openlocfilehash: 2b7dfd28d70b80fd2d0f854b7db3550862b32814
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404367"
---
# <a name="how-to-install-a-visualizer"></a>Nasıl Yapılır: Görselleştiriciyi Yükleme
Görselleştirici oluşturduktan sonra, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' de kullanılabilmesi için Görselleştiriciyi yüklemelisiniz. Görselleştirici yüklenmesi basit bir işlemdir.

> [!NOTE]
> UWP uygulamalarında yalnızca standart metin, HTML, XML ve JSON Görselleştiriciler desteklenir. Özel (Kullanıcı tarafından oluşturulan) Görselleştiriciler desteklenmez.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Visual Studio 2019 için bir Görselleştirici yüklemek için
  
1. Oluşturduğunuz Görselleştiriciyi içeren DLL dosyasını bulun.

2. [Hata ayıklayıcı yan](create-custom-visualizers-of-data.md#to-create-the-debugger-side) dll 'sini (ve bağımlı olduğu dll 'leri) aşağıdaki konumlardan birine kopyalayın:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. [Hata ayıklanan yan](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) dll 'yi aşağıdaki konumlardan birine kopyalayın:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\` *Framework*

    Burada *Framework* şunlardan biri:
    - `.NET Framework` çalışma zamanını çalıştıran debuggees için `net2.0`.
    - `netstandard 2.0` (`.NET Framework v4.6.1+` ya da `.NET Core 2.0+`) destekleyen bir çalışma zamanı kullanarak debuggees için `netstandard2.0`.
    - `.NET Core` çalışma zamanını çalıştıran debuggees için `netcoreapp`. (`.NET Core 2.0+`destekler)

4. Hata ayıklama oturumunu yeniden başlatın.

> [!NOTE]
> Yordam, Visual Studio 2017 ve üzeri sürümlerde farklıdır. Bu makalenin [önceki sürümüne](how-to-install-a-visualizer.md?view=vs-2017) bakın.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Visual Studio 2017 ve daha eski bir Görselleştirici yüklemek için

> [!IMPORTANT]
> Yalnızca .NET Framework Görselleştiriciler Visual Studio 2017 ve üzeri sürümlerde desteklenir.

1. Derleyecek Görselleştiriciyi içeren DLL 'i bulun.

2. DLL 'yi aşağıdaki konumlardan birine kopyalayın:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Hata ayıklama oturumunu yeniden başlatın.

> [!NOTE]
> Uzaktan hata ayıklama için yönetilen bir Görselleştirici kullanmak istiyorsanız, uzak bilgisayardaki aynı yola DLL 'yi kopyalayın.
::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
- [Nasıl Yapılır: Görselleştirici Yazma](create-custom-visualizers-of-data.md)
