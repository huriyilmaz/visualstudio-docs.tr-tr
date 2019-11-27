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
ms.openlocfilehash: 1df72c6978f5ab34a86c74dbc1ea349db5aa4457
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491311"
---
# <a name="how-to-install-a-visualizer"></a>Nasıl Yapılır: Görselleştiriciyi Yükleme
Görselleştirici oluşturduktan sonra, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' de kullanılabilmesi için Görselleştiriciyi yüklemelisiniz. Görselleştirici yüklenmesi basit bir işlemdir.

> [!NOTE]
> UWP uygulamalarında yalnızca standart metin, HTML, XML ve JSON Görselleştiriciler desteklenir. Özel (Kullanıcı tarafından oluşturulan) Görselleştiriciler desteklenmez.

### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Visual Studio 2019 için bir Görselleştirici yüklemek için
  
1. Derleyecek Görselleştiriciyi içeren DLL 'i bulun.

2. [Hata ayıklayıcı tarafı](create-custom-visualizers-of-data.md#to-create-the-debugger-side) dll 'sini aşağıdaki konumlardan birine kopyalayın:

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

### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Visual Studio 2017 ve daha eski bir Görselleştirici yüklemek için

> [!IMPORTANT]
> Visual Studio 2017 ve üzeri sürümlerde yalnızca .NET Framework Görselleştiriciler desteklenir

1. Derleyecek Görselleştiriciyi içeren DLL 'i bulun.

2. DLL 'yi aşağıdaki konumlardan birine kopyalayın:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Hata ayıklama oturumunu yeniden başlatın.

> [!NOTE]
> Uzaktan hata ayıklama için yönetilen bir Görselleştirici kullanmak istiyorsanız, uzak bilgisayardaki aynı yola DLL 'yi kopyalayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)
- [Nasıl Yapılır: Görselleştirici Yazma](create-custom-visualizers-of-data.md)
